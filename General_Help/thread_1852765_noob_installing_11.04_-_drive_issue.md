---
title: "noob installing 11.04 - drive issue"
date: 2011-09-30
forum: General Help
---

### Post by ResilientMonkey on 2011-09-30
Hello folks!

I am attempting to install Ubuntu 11.04 on my PC.  I have 2 250GB drives, one has Windows 7 on it, the other is empty.  I plan to use this second drive to install Ubuntu on it.

Installing from CD:
I click on "Install Ubuntu".  I walk through the installation wizard until I get to "Allocate drive space".

I get this information:
Device
/dev/mapper/nvidia_ghbaghba
 free space
/dev/mapper/nvidia_ghbaghba1

For some reason it is not showing me /dev/sdb which is my empty drive.  I can see it in GParted.

Trying GParted:
Attempt to create partitions - error "Daemon is being inhibited".

How can I prepare my drive to install Ubuntu?

---

### Post by ResilientMonkey on 2011-09-30
Well, after some more digging, I found this:

[http://ubuntuforums.org/archive/index.php/t-1026362.html](http://ubuntuforums.org/archive/index.php/t-1026362.html)

I determined that it was reading my drives as a raid array so I used the terminal to remove the raid information.

I was then able to properly format the drive and continue installation.

---

