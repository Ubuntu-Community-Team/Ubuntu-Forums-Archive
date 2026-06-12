---
title: "Grub lost a bootable installation"
date: 2009-12-16
forum: General Help
---

### Post by man_bash on 2009-12-16
I installed ubuntu 9.10 (64 bit) after windows 7 on a new 500 gb drive. Then I connected an old 320 gb drive to retrieve data from linux partitions there. Ran update with the old drive still in, now grub sees the old 9.04, and 2 windows 7 boot loaders, but neither loader works to boot windows 7. How can I restore the old grub?

ASRock 785G AM3 motherboard
PhenomII X2 550
Powercolor Radeon 4870

---

### Post by zero-n on 2009-12-16
Check [[COLOR="Red"]**this**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by JOHNNYG713 on 2009-12-16
In terminal try  sudo update-grub

---

### Post by man_bash on 2009-12-25
Hi guys!

Thanks for the tries, but the advices above did not help.

Zero-n: I could not get grub running the way it was shown in the link (or from liveCD that is) . I used a Karmic 64-bit CD (same one I installed off)

JOHNNYG713: I ran the command, it discovered that the Windows 7 loaders on the other 2 partitions are not valid, but it neither found the actual needed partition to boot off, nor did it remove the invalid entries frum grub record.

Thanks for your help, but i'm still as lost as I was before

---

### Post by Sugi on 2009-12-25
I am having the same issue, and I still can't get it to work for me as well.

Maybe you may have more luck then me.  Here are some really useful links, please spend some time to read through them.
[http://erickoo.wordpress.com/2009/06/14/how-to-add-vista-partition-to-grub-2-ubuntu-9-10-karmic-koala/](http://erickoo.wordpress.com/2009/06/14/how-to-add-vista-partition-to-grub-2-ubuntu-9-10-karmic-koala/)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[http://ubuntuforums.org/showthread.php?t=1296301](http://ubuntuforums.org/showthread.php?t=1296301)

This may not do anything as you have tried something similar, but you could try this as well: $ sudo update-grub2

Ubuntu 9.10 32bit
Windows XP sda1

Good luck and hopefully I helped some,
Sugi,

---

