# node-red-PLC-station-and-antenna-control

A Windows Node Red flow to implement macro operations for my other Node Red flows.

SCREENSHOTS

Screenshots can be found in the Github Wiki entry for this repository.

INTRODUCTION

This implementation is highly specific to my particular amateur radio station. Nevertheless, it may be useful in part to other efforts, and as an example.

I use the buttons for both control and feedback. The color and text labelling of a button reflect the state of macro operation. This state is implemented by a function node that feeds each button. This is the only flow I have where true, closed loop operations are not used. The button issues a series of commands and it is assumed they are properly implemented. However, the remainder of my collection of flows provides ample closed loop status, so in my case it will be clear if the macro buttons are having their desired effect. For instance, if part of a macro is to assert Thetis TUN, it will be plainly evident in Thetis if it happened or not.

All of the buttons are toggle buttons, this makes the entire UI rather compact and efficient. I know that many people prefer separate buttons and indicators. However the same basic function node-to-button-and-indicator configuration should work just as well in such a case.

Although the buttons are hard-coded at this time, each generating a series of CAT commands, I tried to make the flow relatively generic such that commands are consolidated and then parcelled out to the correct flows via a series of link-out nodes. Using link-out nodes to the other relevant flows prevents having multiple IP connections to the amp, PLC and Thetis.

I've created custom CAT commands for functions unique to my PLC implementation. These start with "xx" and thus will allow easy extensibilty of macro operations with the PLC in the future. Thetis and Elecraft CAT commands are, of course, the normal, native commands for those targets. 

In the future I hope to create a less hard-coded, more programmable method for programming buttons. I would have done that right off, but I ran into a complexity associated with the necessity for delays between certain commands and I haven't sorted how to do that cleanly yet. I'm not a developer and, while I'm enjoying the "low code" Node Red environment, it certainly isn't a "no code" environment!

Developed under node 16.12.0 and npm 8.1.0.
 