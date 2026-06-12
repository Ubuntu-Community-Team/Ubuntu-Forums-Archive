---
title: "Grub bs....=("
date: 2009-11-21
forum: General Help
---

### Post by Goldfish! on 2009-11-21
Okay first things first I am not a Linux fanboy but I like Ubuntu. It still has the lin-sucks ugly to it but it is very interesting to a techie like me so there is that.

I just loaded the WIN7 RTM on a BRAND NEW laptop...right out of the box. No shat...right out of the box (netbook and if it were VISTA it would have been a HUGE failure). Tried to set up a dual boot with Ubuntu like I am used to doing. Okay...

This suxors though.

It made me reload it twice (started like a LIVE boot image each time) and finally made a hard install.

There are like 5 boot options in GRUB now. That is annoying. Never had that happen before. I don't know much about editing GRUB and all that and because of that I am afraid to touch it. Any help or ideas would be much appreciated. I just want it to give me the Windows / Ubuntu boot option like it does in XP on my other machines.

Thanx.

---

### Post by hwttdz on 2009-11-21
So from what I understand:
1) there was a reboot cycle during install
2) you now have multiple ubuntu options in the grub menu

You do not specify what verion of ubuntu or which version of grub you are using (try "grub-install --version).  Or if the options in grub are different kernels? or if they all boot? or if perhaps there are multiple installs on different partitions (you can investigate this using gparted)? You should have at least 1) ubuntu boot, 2) ubuntu recovery boot 3) memtest, 4) windows.  Are you seeing more?  What do you expect to be seeing?  What do you see? 

A good howto about grub can be found here [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Finally, formatting your post as above will generally decrease both the quality and number of replies.  I hope in the future you see fit to share as much relevant information as possible and as little else.

---

### Post by Goldfish! on 2009-11-21
It is the GRUB that comes with the latest ISO release. I don't want to reboot to get all the sticky details, spent enough time going WTF about that already with reboots and reinstalls.

Thanks for the link though. Sure I'll figure out with that. Was just getting frustrated.

---

### Post by sisco311 on 2009-11-21
[thread=1287602]Grub 2 Title Tweaks Thread[/thread]

Follow the guide above to turn off the "memtest" and "recovery mode" GRUB menu entries.

The "Ubuntu, Linux <version>-generic" menu entries boot different kernel versions. It is advised to keep at least two working kernels, in case an update breaks the latest kernel you can still boot the old one. You can use Synaptic to remove the old kernel(s). Just search for "linux-image-<version>-generic". **Be careful**, [COLOR="Red"]don't[/COLOR] remove the current kernel!

NOTE: If you remove the "Recovery Mode" option(s)

see [thread=1195275]Grub 2 Basics[/thread] *#10. Booting to Recovery Mode w/o Menu Option*

---

### Post by Goldfish! on 2009-11-21
Exactly what I was trying to take out. Thanks man.

---

