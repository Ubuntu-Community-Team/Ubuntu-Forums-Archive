---
title: "Grub, Raid and windows--Please help!"
date: 2006-04-19
forum: General Help
---

### Post by richardward101 on 2006-04-19
Just having my first taste of ubuntu, got most things working the way i want them to, but having problems dual booting with windows. This is how linux sees my drives:

hd0    80GB, ubuntu intsalled here
hd1    150GB
hd2    150GB

the final two drives arre actually a SATA RAID-0 array with two partitions, one with windows, the other for media. I can mount these partitions using /dev/maper/sil_agadebcbccff1 and /dev/maper/sil_agadebcbccff2 respectively, and there is also /dev/maper/sil_agadebcbccff, which i am assuming represents the drive as a whole rather than the partitions. I cannot, however get grub to boot XP, the only way i can find to do it is to change the bios boot order every time i want to switch OS.
I'm very impressed with ubuntu but i still need xp until wine can play all the games i want it to.
I've found a lot of forum posts about linux being on a raid array, but not windows.
Any suggestions would be greatly appreciated.

---

### Post by richardward101 on 2006-04-19
I've searched loads of forums for this to no avail, if anyone has even a sugestion or somewhere to look i really appreciate it!
Thanks in advance!

---

### Post by jworr on 2006-04-19
I have been browsing the web and the best I could is this

[http://www.aoaforums.com/forum/64-bit-computing/25365-how-do-i-dualboot-xp64-raid0.html](http://www.aoaforums.com/forum/64-bit-computing/25365-how-do-i-dualboot-xp64-raid0.html)

But honestly what I would do is leave the windows raid system alone 

then I would unplug them from the mother board

next I would hook up another drive and  install ubuntu on it and put grub on it

then I would plug the raid array back in so all three disks are connected

I would the just use the bios to set the primary hard disk (or raid group) to choose what os to boot into


alternatively

I would leave windows alone

install ubuntu on the other hardisk but don't install grub

then boot off a linux boot disk and choose what os from there

I have never used a linux boot or recovery floppy but I know they can be made


I hope this helps you

---

### Post by echo $USER on 2006-04-19
[QUOTE=jworr]

I have never used a linux boot or recovery floppy but I know they can be made


[/QUOTE]
To make a bootable floppy throw one in and run from terminal: "mkbootdisk your_kernal_version" without the parenthesis.  To find out waht kernal version you are using type into terminal "uname -r".  

I'm interested in this topic as well.  I have a raid0 on my windows gaming machine.  I use badger on a old hp and dual boot windows and badger on my laptop.  I would like to install badger or dapper on my gaming machine but still want to dual boot windows.  I have tons of torrents, games, and programs on my game machine that i dont want to ruin if I muck up my raid array.  I dont think ill attempt anything until i have a definative answer.

---

### Post by richardward101 on 2006-04-19
Ok thanks guys, I'll give these a try. What has occoured is that i could just have my BIOS look at Floppy then my windows HD, so i can leave my floppy in for linux and eject it for xp - not perfect but would work. I'll let you (echo) know how it goes.

The main problem withg this is just one of lazyness, as  my case has a motorised sliding cover that fouls any floppy sticking out of the drive.

---

### Post by GriFF3n on 2008-04-14
I'm having the exact same problem as the original poster and didn't want to start a new thread. Has anyone found the answer to this problem? Maybe using a different booter, like boot camp?

GriFF

---

