---
title: "Disconnect USB device (or disable USB) before shut down/power off"
date: 2009-10-05
forum: General Help
---

### Post by MilleniumFlyer on 2009-10-05
Hi there,
 
I'm completely new to Ubuntu/Linux, but after using XP (workstation), Vista (business notebook) and Mac OS X (private notebook) I thought it would be nice to have a media center PC with Ubuntu/XBMC :)
So I bought a Antec Case with integrated Soundgraph iMON LCD/IR device, an nVidia ION 330 mb, a harddrive and some memory and started to install Ubuntu 9.04 Desktop with XBMC-standalone.
 
After I spend the weekend with the terminal window, my big three problems (alsa, lirc, lcdproc) a solved - except one issue:
The Soundgraph LCD is connected directly to the computers power supply (to turn it on via IR, i think) which means the backlight is also on when the computer is turned off.
When you use the iMON Software under Windows, the software will switch off the backlight before windows is shutting down. It stays off until you power on the computer again.
 
 
So I tried the same with the LCD server... you have the option to turn the backlight off when LCDd is not running - and this works. So if I use "/etc/init.d/lcdd stop" the backlight switches off. The same will happen when you shut down the computer - BUT: approx. 1 second before the computer is powering down, the backlight will be switched on. I figured out that this will not occur when I unplug the USB cable after the backlight has been switched off - and it will not turn on again if I plug it in again (until I start the computer - which is good!)
 
I think it could be a possible solution to disconnect the USB LCD device in ubuntu right after the LCDd has been killed by /etc/init.d/lcdd stop command. Or, if this does not work, to disable the USB (ports) completly when shutting down (and enabling it again when booting).
If this would be possible it could be easily added to the stop script (I think...). Any suggestions?
 
 
 
And in addition (or as a workaround):
Is it possible to stop LCDd for suspend/hibernation? (As the LCD will have the backlight on in this modes - because LCDd is not stopped) 
Of course LCDd has then to be started again when the computer is powered on.
 
BR,
Markus

---

### Post by MilleniumFlyer on 2009-10-05
Do you think, that this would be possible by running: rmmod usbcore
?

---

### Post by MilleniumFlyer on 2009-10-05
> **MilleniumFlyer said:**
> Do you think, that this would be possible by running: rmmod usbcore
?

It's always nice to answer questions by your one...
There is no usbcore in my ubuntu. I tried with usbhid, lirc_imon, lirc_dev and ... no does not work.
The only solution currently: stop lcdd and use standby or hibernation. **I'm currenty searching for a way to call stop lcdd on hibernation and to start it when the system is woken up ... any ideas?**

---

### Post by MilleniumFlyer on 2009-10-05
Again I would answer the question myself. I just had to copy and modify the 000record file in /usr/lib/pm-utils/sleep.d/

This will be called on suspend/hibernation and if the computer resumes from this states. The problem on shutdown is still there, but I will use the hibernation mode as workaround.

---

### Post by schnubert on 2011-03-08
Hi!

I am experiencing the same issue with the backlight. Did you ever found a fix?

thanks

---

### Post by danellisuk on 2011-09-15
I think this looks like a good thread for us to work together on fixing the backlight issue.

I begrudgingly installed Windows 7 on a spare disk to see what happens to the iMon LCD when the machine is shutdown.  It turns out that the backlight remains off.  So I guess this is good news, in that there must be a way to get this to behave correctly on Linux.  It does seem that something is either happening on the USB bus, or there is a blip on the USB power lines.  I tested the shutdown operation with a USB optical mouse and recorded a video of Ubuntu vs Windows 7.

[http://www.youtube.com/watch?v=qeIBwxCay8M](http://www.youtube.com/watch?v=qeIBwxCay8M)

On Ubuntu notice the LED on the optical mouse "blip" a split second before the machine powers off, which does not happen with Windows 7.  Now I don't know much about USB, hardware or the Linux kernel, but here is my thought on what might be happening.

My theory is that Linux is powering off the USB devices just before the machine is powered down.  Then the BIOS powers down the USB bus, but this operation is causing the USB bus to quickly power on.  Thus causing the "blip".  It might be that Windows is simply not powering off the USB bus, and leaving it to the BIOS.

I have a number of machines available to test on.  So I will start testing for the "blip" on these machines.

---

### Post by henrikost on 2011-09-25
I am having the same problem.

I have however notoced, that if the display is requested to show the ugly clock when the PC is powered down, this works, thus indicating that your 'blib' of failing power is not the case. Also, on my Antec Veris the LCD backlight is powering back on a few seconds AFTER the power is down.

I have another problem: While the remote and LCD is working fine in Natty, I cannot power on the system when it is turned off (not suspended). Under Lucid, this worked fine, and if I (while the system is off) completely remove the power fo a while, I can turn the system on with the remote (once).

I have seen this before woth a Zalman case and an older imon remote. If the USB receiver is initialized, it sends RC power button press to the USB host. If it is NOT initialized, it toggles the hard-wired power button like if the case button was pressed. In the old time, unloading lirc was enough to decouple the USB receiver so it again will toggle the power button line, but this does not work in Natty, not even unloading the various imon modules..

Anyone seen a solution to this?

Regards
Henrikost

---

### Post by Koookie monster on 2011-09-27
I have this issue too. I have the antec fusion remote case with an imon lcd. Using an Asus P8H67-M PRO H67 motherboard. I just solved the problem («knocks wood») and am reporting my findings here.

Turns out it's a hardware issue. The lcd (or its power supply) sucks. Long story short, I resolved the issue by turning off EPU energy saving mode *and* surge protection from the UEFI (bios).

I found the solution here: [http://www.soundgraph.com/forums/showthread.php?t=3815](http://www.soundgraph.com/forums/showthread.php?t=3815)

---

