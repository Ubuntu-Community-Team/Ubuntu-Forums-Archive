---
title: "Scrambled win7 desktop on installing Ubuntu x64 10.10"
date: 2010-12-07
forum: General Help
---

### Post by SnoopNL on 2010-12-07
Hello,
 
Since I get no response for 2 days now I see my old threath as closed.
 
I have 2 harddrives.
I found out both are Sata (sorry)
They are connected to a ICH7 Intel controller wich is built in into my chipset.
Here are my specifications:
 
MSI MS7528 G31M3
4096MB DDR2 RAM 2x 2048MB
1x 320GB Samsung HDD
1x 250GB Maxtor HDD
1x DVD-RW Optiarc
Nvidia Geforce GT240 GDDR5 512MB XFX
 
Here is the problem:
Every time I try to install Ubuntu x64 10.10, does not mather from USB or CD, I get the problem that I see my Windows 7 x64 Desktop all scrambled up.
A picture of this can be found here:
[http://img3.imageshack.us/i/imag0099c.jpg/](http://img3.imageshack.us/i/imag0099c.jpg/)
 
So I tried the following:
MD5 checksum check , the checksum matches.
Redownloaded the image, same problem.
Deactivated Kaspersky Internet Security 11.0.1.400 and tried making the USB again: Same problem.
Deactivated my entire Sata controller ( windows 7 is not accesible , nor even the harddrives). I still get the image shown before of the windows 7 desktop!
So I figured maybe the image is somehow still not good.
So I tried the iso in a VMWARE and guess what : succes!
 
After that someone else suggested to change the boot order of my HDD, still the same problem.
 
I am really stuck here and hope someone can help me with this.
Any suggestions here?

---

### Post by bobmanuk on 2011-04-03
Hi SnoopNL,

Im sorry i havent got much in the way of answers for you, i do however have almost exactly the same issue you do.

all my details are here
[http://www.linuxquestions.org/questions/showthread.php?p=4312188#post4312188](http://www.linuxquestions.org/questions/showthread.php?p=4312188#post4312188)

it seems the only thing we have in common is the XFX GT 240.

I remember i had a lot of issues with the graphics card when installing windows, random blue screens and crashes, until i had removed the graphics card, installed windows, installed nvidia drivers then re-plugged the card back in.

what do you think?

---

### Post by SnoopNL on 2012-11-01
Hi boobmanuk,
 
Another forum member helped me and we got it sorted all that time ago.
Seems the Nvidia GPU locks up or something.
 
So do the following if you want it working and working every reboot:
I got it working!
trick was : load the failsafe drivers.
Then install the updated nvidia driver.
Reboot
Done!
 
Al credits go to : Hippytaff :)

---

