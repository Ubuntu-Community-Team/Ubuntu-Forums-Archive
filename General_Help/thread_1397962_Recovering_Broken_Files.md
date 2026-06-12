---
title: "Recovering Broken Files"
date: 2010-02-03
forum: General Help
---

### Post by mediumone on 2010-02-03
Hi,

I installed Ubuntu 9.10 on a 100 GB partition of my 120 GB hard disk. I left the other 20 GB as free space. I moved my data (about 20 GB) to my home folder. Everything was fine for two days. Then I installed a few packages with the help of Update Manager. After the installation, I was asked to reboot. Upon reboot, I was always taken to the Memtest86+. It was as if GRUB wasn't detecting my ubuntu installation.

Then I installed Ubuntu again by taking up 20 GB of the existing 100GB partition. I am currently using this installation. When I try to access the older installation (the 80 GB one), I find that all my data in my home folder is broken. (screenshot attached - homefolderbroken.png).

 [ATTACH]145930[/ATTACH]

When I see the properties of the 80GB partition, I can find my data is still present (screenshot attached - data.png). 

[ATTACH]145929[/ATTACH]

Is there anyway I can restore my data? Thanks!

---

### Post by mediumone on 2010-02-04
I ran the "ecryptfs-mount-private" command in the terminal. I am getting a new error - 
 
>  ERROR : Encrypted private directory not setup properly. 
 
See attached image.
 
[ATTACH]146025[/ATTACH]
 
What does this mean? How can I recover my data?

---

### Post by mediumone on 2010-02-05
Few more things I found out - 

1. Grub2 doesn't list any Ubuntu installations. It only shows 2 entries - memtest86+ and memtest86+ console mode (or something). 

2. There is nothing in my /boot/ directory except for a directory called grub and a file called memtest86+.bin. 

[ATTACH]146108[/ATTACH]

What happened to all the other files? Could this be the same issue mentioned in this link - [http://ubuntuforums.org/showthread.php?t=1307643](http://ubuntuforums.org/showthread.php?t=1307643) ?

Should I make any changes in the grub.cfg to get my installations listed in Grub2 menu?

---

