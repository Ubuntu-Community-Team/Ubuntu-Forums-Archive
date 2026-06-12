---
title: "Beagleboard C4 Ubuntu Installation Question"
date: 2010-11-13
forum: General Help
---

### Post by skryne on 2010-11-13
Hi all

I feel rather foolish posting this but I find Linux pretty daunting as I've only started with it in the past few months. 

I am currently attempting to install Ubuntu Maverick 10.10 on my Beagleboard C4. Everything seems to have gone fine but for one thing.

It seems the installation has completed but I am now left with the following on screen...

**ubuntu@omap:"$**

I really don't know what command if any I should input. Has anyone else seen this and if so what did you do?

Thanks :)

---

### Post by cariboo on 2010-11-13
It would really help if you told us a little more about your hardware.

[list]
[*] What is a Beagleboard C4
[*] How much ram
[*] What cpu
[*] what graphics adapter
[*] what network adapter
[/list]

---

### Post by skryne on 2010-11-13
Sorry if I was a bit vague.

I am developing on this platform...

[http://www.liquidware.com/shop/show/BB-C4/BeagleBoard+C4](http://www.liquidware.com/shop/show/BB-C4/BeagleBoard+C4)

"Rev C4 carries an OMAP3530 processor, the 720 MHz, ARM-Cortex A8 processor also found in the Motorola Droid and Palm Pre. The board also features 2GB NAND and SDRAM, which is mounted directly to the processor itself."

And I hope to use the BeagleTouch for interactivity...

[http://www.liquidware.com/shop/show/BB-BT/BeagleTouch](http://www.liquidware.com/shop/show/BB-BT/BeagleTouch)

"With a 480×272 resolution and 262K color touchscreen OLED display, a 20 mm speaker, and a type B-mini interface to RS232 serial, the BeagleTouch snaps directly onto the BeagleBoard to create a handheld tablet computer."


It turns out I just needed to re-boot, however my problems have not ended there. I had intended to install the desktop version of Ubuntu onto this BeagleBoard, however the version I did install was rather different than I expected.

I sourced them here...
[http://elinux.org/BeagleBoardUbuntu#Demo_Image](http://elinux.org/BeagleBoardUbuntu#Demo_Image)
and with a lot of help installed Maverick 10.10. But it seems to be a more of a developmental version of Ubuntu than I expected. 

All I really need to do is to get the Adobe Flash Projector running on the BeagleBoard and to launch on startup. However the Linux projector will not run, which surprised me as it ran fine on Ubuntu on my MAC and I thought that seeing as it was a Linux version of Adobe Flash it would run on any Linux environment.

Basically I need the last Linux download option here..
[http://www.adobe.com/support/flashplayer/downloads.html#fp10](http://www.adobe.com/support/flashplayer/downloads.html#fp10)
"Download the Linux Flash Player 10.1 Projector (TAR.GZ, 4.02 MB)"
to install and run but that is proving difficult.

Any suggestions would be of great help.

---

### Post by donaldparkerii on 2010-12-06
You must obtain your copy of the Flash Player from TI directly, 
[http://focus.ti.com/docs/toolsw/folders/print/adobeflash-a8.html](http://focus.ti.com/docs/toolsw/folders/print/adobeflash-a8.html)

---

