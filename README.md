# Moving average filter for angles 0-360°
[![Build Status](https://travis-ci.org/pilotak/MovingAverageAngle.svg?branch=master)](https://travis-ci.org/pilotak/MovingAverageAngle)

This library requires [MovingAverage](https://github.com/pilotak/MovingAverage) library.

## Mbed example
```cpp
#include "mbed.h"
#include "MovingAverageAngle.h"  // https://github.com/pilotak/MovingAverageAngle

// Buffer will be 4 samples long, it will take 4 * sizeof(float) = 16 bytes of RAM
MovingAverageAngle <4> filter;

int main() {
    printf("result: %.2f\n", filter.add(350)); // insert new number and get result
    printf("result: %.2f\n", filter.add(20)); // insert new number and get result
    printf("result: %.2f\n", filter.add(30)); // insert new number and get result
    printf("result: %.2f\n", filter.add(40)); // insert new number and get result
    printf("result: %.2f\n", filter.get()); // get last result, without adding a newone

    return 0;
}
```
## Arduino example
```cpp
#include "MovingAverageAngle.h"  // https://github.com/pilotak/MovingAverageAngle

// Buffer will be 4 samples long, it will take 4 * sizeof(float) = 16 bytes of RAM
MovingAverageAngle <4> filter;

void setup(){
    Serial.begin(9600);
    Serial.print("result: ");
    Serial.println(filter.add(350), 2); // insert new number and get result
    Serial.print("result: ");
    Serial.println(filter.add(20), 2); // insert new number and get result
    Serial.print("result: ");
    Serial.println(filter.add(30), 2); // insert new number and get result
    Serial.print("result: ");
    Serial.println(filter.add(40), 2); // insert new number and get result
    Serial.print("result: ");
    Serial.println(filter.get(), 2); // get last result, without adding a newone
}

void loop(){

}
```

### Output
> result: 350.00
> 
> result: 357.37
> 
> result: 7.47
> 
> result: 20.24
> 
> result: 20.24
