# FM Radio Receiver

A battery-powered FM stereo receiver kit that I assembled, tested, and investigated to understand how a modern radio works.

**Status:** Completed

**Project type:** Educational kit assembly and functional analysis

**Main IC:** RDA5807FP FM receiver

**Skills:** Soldering, PCB assembly, testing, troubleshooting, datasheet research

![Completed FM radio](photos/finished-radio.jpg)

## Project Overview

The radio uses push buttons for power, volume, and automatic station seeking. Audio is played through connected headphones, while the headphone cable also acts as the FM antenna.

Although the PCB contains relatively few components, most of the receiver is integrated inside the RDA5807FP chip.

## Key Outcomes

* Successfully assembled and tested the receiver.
* Received FM stations through headphones.
* Investigated why reception improved outdoors and near a balcony.
* Identified the main receiver IC and studied its internal architecture.
* Learned the roles of the antenna, crystal reference, mixer, converters, and digital signal processor.
* Documented an unresolved question about how the board implements direct button control.

## System Overview

```text
FM broadcast signals
        ↓
Headphone cable acting as antenna
        ↓
RDA5807FP receiver IC
        ↓
Station selection and FM demodulation
        ↓
Left and right audio outputs
        ↓
Headphones
```

The antenna receives several radio stations at the same time. The receiver selects one station, extracts its audio information, and produces left and right audio signals for the headphones.

## Main Components

| Component          | Purpose                                               |
| ------------------ | ----------------------------------------------------- |
| RDA5807FP          | Receives, selects, and processes FM radio signals     |
| 32.768 kHz crystal | Provides a stable reference clock for accurate tuning |
| Headphone cable    | Carries audio and acts as the FM antenna              |
| Push buttons       | Control power, volume, and station seeking            |
| Capacitors         | Filter the power supply and couple signals            |
| Resistors          | Set and control electrical conditions                 |
| Battery holder     | Powers the circuit                                    |
| PCB                | Supports and connects all components                  |

## How the Radio Works

### 1. Receiving the signal

FM broadcasts create electromagnetic waves in the air. These waves produce a very small changing electrical signal in the headphone cable.

The antenna receives many stations simultaneously rather than only the selected station.

### 2. Amplifying and selecting a station

The signal enters the RDA5807FP through its FM input. An internal low-noise amplifier strengthens the weak signal.

A frequency synthesizer and mixer then help select one station and shift it to a lower intermediate frequency that is easier to process.

### 3. Using the crystal reference

The external crystal does not receive the station or oscillate at the broadcast frequency.

Instead, it provides an accurate reference clock. The receiver uses this reference to generate the internal frequencies needed for tuning.

### 4. Processing the signal digitally

The receiver converts the signal into digital values using analog-to-digital converters.

Its internal digital signal processor then performs functions such as:

* Channel selection
* FM demodulation
* Noise reduction
* Stereo decoding
* Volume processing
* Automatic stereo-to-mono switching

### 5. Producing audio

Digital-to-analog converters change the processed audio back into left and right analog signals.

These signals leave the chip through its audio outputs and drive the headphones.

## Build and Testing

I assembled the board by identifying and soldering the resistors, capacitors, crystal, buttons, headphone jack, battery connections, and other supplied components.

After assembly, I inspected the solder joints, connected the batteries and headphones, and tested the controls.

The radio powered on and successfully found FM stations using the seek buttons.

## Reception Troubleshooting

Reception was initially weak indoors and often consisted mainly of noise.

I tested the radio in different locations and changed the position of the headphone cable. Reception improved significantly near the balcony and outdoors.

This showed that the circuit was functioning and that the main limitation was the antenna environment rather than a major assembly fault.

The experiment demonstrated that reception depends on:

* Antenna position and length
* Distance from the transmitter
* Walls and surrounding structures
* Local interference
* Signal strength

## Technical Investigation

The marking on the main IC was identified as approximately `RDA5807FP`.

Reading its datasheet showed that the small chip contains many parts of a complete radio receiver, including:

* A low-noise amplifier
* A frequency synthesizer
* A mixer
* Programmable amplifiers
* Analog-to-digital converters
* A digital signal processor
* A stereo decoder
* Digital-to-analog converters
* An internal voltage regulator

This explained why the external PCB could remain relatively simple.

## Open Question: Button Control

The available RDA5807FP datasheet describes the chip as being controlled through an I²C communication interface.

However, this board uses direct power, volume, and station buttons without an obvious separate microcontroller.

The exact control method used by this particular kit has not yet been confirmed. Possible explanations include a different chip revision, an undocumented operating mode, a compatible derivative, or incomplete public documentation.

I have kept this as an open question rather than presenting an unsupported conclusion.

## What I Learned

This project began as a soldering exercise but became my first serious investigation into what exists inside an integrated circuit.

It introduced me to what I think of as the **“smaller universes” of electronics**:

```text
Completed FM radio
└── Printed circuit board
    ├── Resistors
    ├── Capacitors
    ├── Buttons
    ├── Crystal
    └── Integrated circuit package
        └── Silicon die
            └── Functional circuit blocks
                └── Transistors
                    └── Semiconductor structures
```

A PCB is already a system of components, connections, and signals. Inside one small IC is another system containing many circuit blocks and microscopic transistors fabricated on silicon.

The project helped me understand:

* How a wire can act as an antenna
* Why the antenna receives several stations at once
* How a receiver selects one station
* What FM demodulation means
* Why receivers use frequency conversion
* How a crystal provides an accurate reference
* How modern ICs replace many separate components
* Why datasheets must be compared with the physical hardware
* Why uncertain findings should be documented honestly

## Project Scope

This was an educational kit rather than an original circuit or PCB design.

My work involved:

* Assembly
* Soldering
* Testing
* Troubleshooting
* Functional analysis
* Datasheet research

I did not design the receiver IC, circuit, or PCB.

## Media

* [Completed radio](photos/finished-radio.jpg)
* [PCB front](photos/pcb-front.jpg)
* [PCB back](photos/pcb-back.jpg)
* [Testing setup](photos/testing-setup.jpg)
* [PCB component layout](schematics/pcb-component-layout.jpg)

## References

* *RDA5807FP Single-Chip Broadcast FM Radio Tuner Datasheet*
* Supplied kit assembly information
