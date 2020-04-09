# About

METICULOUS is a main memory emulator running on a SoC FPGA board.
It can emulate various read/write performance characteristics (e.g., read/write
latency, bandwidth and error ratio) of a main memory device.
All the emulation is done in the hardware layer.
No software-based mechanism is necessary.
A SoC FPGA board is equipped with a powerful 64-bits CPU (e.g., ARM64), which can accommodate a full-fledged operating system.
It enables us to study how system software should be designed for emerging memory devices.

Supported emulation:
- Latency
- Bandwidth
- Bit-flip error
- Hybrid memory

For details, please refer to the below paper.
- (In preparation)


# Availability

The binary package of METICULOUS is available at [Download]().
It is released under the below license.
```
Copyright (c) 2020 National Institute of Advanced Industrial Science and Technology (AIST)

Permission is hereby granted, free of charge, to any person obtaining a copy of
this software and associated documentation files (the "Software"), to deal in
the Software without restriction, including without limitation the rights to
use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies
of the Software, and to permit persons to whom the Software is furnished to do
so, subject to the following conditions:

The above copyright notice and this permission notice (including the next
paragraph) shall be included in all copies or substantial portions of the
Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

At this moment, the source code of METICULOUS is available for those who collaborate on research projects with us.
It is also available under an agreement with AIST. Feel free to contact us.


# Usage

## Prerequisite

- Xilinx ZCU104 (Zynq UltraScale+ MPSoC ZCU104 evaluation board) with a 32GB
  PL-side SO-DIMM DRAM module.
- Write an image file to a micro SD card and boot it. The FPGA is automatically
  programmed and Linux starts on the 64-bit ARM CPU.

## API

The performance characteristics of the main memory is configured through the
control registers of the emulator.
A programming library provides an API for ease of use.
Fr example, the first function sets read/write latency, respectively; the upper
16 bits of the second argument is read latency, the lower 64 bits is write
latency.
```
FME_SetLatency(const unsigned int bank, const unsigned int latency_in_100ns);
FME_SetThroughput(const unsigned int bank, const unsigned int throughput_in_100mbps);
FME_SetErrorRate(const unsigned int bank, const unsigned int error_rate_in_percentage);
```

To emulate hybrid main memory, this function sets the boundary of 2 memory regions.
```
FME_SetBoundary(const unsigned int bank, const unsigned int boundary);
```

More information will come up soon.


# Contributors

- Takahiro Hirofuchi (AIST)
- Ryousei Takano (AIST)
- Akram BEN AHMED (AIST)


# Contact

- [Takahiro Hirofuchi (AIST)](https://takahiro-hirofuchi.github.io)


# Copyright

Copyright (c) 2020 National Institute of Advanced Industrial Science and Technology (AIST)
