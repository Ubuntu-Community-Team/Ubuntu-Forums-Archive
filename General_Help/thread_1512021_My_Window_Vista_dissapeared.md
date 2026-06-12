---
title: "My Window Vista dissapeared"
date: 2010-06-17
forum: General Help
---

### Post by Simdog1 on 2010-06-17
K well i was trying to remove some partition since ubuntu took a lot of space so i messed around with ubintu until i found some partition editor. i went in system>Administrator>disk utility then i selected my 320 gb hard disk and deleted partitions (i didnt know what i was deleting them from). i restarted my computer and clicked on my vista on boot menu but i got an error which ive forgoten it was something like no disk. after that i clicked on ubuntu recovery and did update grub, then clicked on repair something (i forgot) it took like 30 minutes to repair but after that my vista dissapeared now i have 2 different linux in my boot menu. 1 is a linux 19 the other is a linux 22. 

please help! i want vista back

---

### Post by pricetech on 2010-06-17
It looks like you deleted your vista partition.  Tinkering with the partition editor is not a good idea if you don't know exactly what you're doing.

You'll need to reinstall vista, then reinstall GRUB.

---

### Post by bcbc on 2010-06-17
try testdisk ([http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk))

You can install it using synaptic as long as you have the universe repository enabled (second checkbox in Software Sources -- under System->Administration)

> TestDisk can
Fix partition table, recover deleted partition

EDIT: if you do manage to get it back, run ```
sudo update-grub
``` to get vista back on your grub menu

---

### Post by QIII on 2010-06-17
Stop and think for a moment.  If your Ubuntu installation is on a separate disk from the one you are concerned about,  you should be able to follow the instructions above with little risk.  It probably would have been difficult in the extreme to modify the partitions on a mounted disk, so I don't guess that is what happened.

However... If Ubuntu is installed on the disk from which you deleted the partitions:

DON'T use your computer any more than you must.  Go to a different computer to communicate with us.

If your data is recoverable now, the more you use the machine, the more likely it is that you will overwrite data that you would like to have recovered.  As it is, you still may be able to recover your partition if you have not done something to overwrite things.

Download some recovery tools like TestDisk and Photorec to CD on a DIFFERENT machine.

Power the machine up with the recovery disk in the tray so that you do not mount your hard drive.

I believe TestDisk has a partition recovery tool.  Both TestDisk and Photorec can recover individual files.

DON'T do this with your HDD mounted, or you may make matters worse.  Don't install anything.  Don't run TestDisk while the drive is mounted.

---

### Post by Simdog1 on 2010-06-17
after test disk is downloaded what do i do? it just a folder with things in it idk which one to run

---

### Post by bcbc on 2010-06-17
Read this first, and load it in a browser for reference.
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

To run testdisk, go to a terminal and run:
```
sudo testdisk
```

---

### Post by proggy on 2010-06-18
> **bcbc said:**
> Read this first, and load it in a browser for reference.
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
you`ll need to install testdisk first
To install testdisk, go to a terminal and run:
```
sudo apt-get install testdisk

``` then try it

---

### Post by bcbc on 2010-06-19
> **proggy said:**
> then try it

or you could just read post #3 again.

---

