---
title: "no space left on device"
date: 2012-01-22
forum: General Help
---

### Post by deadlieststewie on 2012-01-22
this is my first time running ubuntu, or any other operating system other than windows. and i have it working side by side with windows 7.  

so far i love my experience with ubuntu, but i have one problem.  at first it was perfect, as i downloaded so many apps or programs, but now it wont let me download anything and says that there is no space left on device. . since im new to ubuntu, and dont know what im doing i figured this would be the place to come to to fix it.

---

### Post by ajgreeny on 2012-01-22
Have a look at the disk usage with Disk Usage Analyser and you may find what is using all your space.  Meanwhile run ```
sudo apt-get clean
```to remove all the downloaded package files in /var/cache/apt/archives.

How big are your partitions?  Run ```
sudo parted -l
``` to show partitions and sizes

---

### Post by deadlieststewie on 2012-01-22
my partitions are

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1574MB  1573MB  primary  ntfs         boot, diag
 2      1574MB  627GB   626GB   primary  ntfs
 3      627GB   640GB   12.9GB  primary  ntfs         hidden

when i run the pther doe you gace me all it does is ask for my password and then does nothing.  ill try to check my disk usage analyzer and post it here.

---

### Post by deadlieststewie on 2012-01-22
ok it looked like its only using 15 gigs of my 650 HD. is there a way i can get it to use all of it?

---

### Post by xyzzyman on 2012-01-22
It looks like you did a WUBI setup, is that correct?

---

### Post by deadlieststewie on 2012-01-23
i have no idea. i got it from using my windows, and put it on a DVDR to install it to this laptop

---

### Post by oldos2er on 2012-01-23
Since all your partitions are NTFS, you must have a Wubi installation. Wubi is limited to 30 GB.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by deadlieststewie on 2012-01-24
is there a way i can fix this? without losing what i have on here already?

---

### Post by xyzzyman on 2012-01-24
> **deadlieststewie said:**
> is there a way i can fix this? without losing what i have on here already?

Maybe you can offload some files to your windows partition. What size is your home? You can find this by running 'Disk Usage Analyzer' that's preinstalled. Just click 'Scan Home' and watch it count up.

Another thing to clean up space (If it doesn't error)

```
sudo apt-get install bleachbit
```

And run it normal and as root to clean up log & temp files... Although in the end you're most likely going to be backing up your data, repartitioning your system and installing Ubuntu by itself. The Wubi install you did is just a test environment so your options are limited.

---

### Post by bcbc on 2012-01-24
You can resize the wubi virtual disk as a short term solution: [http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)

You can migrate the wubi install to a normal dual boot: [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by deadlieststewie on 2012-01-24
i just remembered something. 

when i installed it, it gave me 3 choices, one was a demo and it said that in the demo i would have the option of downloading it in full in the demo. thats one option i picked since i didnt know exactly how i would like it. 

does anyone know how i would be able to download it in full from the use of the downloaded demo i have on it now?  pictured in the link below. scroll down a little.

[http://seogadget.co.uk/wp-content/uploads/2008/11/ubuntu_install1.gif](http://seogadget.co.uk/wp-content/uploads/2008/11/ubuntu_install1.gif)

---

### Post by xyzzyman on 2012-01-24
> **deadlieststewie said:**
> i just remembered something. 

when i installed it, it gave me 3 choices, one was a demo and it said that in the demo i would have the option of downloading it in full in the demo. thats one option i picked since i didnt know exactly how i would like it. 

does anyone know how i would be able to download it in full from the use of the downloaded demo i have on it now?  pictured in the link below. scroll down a little.

[http://seogadget.co.uk/wp-content/uploads/2008/11/ubuntu_install1.gif](http://seogadget.co.uk/wp-content/uploads/2008/11/ubuntu_install1.gif)

The second link the previous poster explains how to. Before doing anything back up your data on linux and windows.

---

### Post by deadlieststewie on 2012-01-24
what does it mean when it says migrate with swap or without swap?

---

### Post by bcbc on 2012-01-24
> **deadlieststewie said:**
> what does it mean when it says migrate with swap or without swap?

To migrate with [swap]("https://help.ubuntu.com/community/SwapFaq") means to migrate with a swap partition. The migration script will do some things behind the scenes to hook up the swap partition and also make sure you can hibernate to it (that's the other thing you can do with a swap partition - while technically possible with a swap file, it's not supported natively). 

Note that the swap partition must be greater than the size of your Ram to allow hibernation. I would recommend +1GB if your Ram is < 2GB or +.5GB if greater. e.g. 4GB Ram = 4.5GB swap partition size. There doesn't seem to be a definitive guide on exactly what the 'overflow' should be.

However, you don't have to have a swap partition. You can also use a swap file (like the Wubi install uses). 

So in short, when you migrate a wubi install, you need to create a single target ext4 partition (at a minimum). But it's a good idea to also create a swap partition at the same time. If you create an extended partition you can create both the target and swap as logical partitions within that.

---

### Post by deadlieststewie on 2012-01-24
it didnt work

bash: wubi-move-2.1.sh: No such file or directory

---

### Post by deadlieststewie on 2012-01-24
its saying that dev/sda5 does not exist

---

### Post by bcbc on 2012-01-24
The script doesn't create partitions. You can use gparted for that. You can also use Windows Vista/7 disk management console to shrink the C: partition (preferable if you have Vista/7).
That creates a space. Then you can use gparted to create an extended partition in that space and within that 2 logical partitions, one ext4 partition, and one swap partition.

When you're done creating the partitions, if you still need help you can post the output of:
```
sudo fdisk -l
```

PS since partitioning always has a small risk of data loss, you should backup beforehand. It's also a good idea to make sure you have a windows repair cd and restore disks.

PPS review this [http://ubuntu-with-wubi.blogspot.com/2011/05/how-to-migrate-in-pictures.html](http://ubuntu-with-wubi.blogspot.com/2011/05/how-to-migrate-in-pictures.html)

---

### Post by deadlieststewie on 2012-01-24
would it be easier if i said that i dont plan  on using windows on this computer anymore?

i plan on replacing windows on this system, since i have 2.

also i want to thank you all. you have been very helpful to me

---

### Post by bcbc on 2012-01-24
Okay, in that case you can review these: [http://askubuntu.com/questions/93954/how-do-i-get-rid-of-windows-during-wubi-migration](http://askubuntu.com/questions/93954/how-do-i-get-rid-of-windows-during-wubi-migration)
and
[http://askubuntu.com/questions/86327/migrating-wubi-to-a-real-partition](http://askubuntu.com/questions/86327/migrating-wubi-to-a-real-partition)
(both are basically the same but there's a little different info).

I'm going offline, but I'll check tomorrow if you have any other questions.

---

