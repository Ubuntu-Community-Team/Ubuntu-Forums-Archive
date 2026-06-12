---
title: "Xubuntu crashes during the work"
date: 2012-03-19
forum: General Help
---

### Post by GreatDanton on 2012-03-19
I do not know how to name my problem, but anyway.
I discovered that sometimes my xubuntu, during the work, get a black screen itself. That is not a screensaver! Then the display is cycling during 3 phases. 1 phase is black screen, then second phase is little window on the top of the monitor (that window is green with white stripes), and in 3 phase i got black screen again with some text on it (it says something like this: pulse audio [OK], checking battery [OK] )

Does anybody knows what causes the problem?

My computer: Dell inspiron 1100
512 Mb RAM
40 GB HDD
Graphic card is integrated

---

### Post by ajgreeny on 2012-03-19
> **GreatDanton said:**
> I do not know how to name my problem, but anyway.
I discovered that sometimes my xubuntu, during the work, get a black screen itself. That is not a screensaver! Then the display is cycling during 3 phases. 1 phase is black screen, then second phase is little window on the top of the monitor (that window is green with white stripes), and in 3 phase i got black screen again with some text on it (it says something like this: pulse audio [OK], checking battery [OK] )

Does anybody knows what causes the problem?

My computer: Dell inspiron 1100
512 Mb RAM
40 GB HDD
[COLOR=Red]Graphic card is integrated[/COLOR]
And what card is it?  Use ```
sudo lshw -C display
``` and copy output back here if you don't know.

---

### Post by GreatDanton on 2012-03-20
Here is my screen shot

---

### Post by GreatDanton on 2012-03-26
bumping this from page 2.

---

### Post by Rodney9 on 2012-03-26
Som of the tips here - 

[http://ubuntuforums.org/showthread.php?t=1797977](http://ubuntuforums.org/showthread.php?t=1797977)

should help.

Rodney

---

### Post by GreatDanton on 2012-03-28
Thank you for this post. It really helped me. Just one problem remains. I have downloaded A32 Bios update from Dell page. Can anyone tell me how to run this program, because of the format (.exe) and i cannot run it with my linux.

How to solve this?

---

### Post by GreatDanton on 2012-03-31
I found this site:
[https://wiki.archlinux.org/index.php/Flashing_BIOS_from_Linux](https://wiki.archlinux.org/index.php/Flashing_BIOS_from_Linux)

---

### Post by GreatDanton on 2012-04-08
Hi again.
I created one more partition with windows xp cd, install windows xp on it, and then i flashed BIOS. Now my BIOS is A32 (the latest :)). After upgrading my Bios i deleted the whole Hard disk, and now I have installed only Linux Xubuntu 10.04. However now, during the boot, i get black screen (i cannot log in).I changed (like i read on the forums):

etc/default/grub
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.modeset=1"

The problem is now solved! The solution worked fine.
I also installed Ubuntu 10.10 and i can say that Ubuntu 10.10 is much more stable operating system than xubuntu. I can also say that the Ram and Cpu usage is very simmilar to xubuntu, so there aren't much difference between them.

---

