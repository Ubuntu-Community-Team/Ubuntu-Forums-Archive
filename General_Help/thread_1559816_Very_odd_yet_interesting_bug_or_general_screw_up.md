---
title: "Very odd yet interesting bug or general screw up"
date: 2010-08-24
forum: General Help
---

### Post by marcusdufrane on 2010-08-24
Running on a 32 bit lucid install, I'm using a usb to serial device. That aside is working...kinda. Here's the odd and interesting bit. 
The program I wrote uses the usb to serial device to communicate with a relay board and in turn control some meters. The problem now arises as the communication is screwy now. This is a fresh install but the program was running on 8.04 with no problems and now on 10.04 with this interesting glitch, nothing has changed in the program, now for the glitch...

the device is sent 4 bytes the first two control the device and the second two are for the data to be sent. for example setting a write array to turn on the first relay is done like so array = { 0x90, 0x02, 0x01, 0x00}

the device reads and works for all individual relays i.e. 1, 2, 4, 8 but when i go to combine relays such as 5 or 10 to control both relays 1 and 3 or 2 and 4 respectively it doesn't work, 5 works but 10 does not, sending 10 actually activate what sending 13 should, and here's the kicker(or the interesting part) sending 13 actually activates what sending 10 should.

like i said the program hasn't changed so I'm curious if anyone here has any ideas as to what the F*&# is going on here, I'm thinking it's something in the change from the version but i have no clue?
:mad:

---

### Post by marcusdufrane on 2010-08-24
just refreshing his to see if anyone has an ideas this morning.

---

### Post by marcusdufrane on 2010-08-24
So I played around with it some more, still nothing. Though maybe it was the usb to serial cable so i tried a different one, this one actually loaded needed drivers. But still no fix. Does anyone know of a bug in Lucid that may be causing this? Im lost as to why this would happen.

---

