# SerialPorts

[![Build Status](https://travis-ci.org/sjkelly/SerialPorts.jl.svg?branch=master)](https://travis-ci.org/sjkelly/SerialPorts.jl)
[![Coverage Status](https://img.shields.io/coveralls/sjkelly/SerialPorts.jl.svg)](https://coveralls.io/r/sjkelly/SerialPorts.jl?branch=master)

[![SerialPorts](http://pkg.julialang.org/badges/SerialPorts_0.3.svg)](http://pkg.julialang.org/?pkg=SerialPorts)

[![SerialPorts](http://pkg.julialang.org/badges/SerialPorts_0.4.svg)](http://pkg.julialang.org/?pkg=SerialPorts)

SerialPorts.jl lets you work with devices over serial communication with Julia.
It is designed to mimic regular file IO as in the Base Julia library.

This package requires PySerial, which is used through PyCall. Conda is used as
a fallback so cross-platform installation is simple. Overtime, one of
the long term objectives should be to rewrite this in Julia for better portability,
installation, and performance.

## Documentation

A `SerialPort` can be treated like any other IO stream in Julia.

A brief example:

```
using SerialPorts
s = SerialPort("/dev/ttyACM1", 250000)
write(s, "G1 X1000 F10000\n")
# if this is connected to a 3D printer it's not my fault if it breaks.
close(s)
```

`open`, `close`, `read`, `write`, `nb_available`, `readavailable`, are all
directly defined for `SerialPort`.

In order to see the attached serial devices, use `list_serialports()`.

The `Arduino` submodule provides functionality for manipulating Arduinos over
serial. `SerialPorts.Arduino.reset(s::SerialPort)` will reset an Arduino.

## License
Available under the [CC0 1.0 Universal Public Domain Dedication](http://en.wikipedia.org/wiki/Creative_Commons_license#Zero_.2F_Public_domain). See: [LICENSE.md](./LICENSE.md).

