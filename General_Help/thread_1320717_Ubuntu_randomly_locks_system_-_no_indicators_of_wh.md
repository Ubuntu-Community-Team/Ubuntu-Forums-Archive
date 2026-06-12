---
title: "Ubuntu randomly locks system - no indicators of why"
date: 2009-11-09
forum: General Help
---

### Post by lipinski on 2009-11-09
My Ubuntu system, running 9.10, recently starting freezing up entirely.  Things were going great, I have had very few problems with this system.  Then all of a sudden (i.e., no system nor SW changes immediately preceding), my system started locking up.  

And, I mean locking up hard - entirely non-responsive.  No mouse response, no keyboard response (including caps/num locks), no ping response and thus no ssh.  The only way out was to press the reset button.  I also tried the Alt-SysRq + REISUB combination to no avail (although I've never used that one before, so never seen it work).

I cannot pinpoint any particular cause.  Sometimes the system is idle (with screensaver), sometimes, surfing the web, sometimes, checking email, etc.  I cannot find a common trigger.

I have looked through /var/log and cannot find any indication.  messages shows the standard --MARK-- entries every X minutes or whatever, then they stop, then the entries for the boot-up.

There is no consistency to the interval of this either.  As of two weeks ago, this never happened.  Now, it happens sometimes when system has been on for 30 min, sometimes, after 4 hours.

Right now I'm running a memtest scan to see if I have some newly problematic memory.

Any other ideas on how to get to the bottom of this issue?

Note: I'm submitting this post via my work-provided laptop while the memscan is running on my system.  Otherwise, I'd post some HW specs.

---

### Post by jbrown96 on 2009-11-09
When the system locks up, is Xorg still active? By that I mean, can you see the desktop, screen saver, etc. or is it just a black screen with the back light on/off?

---

### Post by lipinski on 2009-11-09
> **jbrown96 said:**
> When the system locks up, is Xorg still active? By that I mean, can you see the desktop, screen saver, etc. or is it just a black screen with the back light on/off?

If the screensaver is on (in my case a blank screen), or if the monitor is "off" in power-save mode, then it will not come back on.  Moving the mouse, pressing keys, etc., the desktop will not be painted nor will the monitor resume if "sleeping".

If the lockup occurs when the screensaver is not yet on, then the screen remains displayed, but there is no response to user input.  So, I still see all my windows, desktop, etc.  (on-screen Clock does not change as time passes)

---

### Post by anselm on 2009-11-09
This seems to be a problem with the Intel video drivers, their are other threads about your same problem, no real fix as of yet.

---

### Post by lipinski on 2009-11-10
I don't know if it would be the Intel driver - because this system was running previously with no issues.  But, it's always a possibility.

What I did find is that my PC will now shut itself off during a MemTest86 scan.  Don't know why, and don't have time to watch it entirely, but somewhere between 1-2hrs of memory scanning, the system just powers off.  It's actually difficult to power back up, I think the last time, I had to not only turn the rear power switch off, but also unplug it.  

So, now I'm leaning towards a memory or power supply problem.

Any suggestions on how to narrow it down?  

Personally, I'm thinking about swapping out the P/S since I have a spare one of those, but no spare (compatible) memory DIMMs.

---

### Post by jbrown96 on 2009-11-10
If it is a PS problem, then you should replace it soon. A variable current from the PS can damage your hardware. 

You could also try removing some of your RAM, and then trying memtest. This takes a long time though... If you have 3-4 DIMMS, then leave two and run memtest. If there's no problems then swap for the other two. Hopefully you can narrow it down quickly.


You could also try an older kernel when booting the machine. If it is a kernel problem, then it wouldn't happen until the next reboot, and maybe you forgot there was an update. You may need to hold shift at the beginning of booting, to get the grub menu.

---

### Post by lipinski on 2009-11-11
ok - so it was all an overheating problem.

After investigating using sensors/xsensors, I noticed my CPU was pushing 65C when my system was almost idle.

I removed the heatsink, cleaned off the stock thermal tape and put new high quality thermal grease.  My CPU is now running around 50C.  

Thanks to all that posted suggestions.

---

### Post by jonathanparris on 2010-01-11
After Mouse locks up I am able to re engage the pointer by connecting a USB 3D optical mouse. My primary mouse is a Cordless Logitech Optical Mouse. This happens randomly while using Ubuntu 9.10 Karmic. Also happened in 9.04 Juanty before I upgraded. Here is the /var/log/messages from terminal after the primary mouse froze and I connected the USB. Let me know if there is anything else I can provide to help with this issue.

CONF(NETDEV_CHANGE):  eth0:  link  becomes  ready Jan 11 14:34:28
desktop kernel:  [    25.824432]  usb  1&#8208;4:  usbfs:  interface  1
claimed by usblp while &#8217;usb&#8217; sets config #1 Jan 11 14:35:28 desk&#8208;
top kernel: [   86.724031]  Clocksource  tsc  unstable  (delta  =
&#8208;272756943 ns) Jan 11 14:39:17 desktop pulseaudio[1595]: ratelim&#8208;
it.c: 66 events  suppressed  Jan  11  14:39:17  desktop  pulseau&#8208;
dio[1595]:  asyncq.c:  q overrun, queuing locally Jan 11 14:39:48
desktop pulseaudio[1595]: last message repeated 10 times  Jan  11
14:40:11  desktop  pulseaudio[1595]: ratelimit.c: 368 events sup&#8208;
pressed Jan 11 15:07:54 desktop kernel: [ 2032.302063] hda&#8208;intel:
IRQ  timing workaround is activated for card #0. Suggest a bigger
bdl_pos_adj.  Jan 11 15:15:49 desktop kernel: [ 2507.648060]  usb
2&#8208;7: new low speed USB device using ohci_hcd and address 4 Jan 11
15:15:49 desktop kernel: [ 2507.860307] usb 2&#8208;7: configuration #1
chosen   from   1  choice  Jan  11  15:15:49  desktop  kernel:  [
2507.871709]    input:    USB    Optical    Mouse     as     /de&#8208;
vices/pci0000:00/0000:00:0b.0/usb2/2&#8208;7/2&#8208;7:1.0/input/input14  Jan
11  15:15:49   desktop   kernel:   [   2507.871860]   generic&#8208;usb
0003:15CA:00C3.0003:  input,hidraw2: USB HID v1.10 Mouse [USB Op&#8208;
tical Mouse] on usb&#8208;0000:00:0b.0&#8208;7/input0

Havent yet found a fix to this problem.....anyone have any ideas

---

