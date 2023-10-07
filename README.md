# Low-Noise Amplifier for Current Sensing

This is an experimental breakout board for the ultralow noise AD8331
variable-gain amplifier with internal low-noise preamplifier. 
The board is designed to provide electrical isolation
between the output (connects to oscilloscope) and the input port.

- AC-coupled input up to 200 mV
- Adjustable gain amplifier, up to 55 dB
- Galvanically isolated output
- Single 3.3V supply

The input impedance of the amplifier should be around 6k ohms.
The output is matched to 50 ohms over an isolating signal transformer.

![<img src="./docs/pcb.png" width="40" />](docs/pcb.png)
![<img src="./docs/pcb1.png" width="40" />](docs/pcb1.png)

The amplifier module is intended to be used as a current probe with
an additional shunt resistor. The amplifier is placed near the device 
under test. The output signal is digitized by an oscilloscope for analysis.

~~~
   .
   .
   |
 __|__
|     |
| DUT |
|_____|             ______________________________
   |               |                              |
   +------------+  |   Low-noise amplifier        |_____
  | | Shunt     +--|   with up to 55 dB gain      |///  |_  ==> To oscilloscope
  | |           +--|                              |///__|
   +------------+  |                              |  
   |     Short     |______________________________|
   .     wiring
   .
~~~


## Progress

- [x] Schematics design
- [x] PCB layout
- [ ] PCB prototype manufacturing
- [ ] In-circuit verification
- [ ] Proof-of-concept of power analysis side channel attack

## Motivation
The current probe is designed to measure the transient current consumption
of microcontrollers and low-end CPUs in order to create a power consumption
side channel, which can be used to leak information about cryptographic
operations.

Such side-channel attacks have been known to exists for many years, and there
are even [commercial tools](https://chipwhisperer.readthedocs.io/en/latest/getting-started.html)
available which simplify the research process.

My goal with this DIY low-noise current probe is to have a cost-effective 
alternative to other specialized tools, as I already own 
suitable measurements equipment (i.e., an oscilloscope) 
and do not need access to other attack methods (such as fault injection).
