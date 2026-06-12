---
title: "Bluetooth hid and tomtom go remote"
date: 2009-11-04
forum: General Help
---

### Post by markp1989 on 2009-11-04
i read on other forums that the bluetooth remote is detected as a bluetooth keyboard. all guids on the interent are eaither out of date, or tell you to use the graphical bluetooth utilities, that i dont have installed, as i started from a command line install.

i have installed the bluez-compat and bluez packages 

hcitool scan sees the remote
mark@torrentslave:~$ sudo hcitool scan
Scanning ...
	00:13:6C:BC:29:43	TomTom Remote


 but i cannot connect to it
mark@torrentslave:~$ sudo hidd --connect 00:13:6C:BC:29:43
Can't create HID control channel: Connection refused


i have a feeling that its using the wrong passcode , the remote book says the passcode is 0000 , but i think ubuntu is trying to connect with passcode 1234. 

how can i change the passcode that hidd connects with?

thanks Markp1989

---

