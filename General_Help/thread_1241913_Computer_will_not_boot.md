---
title: "Computer will not boot"
date: 2009-08-16
forum: General Help
---

### Post by mattjones124 on 2009-08-16
Help me Ubuntu forums, you are my only hope.

I left my computer on during a really bad thunderstorm, the power went off at my house, and my computer has not worked since.

When I boot my computer now, the POST screen looks like normal, but it gets stuck at the GRUB menu.  It either gets stuck just saying GRUB, or looks like it is booting normally but then just has a flashing/blinking underscore.  I let it sit at this screen for hours, but it never made it past.

I thought to myself, GRUB must be messed up, I will just boot to a livecd and fix it.  However, when I try to boot from the livecd, it gives states the errors "ATA1.00: revalidation failed (errno=-5)" described in [http://ubuntuforums.org/showthread.php?t=773225](http://ubuntuforums.org/showthread.php?t=773225).  I tried to perform the troubleshooting steps by using acpi=off but it still gives the same error.  

I took a picture of the screen to hopefully give you a better idea of what I am talking about.

[IMG]http://farm4.static.flickr.com/3556/3826502749_6bb62f8da4_o.jpg[/IMG]

It is a pretty standard setup, other than the fact that it has a three SATA hard drive softraid.

Does anyone know how to fix this issue?  Do you require any other information?

---

### Post by cholericfun on 2009-08-16
no idea,
did you try putting the drives in another computer to see if they are still ok. that way you can at least backup your data.

---

### Post by lessgov2007 on 2009-08-16
I'd try disconnecting your hard disks then booting from the LiveCD. If it then boots you've narrowed down the issues to something with the hard disks. 

The whole thunderstorm thing worries me. I've been lucky myself, but my friends computer ended up fried once from a power surge. I'm sure that makes you feel better...

---

### Post by demosthene1 on 2009-08-16
Just a thought...
go into the computer bios and reset it back to default.
Reboot.

---

### Post by lessgov2007 on 2009-08-16
> **demosthene1 said:**
> Just a thought...
go into the computer bios and reset it back to default.
Reboot.
Sounds like a good thought to me! I had a computer once that would have some weird issue, and removing the CMOS battery would make it work again, well, for a while any ways.

---

### Post by mattjones124 on 2009-08-16
So I unplugged the drives, and I can now boot with the livecd.  

Does anyone know a good program that works with softraid that would check the disks for errors that would be causing this?  I know it is more than likely that is a physical issue, but I might as well throw up a hail mary that it is a logical issue.  

What sucks is that my backup system broke a few weeks ago, and my 1 TB worth of media is probably gone.

---

### Post by lessgov2007 on 2009-08-16
In see in the image of the OP "sda", so I'd assume the problem is likely coming from the master disk. You could try only plugging in the master, trying to boot to see if it fails again. If so, it would probably be a good guess the master is creating the issues. As far as software to check the drive. I honestly have no idea. Hopefully one of these guru's around here will know just the thing. Sorry your having such bad luck. Most likely it's only the one hard disk, and the other two are probably alright. If you wanted, you could set one of the other two to a master, hooking both of them up and trying to boot. If you have no issues then you can assume those two drives survived.

---

### Post by bodyharvester on 2009-08-16
> **mattjones124 said:**
> Help me Ubuntu forums, you are my only hope.

that is exactly what princess Leia said on episode 4!:popcorn:

---

### Post by mattjones124 on 2009-08-17
I put the drives back into IDE mode and used Seagate Tools to scan the drives and had one drive fail consistently.  
 
Does anyone know if a tool like Spinrite would resolve this issue, or is it probably a hardware issue and needs to be replaced?

---

### Post by mattjones124 on 2009-08-18
After much fiddling, I got the boot process to make it past the GRUB screen.  I switched around SATA cables and changed which input they connected to, and it gets past GRUB, but goes to the Busybox screen.  Here is a picture:
 
 
 
[IMG]http://farm4.static.flickr.com/3489/3833511242_b532d3551c_b.jpg[/IMG]
 
 
Sorry about the quality.
 
I did not have a chance to do any real troubleshooting, but what would be causing this?  Can a softraid adapt to connections being switched?
 
Any idea why this would happen, or how I can fix it?

---

### Post by P4man on 2009-08-18
eh.. I dont know much about softraid, but that drive you just disconnected, it looks like you really needed it :). Did you have a mirroring raid? Did you mirror everything, including the boot partition (Im guessing you didn't, and thats why its not booting).

---

### Post by wojox on 2009-08-18
> **bodyharvester said:**
> that is exactly what princess Leia said on episode 4!:popcorn:

I thought that sounded familiar.

---

