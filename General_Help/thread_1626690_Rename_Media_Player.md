---
title: "Rename Media Player"
date: 2010-11-20
forum: General Help
---

### Post by victor9098 on 2010-11-20
Hi All,

Been having some problems renaming a mp3 player. When I connect it to my computer it shows us like in the image I have attached below. I have tried to rename the media by going into its properties (no luck) and then tried to use gparted, but while I can select it, all the options are greyed out. 

Any help would be great, thank you!

---

### Post by ajgreeny on 2010-11-20
You may need to simply label the partition on the mediaplayer using gparted.

You will need to ensure the partition is unmounted, which you can do by right clicking on it, which is probably why you said the various controls were greyed out when you tried gparted earlier.

If you label the partition **Music_Player**, or whatever you want, it should mount under that name and will also be called that in the Places menu.

---

### Post by victor9098 on 2010-11-20
I open gparted and all the options are greyed out accept for the two you can see in the attachment below. I relabel USB keys all the time with gparted, but I have not seen this before.

The third image shows the properties of the device, I can not see anything out of place. I have 'mtools' installed and that should allow me to handle msdos devices :?:

Thanks for the reply, I appreciate the help

---

### Post by ajgreeny on 2010-11-20
There is no partition showing at all, that's why you can't do anything to it.  You can not label unallocated space, which is what you have showing.

What is the output of ```
sudo fdisk -l
``` with the player attached?

---

### Post by victor9098 on 2010-11-20
> **ajgreeny said:**
> There is no partition showing at all, that's why you can't do anything to it.  You can not label unallocated space, which is what you have showing.

What is the output of ```
sudo fdisk -l
``` with the player attached?

I have attached the output of fdisk for you! I can see the media player at the bottom at /dev/sdh, but I can not understand much more then that.

---

### Post by ajgreeny on 2010-11-21
That shows that there is an 8GB drive, but there are no partitions on it, I'm afraid, as seemed to be the situation in my last post.

Compare sdg:-

```
Disk /dev/sdg: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x74c4283a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1        4864    39070048+  83  Linux
```
with sdh:-
```
Disk /dev/sdh: 7916 MB, 7916748800 bytes
244 heads, 62 sectors/track, 1022 cylinders
Units = cylinders of 15128 * 512 = 7745536 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
```

The lack of the final line shows there is no partition on the disk.  Have you formatted it or deleted the partition that was there previously, and can you actually use the player for music at the moment?  Also do you have any backup of the firmware files or system files that may have been on the machine in the past?

---

### Post by victor9098 on 2010-11-21
As far as I am aware I have done nothing to it, I certainly have never formatted it. It has always worked fine, connects to banshee, syncs never a problem with it. I just would like to change the name that comes up on my desktop! In the 'computer' folder it does identify itself with its full name just fine (Sansa Fuze 8GB) but that is the only place it seems to do so.

There have been 2 firmware upgrades on the device which I have carried out via a windows machine. 

Just thought I was missing something simple, but obviously this is a much more complicated problem. Thank you for looking at the output and your help.

---

### Post by ajgreeny on 2010-11-21
Ah!  A sansa machine.

Does it connect as an MTP player or as a USB mass storage device?  I think there is a button or switch to turn it into a UMS device if it is MTP at the moment, but I can not remember properly.  Read through all your instruction info that came with the player.

---

### Post by victor9098 on 2010-11-21
I do not use the MTP setting, I know from reading how-to's they suggest to keep away from that setting for ease of use. So it has always been used with its MSC setting.

I have owned this for some 5 months now and have just got tired of the strange naming! Most tutorials suggest going into either the device properties or via gparted, but as you have seen both have been dead ends for me

---

### Post by ajgreeny on 2010-11-21
Sorry, but a dead-end for me as well.  With no partition to name, I have absolutely no idea where to go from here.

It must, of course, have a partition on it, but where is it?  I'm totally baffled!

---

### Post by Bradj47 on 2010-11-21
What I had to do to rename my Sansa was to reformat the entire device with a new name. I used gparted if I remember correctly.

---

### Post by victor9098 on 2010-11-21
> **ajgreeny said:**
> Sorry, but a dead-end for me as well.  With no partition to name, I have absolutely no idea where to go from here.

It must, of course, have a partition on it, but where is it?  I'm totally baffled!

Thanks a lot for everything, will leave the thread open, hopefully somebody might have an idea

---

### Post by victor9098 on 2010-11-21
> **Bradj47 said:**
> What I had to do to rename my Sansa was to reformat the entire device with a new name. I used gparted if I remember correctly.

Did you copy the files off your sansa and then format? What did you format it too and everything was fine after?

---

