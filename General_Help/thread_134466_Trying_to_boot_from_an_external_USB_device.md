---
title: "Trying to boot from an external USB device"
date: 2006-02-21
forum: General Help
---

### Post by niglch on 2006-02-21
I've been at this all week now and I'm sick of bashing my head into error after error trying to get Ubuntu to boot off my USB external HD. So, what I have done so far is installed grub on my External HD and put GRUB in /dev/sdb (the boot section of the external HD). Now when I boot with the external HD on, it brings me to GRUB. However, just trying to boot ubuntu directly doesn't work. I have to hit the 'e' key and change the first line from boot (hd1,0) to (hd0,0) and then hit 'b'. I have no idea why the installer got this wrong. In fact, the (hd1,0) is the windows recovery partition of my internal drive. Also, trying to boot windows XP results in the thing freezing, forcing me to reboot. So, back to booting from (hd0,0), being the actual Ubuntu option, starts loading, and even goes as far as teasing me with the "Ubuntu" loading splash with the progress bar. It says "Loading modules ... OK" and then drops out to the shell saying "Alert! /dev/sdb1 does not exist!". It should though, since I remember it's creation during the install and it also shows up on knoppix as a drive.

I also read the post [here]("http://www.ubuntuforums.org/showthread.php?t=80811&highlight=External+HD") about how another member actually got it to work by using rescue mode of the install CD. I tried getting into this by typing "rescue" as a boot parameter when I insert the install disk. It doesn't bring me to a terminal window though. It brings me to the language selection screen with "Rescue mode" in the corner.

So, yeah, I'm full of problems.

---

