---
title: "can not boot Please help"
date: 2011-03-23
forum: General Help
---

### Post by GeoLasha on 2011-03-23
Hey guys, my Ubuntu 10.10 was working perfectly. I had grub2 and everything with single OS so I decided to add xp for the dual boot because I needed some software but after I installed Xp it automatically goes to boot xp without even asking me if I want ubuntu. Basically Xp partition became a boot partition. I logged from live cd and changed boot partition back to the ubuntu  partition with Gparted and when I restarted it hanged at blinking "_" doing nothing. I need help please, I have everything on my Ubuntu and I can not tolerate loosing it so how would I possibly boot and make my Ubuntu Partition as a default boot partition because that is where my Grub2 is.

THank you very much and I am waiting for response, this is emergency.

Lasha

---

### Post by kiyop on 2011-03-24
Please read 
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Boot with Ubuntu Live CD and mount the partition containing your installed ubuntu / partition (with /boot directory inside) by clicking
"Places" -> ...
Find the mounted directory by typing "CTRL" + "L" on file manager.
The mounted directory may be
[COLOR=blue]/media/....[/COLOR]

Open 
"Application" -> " Accessary" -> "Terminal"
and type 
```
sudo parted -l
```to find out the device file name of your internal HDD, such as
[COLOR=red]/dev/sda[/COLOR]

and type 
```
sudo grub-intall --root-directory=[COLOR=blue]/media/....[/COLOR]  [COLOR=red]/dev/sda[/COLOR]
```Restart and remove Ubuntu Live CD.

<<Edited at 3/24 22:28 in JAPAN>>
If you cannot succeed in booting Ubuntu after finishing the above-mentioned method,
boot with Ubuntu Live CD and open terminal and type the above lines and then,
```
sudo  mount  --bind  /dev  [COLOR=blue]/media/....[/COLOR]/dev
sudo  mount  --bind  /sys  [COLOR=blue]/media/....[/COLOR]/sys
sudo  mount  --bind  /proc  [COLOR=blue]/media/....[/COLOR]/proc
sudo  chroot  [COLOR=blue]/media/....[/COLOR]  /bin/bash
update-grub
exit
exit
```and restart and remove Ubuntu Live CD.

If you cannot boot ubuntu installed in internal HDD, I suggest you to post the result of boot info script.
Get boot info script at:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by gufide on 2011-03-24
[COLOR=Silver]The "easy solution" will to re-install ubuntu by override the ubuntu partition by going to "advanced partitioning tool" in the ubuntu installation, then, delete your ubuntu partition, make a new "swap" partition of 4Go, after make an "ext4" partition that take the rest of the place and put a "/" for the boot path. Make sure that you backed up your files. This solution should make you able to boot to xp or ubuntu thought grub2

The "hard solution" is to go to the recovery mode and repair it.

[COLOR=Black]You should follow the [/COLOR][/COLOR][kiyop]("http://ubuntuforums.org/member.php?u=1246530") solution... I think this is the best one[COLOR=Silver][COLOR=Black].[/COLOR]
[/COLOR]

---

