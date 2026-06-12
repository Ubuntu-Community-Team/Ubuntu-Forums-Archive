---
title: "Multiple issues dealing with booting itself"
date: 2011-05-12
forum: General Help
---

### Post by M5000 on 2011-05-12
So, I'm obviously a new user to the whole Ubuntu scene, and I'm not exactly sure where I should put this, so I'll post here, if I'm wrong please redirect me to somewhere more appropriate. Either way, I need some help here. I've had Ubuntu before on my main computer that I'm writing this from but Grub got me angry and I just deleted the partition it was on, they say it's better if you can dedicate a whole machine to it at least for beginners, and I'm not sacrificing my gaming rig. See if you can figure this one out, boys.

Anyway, the story goes as follows: 
At school they're making room for storage. Long story short, I managed to procure a new (to me) laptop, which is a Jetta C230 (That is, a lower-end laptop)-For free. It needed some RAM, so I managed to fit the sticks from my old semi-broken HP Pavilion into it. It turned on and got to Windows that was already installed. I got Ubuntu downloaded and installed to a flash drive, I ran it and installed it from the flash drive. And that's where my issues began. When I installed, I formatted the drive, wiped it clean of everything, finished up, and removed my flash drive (At this point, Ubuntu should be installed on the hard drive). When I restarted, the first time at least, the system went through the BIOS super fast and booted like gold; it went into Ubuntu and started doing its little updates and stuff. I'm messing around with a few configs and stuff and it freezes. Just like the Windows I'm so used to. Needless to say at this point I'm a bit confused, there seemed to be no chance of any responsiveness so I forced a shutoff and re-started, hoping to resume the updates. Well, this is where it gets interesting. Upon restarting, the BIOS is slow as all getout again (which is to be expected on an old PC) but I also noticed that the hard drive isn't showing up in my boot options; the only thing I get is what appears to me to be my USB hub or something, it's the same label my flash drive has, but no hard drive. I'm weirded out so I put my flash drive back in and look in my devices, sure enough, the hard drive pops up in my boot menu. I set it as the first boot device, restart with my flash drive in, and I get some Intel boot manager saying there's no storage media inserted or something. (When I first had it, I could use the "any key" to boot XP.) My two issues I need solved at this time are as follows: How can I get the Intel boot manager to go away and let Grub do the work? (If it's even installed, I don't know.) And what is the issue with my hard drive? I even tried re-seating the whole dealy and nothing helped. 

Processor: Intel Pentium M 1.5 ghz
RAM: 512MB DDR SO-DIM
HDD: 20 GB
Computer manufacturer/model: Jetta C230

Alright guys, that sums up about all the info I can give you. This is pretty much a Ubuntu n00b who is totally used to Windows who just wants a laptop that works and can experiment with Ubuntu on. 
Thanks in advance, 
M5000

EDIT: IF it helps, my computer is emitting a strange sound that is not unlike Chewbacca. I don't know if it's the hard drive or not, I'm pretty sure it's just the GPU fan though.

---

### Post by M5000 on 2011-05-12
Bump, can I get a bit of help here please?

---

### Post by Quackers on 2011-05-12
I strongly suspect that the hard drive just died. And the noise could be the drive self-destructing.
I am no expert on this subject, but that's what it sounds like to me.
Can you take it out and test it in another pc?

---

### Post by M5000 on 2011-05-12
> **Quackers said:**
> I strongly suspect that the hard drive just died. And the noise could be the drive self-destructing.
I am no expert on this subject, but that's what it sounds like to me.
Can you take it out and test it in another pc?
I really don't think it's dead because I'm sitting here right now and I have my USB stick in, and the hard drive is now showing. It only goes away when I boot without the USB stick in. Do you think it would have anything at all to do with the persist file (?) that the pendrivelinux program puts on there?

---

### Post by Quackers on 2011-05-12
Is it possible that the bios is recognising your USB stick as a USB HDD and is still not seeing the actual internal drive? What size is the drive showing in bios?

---

### Post by M5000 on 2011-05-12
> **Quackers said:**
> Is it possible that the bios is recognising your USB stick as a USB HDD and is still not seeing the actual internal drive? What size is the drive showing in bios?
I also get an error before entering CMOS that says "CMOS Settings Incorrect" and "Date/Time Not Set."

No.. Wait.. I just realized something. It's showing an HP "Hard Drive" yet I know that the hard drive is Toshiba. My flash drive, however, is an HP. I think you were right on the hard drive, unfortunately. I'll see what I can do from there. I have another 80 Gig from the same computer, I'm not sure I want to format it or not but I'll have a look see. 
Anyhow, thanks for all your help, that's all I need for now, I'm sure I'll be back with questions on how to install things once I actually get myself set up. Cheers;
-M5000

---

### Post by Quackers on 2011-05-12
No problem.
I hope you have better luck with the other one! :-)

---

### Post by M5000 on 2011-05-12
> **Quackers said:**
> No problem.
I hope you have better luck with the other one! :-)
Yes, it was the hard drive, I have the new one in and it's working just like it did in the old laptop, except the screen actually lights up. XD

---

### Post by Quackers on 2011-05-12
Good luck to you then :-)

---

### Post by Blasphemist on 2011-05-12
I agree with quakers. Boot to the usb and run any disk utility. I bet the hard drive doesn't show up.

---

