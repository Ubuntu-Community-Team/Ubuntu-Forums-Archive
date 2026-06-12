---
title: "Fixing X on 9.10"
date: 2010-04-01
forum: General Help
---

### Post by hangfire on 2010-04-01
The video card died on my old server, I want to spend $0 to fix it so I put in an old S3 Virge PCI video card. I just need to set up a bunch of stuff under X and then I can leave it alone for another few months before I replace it.

The old video card works showing the BIOS and Kubuntu 640x480 startup graphic, but once it gets to X login it breaks. I try to log into an alternate console but apparently X is in a restart cycle as I lose the text mode screen and can't get it back for a long time, at which point that alternate console is back at the login prompt... until it goes away again a few seconds later.:sad:

So, I tried to boot into Grub but hitting Esc (or spacebar, or any other key) as it goes past the Grub boot prompt. After several tries I got up to about 100Hz of button pushing to no avail. Grub steadfastly ignores anything I do to get its attention. The keyboard is functional at that point because I can hit delete a little earlier in the boot cycle and get into the BIOS.

So, I booted a 9.10 Live CD. I mounted /boot and see the kernel image, etc., but can't find menu.lst under grub/ or anywhere in there, to edit the startup wait time.

Questions:
1. From the Live CD, how do I fix grub to let me log in? I can't even find menu.lst under <mountpoint for /boot>/grub/.

2. How do I fix X, or at least start to fix X for the S3 Virge, from a Live CD, and/or continue once Grub is fixed?

I used to be able to switch the link for X to the appropriate driver but apparently that is not the way it is done anymore.

Please help!

---

### Post by hangfire on 2010-04-01
Bump.

---

### Post by brujoand on 2010-04-01
what if you choose to boot in "recovery mode" and choose to be dropped to root shell, try "dpkg-reconfigure xserver-xorg" to reconfigure x, then reboot.

---

### Post by hangfire on 2010-04-01
Thanks for responding.
> **GrimmVarg said:**
> what if you choose to boot in "recovery mode"

I've been choosing, but the boot loader wasn't listening.

I think I just made progress on this question. I've discovered why my Grub googling hasn't brought answers. I'm running grub2. In the Community Documentation I found the following:

```
# Hold down SHIFT to display the menu during boot (formerly ESC in GRUB legacy).
```
A pointless change that cost me an hour, this is as bad as changing Ctrl-Alt-Backspace.

> **GrimmVarg said:**
> 
and choose to be dropped to root shell, try "dpkg-reconfigure xserver-xorg" to reconfigure x, then reboot.

Thanks... I left out this step when describing how I got here. After booting the "new" card, I did run "sudo dpkg-reconfigure xserver-xorg". That didn't fix X immediately, so I did a shutdown and cold boot. That's when the current issue I have started. Once I get past that, I think I'll need more than the **dpkg-reconfigure** command, since that is what got me here in the first place.

Apparently there are special issues with this old card and modern xorg. While not surprising considering its age, this used to be an old stand-by 2D card that always worked when the fancy stuff didn't. That's the only reason I kept it.

-HF

---

### Post by hangfire on 2010-04-09
I accomplished what I wanted to, limping along on the old PCI card for a few days and getting some data off of that system before moving the hard disk to all new hardware. The fix was copying the generic VESA xorg.conf from the LIVE CD to the disk.

9.10 was extremely friendly towards my new generation 4200 integrated video. I removed the VESA xorg.conf, did one dpkg-reconfig and that's it. 1920x1200, OpenGL and all video formats are working fine with zero effort. I guess the old standby wisdom that Linux is more friendly towards old hardware and nVidia video is no longer the case. 

Kudos to the Ubuntu team and AMD/ATi for working together to support newer hardware.

-HF

---

