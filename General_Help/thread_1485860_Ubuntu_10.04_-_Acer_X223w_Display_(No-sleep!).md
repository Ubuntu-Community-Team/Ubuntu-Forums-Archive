---
title: "Ubuntu 10.04 - Acer X223w Display (No-sleep!)"
date: 2010-05-17
forum: General Help
---

### Post by A4orce84 on 2010-05-17
Hey Everyone,

I recently installed Ubuntu 10.04 on my desktop and finally got everything working !  (My network card would never work in 8.04 / 8.10, no matter how many DIYs and tweaks I did, so I was very surprised everything worked OOTB with 10.04!)

Anyway, everything works except my Acer X223W refuses to go to sleep (standby-mode) after 10 mins....even though I configured it to do so in the power management options.

I have a NVIDIA GeForce 8800GT graphics card running the "NVIDIA Accelerated Graphics Driver."

I leave my computer on a lot, so I was surprised my screen-saver was still running this morning and the monitor was not in sleep mode.

Anyone know what things to try and get this working?

Thanks in advance!


--Asif

---

### Post by A4orce84 on 2010-05-17
Hey Everyone,

I recently installed Ubuntu 10.04 on my desktop and finally got everything working ! (My network card would never work in 8.04 / 8.10, no matter how many DIYs and tweaks I did, so I was very surprised everything worked OOTB with 10.04!)

Anyway, everything works except my Acer X223W refuses to go to sleep (standby-mode) after 10 mins....even though I configured it to do so in the power management options.

I have a NVIDIA GeForce 8800GT graphics card running the "NVIDIA Accelerated Graphics Driver."

I leave my computer on a lot, so I was surprised my screen-saver was still running this morning and the monitor was not in sleep mode.

Anyone know what things to try and get this working?

Thanks in advance!


--Asif

---

### Post by kooia on 2010-05-17
Well, I think you're lucky.  Mine goes into sleep mode and I can't wake it up.  I have to hold the power until it wakes up again.

[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)
or
[https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops)

---

### Post by A4orce84 on 2010-05-18
Sorry let me clarify, the display is not a laptop, its an actual external monitor:

[http://www.amazon.com/Acer-X223W-Widescreen-LCD-Monitor/dp/B002TS8Z7Q](http://www.amazon.com/Acer-X223W-Widescreen-LCD-Monitor/dp/B002TS8Z7Q)

---

### Post by Youresorock on 2010-05-18
My Dell Mini9 will also not sleep the screen.  Anybody have a tip?

---

### Post by lisati on 2010-05-29
Threads merged

---

### Post by mgmiller on 2010-06-03
I have a 64 bit install of 10.04 upgraded from 9.10.  I have had this problem on and off for a while now.  It only exhibits this behavior after a reboot.  All I do is log off and back on and that seems to do the trick.  Since I rarely reboot this machine, it hasn't bothered me too much.  I have a geforce 8600GT driving a 25" Samsung.

---

### Post by mrinehart93 on 2010-06-03
I have an Acer x203w which is just the 20" version of your monitor. Mine sleeps and wakes up perfectly. I also have a nVidia 9800GT which is 99% the same as the 8800GT. I installed the driver while enabling compiz-fusion. I setup the sleep/wake through System->Preferences->Power Management.

---

### Post by A4orce84 on 2010-06-27
Did not fix the issue unfortunately.

Anyone else have any tips? =(

Thanks!


--Asif

---

### Post by A4orce84 on 2010-07-08
bump

---

### Post by torpidnotion on 2010-07-15
I am also having this problem with a Geforce 8600GT and an Acer P244W 24" connected via HDMI.  Running 10.04 64-bit.

All of the following commands successfully set the monitor into suspend manually:
torpid@helios:~$ xset dpms force off
torpid@helios:~$ xset dpms force standby
torpid@helios:~$ xset dpms force suspend

---

### Post by A4orce84 on 2010-08-21
I'm not sure I understand your commands, are you saying this FIXED your issue with suspend?

Anyone else have any luck?

---

### Post by torpidnotion on 2010-08-21
No, I didn't fix it, but setting the display manually into sleep mode using those commands suggest that it's NOT a problem with the hardware itself.

---

