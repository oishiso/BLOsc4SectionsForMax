blosc4sections~.mxo
(Band-limited oscillator with 4 sections)

============================

Requirements:
Object “blosc4sections~.mxo” only works in Max 6.1 or higher. It is not compatible with earlier versions of Max.

============================

How to install:
- Start Max and add the folder “BLOsc4SectionsForMax” to your file search path.
(From Menu “Options” > “File Preferences” > “+” button at lower left corner of the window)
- Open “blosc4sections~ demo.maxpat” to play demo

============================

Contents of folder “BLOscForMax”:

blosc_presets.json - Preset file for demo patch

blosc4sections~ demo.maxpat - Demo Max patch

blosc4sections~.mxo - Max object

objects Folder - Includes Xcode project and C source code, which is used to develop the above max object.
Xcode Project:
/BLOscForMax/objects/projects/msp/blosc4sections/blosc4sections~.xcodeproj
C source code:
/BLOscForMax/objects/projects/msp/blosc4sections/blosc4sections~.c 

============================

Instruction for using object:

Activate a section by giving non-zero value to both Lowest or Highest Harmonic Index.
Deactivate a section by giving “0” to either Lowest or Highest Harmonic Index.

Parameter “Spread Value” corresponds to the power value described in the section 5.1 of our paper (“Raising power in the time domain”)
There is also a parameter “Spread Compensation” to determine if frequency shifter is applied to compensate the side effect of raising power. When “Spread Compensation” is On (by giving non-zero value), the frequency of lowest harmonic of a section stays same no matter how we change “Spread Value”. If “Spread Compensation” is Off, the frequency of lowest harmonic of a section is dependent on “Spread Value”.

The object has both real (cosine-sum) output and imaginary (sine-sum) output from two outlets. In the demo patch, you can see the waveform from both outlets by checking “Scope On” box.

Amplitude normalization function is implemented in “blosc4sections~” object, thus output amplitude keeps same regardless of its parametric values. Amplitude normalization is done by fixing the maximum displacement value of real output to 1, and this means the maximum displacement value of imaginary output is less than 1. 


Object “blosc4sections~” has 4 arguments: 
"Fundamental Frequency”
"Lowest Harmonic Index (Section 1)" 
"Highest Harmonic Index (Section 1)"
"Spectral Slope (Section 1)"

Object “blosc4sections~” has 26 input parameters from inlets:
(From left inlet)
"Fundamental Frequency”
"Lowest Harmonic Index (Section 1)" 
"Highest Harmonic Index (Section 1)"
"Spectral Slope (Section 1)"
"Even to Odd Harmonics Amp Ratio (Section 1)"
"Spread Value (Integer Input) (Section 1)"
"Section Amp (Section 1)"
"Lowest Harmonic Index (Section 2)"
"Highest Harmonic Index (Section 2)"
"Spectral Slope (Section 2)"
"Even to Odd Harmonics Amp Ratio (Section 2)"
"Spread Value (Integer Input) (Section 2)"
"Section Amp (Section 2)"
"Lowest Harmonic Index (Section 3)"
"Highest Harmonic Index (Section 3)"
"Spectral Slope (Section 3)"
"Even to Odd Harmonics Amp Ratio (Section 3)"
"Spread Value (Integer Input) (Section 3)"
"Section Amp (Section 3)"
"Lowest Harmonic Index (Section 4)"
"Highest Harmonic Index (Section 4)"
"Spectral Slope (Section 4)"
"Even to Odd Harmonics Amp Ratio (Section 4)"
"Spread Value (Integer Input) (Section 4)"
"Section Amp (Section 4)"
"Spread Compensation (0: Off, Other Value: On)"

============================

About the demo MAX patch:

- Presentation Mode
The patch opens in presentation mode. 
To quit presentation mode, “View” > “Presentation”, or Option+Command+E.
To change the default opening mode, go “View” > “Patcher Inspector” > Uncheck “Open in Presentation”.

- Fix Mode or Modulation Mode
Each parameter can be either “Fix Mode” or “Modulation Mode”.
Depending on parameter, either “Fix & Min Value” or “Fix & Max Value” determines the parametric value when in “Fix Mode”.
Number box “Min Value” and “Max Value” determine the lower and the upper limit of parametric value when in “Modulation Mode”.

- Amplitude Envelope
Amplitude envelope can be on/off.
When in “With Env” mode, it can be repeatedly triggered by checking “repeat play“ box. When “repeat play” is off, one-shot trigger can be done by clicking “play” button.

- Presets
I have programmed the following 10 default presets.

1: "a" vowel f0=150Hz Male
2: "a" vowel f0=150Hz Female
3: "a" vowel f0=200Hz Male
4: "a" vowel f0=200Hz Female
5: "a" vowel f0=300Hz Male
6: "a" vowel f0=300Hz Female
7: "a" vowel f0=400Hz Male
8: "a" vowel f0=400Hz Female
9: Formant modulation (with 2 sections)
10: Modulate Everything (with 4 sections)

Store new presets using message “store 11” to “store 20”, or overwrite existing presets using message “store 1” to “store 10”.
“write” message exports current preset setting as an external .json file.
“read” message imports preset setting from an external .json file.

- Formant Demo
Move the pointer on figure “HillenbrandFig4.png”, it changes "Highest Harmonic Index (Section 1)" and "Lowest Harmonic Index (Section 2)".


============================
License
Copyright (c) 2016 So Oishi. All rights reserved.
This program is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or any later version.


============================
Author
So Oishi<oishiso@gmail.com>