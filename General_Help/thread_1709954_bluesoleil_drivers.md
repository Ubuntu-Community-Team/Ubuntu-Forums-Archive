---
title: "bluesoleil drivers"
date: 2011-03-19
forum: General Help
---

### Post by pravinvaz on 2011-03-19
Hi 
 
just installed ubuntu, but it did not detect the bluetooth dongle (which has wifi on it as well). Trying to find drivers for ivt bluesoleil (ver 2.7 under windows ) for ubuntu as i dont have the install cd for it. any support here ?
 
this is the closest i got to , although they do not provide a link  to the install file.
 
[http://www.bluesoleil.com/support/Intro.aspx?topic=BlueSoleil_Ubuntu_help](http://www.bluesoleil.com/support/Intro.aspx?topic=BlueSoleil_Ubuntu_help)

---

### Post by wyliecoyoteuk on 2011-03-19
My Tevion USB bluetooth works without the BlueSoleil software.
Unfortunately, BlueSoleil charge for their driver CDs( or they do for the windows ones, didn't know there was a Linux version)

Seems that they want &#8364;19.99 for a license.

---

### Post by wyliecoyoteuk on 2011-03-19
open a terminal and type 

> lsusb

This should list your connected usb devices. My Tevion has no identifier string, (appears a s an address with blank info) but it is detected and it does work, the Bluetooth "B" appears in the top bar, clicking on that allows me to configure it.

---

### Post by YfoMp5QBh2 on 2011-03-19
I have a bluesoleil bluetooth dongle and it worked out of the box without tinkering when I installed 10.04 Lucid Lynx. Have you tried searching for a bluetooth program in the ubuntu software centre?

---

### Post by pravinvaz on 2011-03-22
oh k... somehow this one didnt detect it... the brand name under windows shows as
3DSP bluesoleil by IVT corporation.
Have looked up bluetotth programs in the software centre and downloaded a few, somehow didnt work. 
 
 
> **spadge_2356 said:**
> I have a bluesoleil bluetooth dongle and it worked out of the box without tinkering when I installed 10.04 Lucid Lynx. Have you tried searching for a bluetooth program in the ubuntu software centre?

---

### Post by wyliecoyoteuk on 2011-03-22
What result did you get to lsusb?
That will tell you if Linux is detecting it or not.

If it is, unplug it and plug it in again, then typing 

dmesg

will show you any messages associated with it

---

