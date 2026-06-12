---
title: "Suggestions for screen freeze and random reboot"
date: 2011-06-27
forum: General Help
---

### Post by bobnutfield on 2011-06-27
Hello Everyone,

I have an old P4 desktop that I have been trying to set up as a file server in my home.  This was  computer from work that was used for security cameras, and as such, had a PCI card for connecting the cameras, and three 500gb IDE drives.  At work, it began randomly restarting (it was running Windows XP).  Rather than repair, the boss was just going to dump it so I took it home thinking I could isolate the problem and fix it.  Seemed like a good idea as I had been wanting to get an old desktop to use as a file server.  

Somehow, I was able to format the main drive and install Ubuntu 10.10.    These are the symptoms:

1.  When starting from cold, it will boot and run for about five minutes, it will freeze and reboot itself.  
2. When rebooting after it has warmed up, this event takes place immediately after reaching the desktop.

What I have done to isolate the problem:

1.  Replaced the graphics card (it had an ATI, replaced with a nVidia)
2. Replaced the CPU fan (not an overheating issue)
3. Tried a live CD with all of the Hard Drives disconnected (exact same issue occurred.), so obviously not a hard drive problem
4. Noted that the issue is the same with both graphics cards
5. Noted that while in the BIOS is will run just fine as long as I need it to (therefore not a power supply issue)
6. Currently running Memtest with three passes so far and no errors (has only 512mb memory)

This computer has an Asus MB and an American Megatrends bios (from about 2004).  I cannot find any thing that suggests a  CPU malfunction because it does boot and is not overheating.  I have always been able to isolate these kinds of problems in the past to either graphic card failure, power supply failure or memory failue.  It seems to be none of these.  

Can any kind soul with hardware expertise suggest something I can try?  Not the end of the world if I can't fix it, but I thought there would still be some life in it for light duty.

Thanks for any replies



3.

---

### Post by blueridgedog on 2011-06-27
A new CPU fan does not rule out heat.  Verify the CPU temps with lmsensors:

[http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780)

You can feel the heat sink with your hand as well as the chipset.  The thermal paste may be due for replacement.

Also, the power supply may be enough to run the bios, but not the system, but I suspect heat based on what you have listed.

---

### Post by bobnutfield on 2011-06-27
> **blueridgedog said:**
> A new CPU fan does not rule out heat.  Verify the CPU temps with lmsensors:

[http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780)

You can feel the heat sink with your hand as well as the chipset.  The thermal paste may be due for replacement.

Also, the power supply may be enough to run the bios, but not the system, but I suspect heat based on what you have listed.


Thank you.  For the short time that it runs, I was able to check temps with lmsensors.  CPU temp is 31 degrees, fans all working properly.  No excessive heat from the chipset or CPU housing.  Checked all of that first and replaced the thermal paste with the new fan.  Those seemed to be the obvious problems but it doesn't appear to be heat, though I may still find some thing overheating.  CPU overheats (for me anyway) always resulted in a shut down once the failsafe heat was reached.

It may turn out to be heat somewhere, but it does not look like it so far

Thanks for your help

---

### Post by bobnutfield on 2011-06-27
Update:

Not sure what the errors mean, but when running a live cd, just before the freeze, I was able to produce the errors on two different distro live cd's (I am copying from the screen)

Kernel panic - not syncing: fatal exception at interrupt
Pid: 0, comm: swapper tainted: G.       D.       2.6.32-5-686 1

Then it does a call trace listing a number of events and memory addresses:

Panic
Oops
Do invalid op
Hrtimer op
Lapic next event
Clock events program event

Hopefully, this will mean something to someone

---

### Post by blueridgedog on 2011-06-27
Do you have a local shop that can test the power supply?  I have a power supply tester that will put the various voltages under load.  If it were my box and I have access to parts from work and home, I would test another power supply...you have verified cool temps, disconnected all non-essential devices.

One additional step would be to remove all drives, including CDROMs and boot on a USB key..with the hard drive/SATA controller disabled.  You are really down to motherboard/CPU/PSU at this point.

---

### Post by bobnutfield on 2011-06-27
Thank you.  You are probably right, in which case it is the bin for this old dinosaur.  It is not worth investing any money in.  Odd thing is, I had an old live CD of Ubuntu 8.10 and it loaded it and has been running now for about 20 minutes with no freezes or reboots.  Newer versions of any distro live CD would not even get to the desktop before freezing.  

Now been about half an hour with no freezes or reboots.  I wonder if there is something in the newer kernels it doesn't like.  This versi on of Ubuntu live cd is kernel 2.6.27 from 2008.

---

### Post by DawieS on 2011-06-27
I had similar issues with an old motherboard, where the small heat-sink on the (north-bridge ?) was glued, in addition to being held to the board by 2 small spring-loaded pins. After a few years of use, this glue (which looks like mirror tape) became hard and brittle, and the heat sink became slightly loose, only held by the 2 pins, and not making good contact to the surface that it was supposed to cool down.

I fixed it by removing all the glue, and adding a few layers of aluminum foil, with a bit of thermal paste in between. This gave a new life to an otherwise unusable motherboard.

---

### Post by blueridgedog on 2011-06-28
> **bobnutfield said:**
> Now been about half an hour with no freezes or reboots.  I wonder if there is something in the newer kernels it doesn't like.  This versi on of Ubuntu live cd is kernel 2.6.27 from 2008.

Do other OS's have similar issues?

---

