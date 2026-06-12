---
title: "Unable to mount anything via USB"
date: 2011-03-25
forum: General Help
---

### Post by DaveS4 on 2011-03-25
[B]So first of all, I'm very new so, sorry in advance for my general lack of know-how. Especially regarding the terminal. 

So a week or so ago, I found that I was unable to mount my external hard drive. I did some research and was able to do it manually (Sudo mount ......). 
But just recently, I decided to get my iPod going with my new operating system. It won't auto-mount and after researching all day, I can't figure out how to do it manually. 
And I'd like to address the real problem here and find out why nothing is auto-mounting. 

When I run sudo fdisk -l ......[/B]

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005e2e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37528   301442048   83  Linux
/dev/sda2           37529       38914    11126785    5  Extended
/dev/sda5           37529       38914    11126784   82  Linux swap / Solaris
Note: sector size is 4096 (not 512)

Disk /dev/sdb: 159.8 GB, 159840301056 bytes
26 heads, 50 sectors/track, 30018 cylinders
Units = cylinders of 1300 * 4096 = 5324800 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30019   156093788    b  W95 FAT32
Partition 1 does not start on physical sector boundary.



**And when I run dmesg | tail .......**

[ 1574.012501] sd 7:0:0:0: [sdb] Mode Sense: 68 00 00 08
[ 1574.012507] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 1574.014378] sd 7:0:0:0: [sdb] 39023511 4096-byte logical blocks: (159 GB/148 GiB)
[ 1574.015499] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 1574.015505]  sdb: sdb1
[ 1574.048234] sd 7:0:0:0: [sdb] 39023511 4096-byte logical blocks: (159 GB/148 GiB)
[ 1574.049487] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 1574.049491] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[ 1623.271610] FAT: count of clusters too big (9755749)
[ 1623.271614] VFS: Can't find a valid FAT filesystem on dev sdb.


**I don't really know what all of this means, or how to address the problem. So could someone get me started? Thanks.**

-Dave

---

### Post by lmarmisa on 2011-03-25
Welcome to the forums.

It seems that the FAT filesystem of your external HDD has some errors. I recommend to repair that partition. Please, open a terminal and type this command:

```

sudo fsck.vfat /dev/sdb1

```

The previous command must be typed with the FAT partition unmounted. You say that you are unable to mount it. So, apparently there is no problem about that. Anyway, you could verify that the /dev/sdb1 partition is not mounted typing the command:

```

mount

```

You have detected some problems trying to mount other devices. Try to post the output of this other command:

```

ls -l /media

```

---

### Post by wojox on 2011-03-25
Have you formatted the iPod with Windows? Have you installed GTKPod?

When you mount anything does it show up on the left side of Nautilus?

---

### Post by DaveS4 on 2011-03-26
> **wojox said:**
> Have you formatted the iPod with Windows? Have you installed GTKPod?

When you mount anything does it show up on the left side of Nautilus?

I used to have windows yes. I made the switch to ubuntu just recently, and this is the first time I've tried using my iPod with it. 
I have installed GTKPod. It doesn't recognize anything. 
And Nautilus doesn't add an icon for my iPod or my external drive.... that's the problem. Nothing mounts automatically. 

-Dave

---

### Post by DaveS4 on 2011-03-26
> **lmarmisa said:**
> Welcome to the forums.

It seems that the FAT filesystem of your external HDD has some errors. I recommend to repair that partition. Please, open a terminal and type this command:

```

sudo fsck.vfat /dev/sdb1

```

The previous command must be typed with the FAT partition unmounted. You say that you are unable to mount it. So, apparently there is no problem about that. Anyway, you could verify that the /dev/sdb1 partition is not mounted typing the command:

```

mount

```

You have detected some problems trying to mount other devices. Try to post the output of this other command:

```

ls -l /media

```


So is this the solution? I don't understand it all, but I can figure it out if this is the way to go. 

-Dave

---

### Post by GenericBox on 2011-03-26
Hi, 

I am also fairly newb when it comes to Ubuntu, and I have been having the same problem. I have asked all over IRC and no one is answering me. I don't believe it is anything to do with the solutions / checks people have posted so far. 

My similar issues arose from a recent update (as far as I can tell). I can neither open "Computer" "Network" or "Trash" from the Places menu, receiving the following error:

[Could not display "computer:".] Nautilus cannot handle "computer" locations.

I think the problems are related. Could you click on these items from your Places menu and tell me if you have the same issue as me?

Thanks.
GB.

---

### Post by lmarmisa on 2011-03-26
Sorry. Maybe my post was a bit messy.

I suppose the outputs of the commands **sudo fdisk -l** and **dmesg | tail** belong to the case of your external hard drive (not to the case of iPod). I see a 159.8 Gbytes hard drive containing one FAT32 partition. That partition has some errors and you should try to fix them. How?.

Plug the external hard drive, type the command

```

mount

```

and check that the partition **/dev/sdb1** is not mounted.

When you verify this partition is not mounted, type this other command for repairing the damaged FAT32 partition:

```

sudo fsck.vfat /dev/sdb1

```

I suppose that procedure will fix your external hard drive.

Now, another issue. You have problems with iPod and you ask why nothing is automounting. I would like to know the contents of your **/media** folder. Sometimes there are some rubbish folders there and this is the cause that the devices cannot mount properly.

Please, post the output of the command:

```

ls -l /media

```

---

### Post by DaveS4 on 2011-03-26
> **lmarmisa said:**
> Sorry. Maybe my post was a bit messy.

I suppose the outputs of the commands **sudo fdisk -l** and **dmesg | tail** belong to the case of your external hard drive (not to the case of iPod). I see a 159.8 Gbytes hard drive containing one FAT32 partition. That partition has some errors and you should try to fix them. How?.

Plug the external hard drive, type the command

```

mount

```

and check that the partition **/dev/sdb1** is not mounted.

When you verify this partition is not mounted, type this other command for repairing the damaged FAT32 partition:

```

sudo fsck.vfat /dev/sdb1

```

I suppose that procedure will fix your external hard drive.

Now, another issue. You have problems with iPod and you ask why nothing is automounting. I would like to know the contents of your **/media** folder. Sometimes there are some rubbish folders there and this is the cause that the devices cannot mount properly.

Please, post the output of the command:

```

ls -l /media

```


Thank you. 
I believe that the 159.8 GB hard drive with errors *IS* my iPod. Am I going to have to erase/reformat it??


And secondly, When I get the contents of /media, I get....
"ipod
IPOD
passport"

Now I know that I created two of those entries. One when I successfully mounted my external HD (passport) and another when I unsuccessfully tried to mount my ipod (ipod). 

Thanks

---

### Post by DaveS4 on 2011-03-26
> **GenericBox said:**
> Hi, 

I am also fairly newb when it comes to Ubuntu, and I have been having the same problem. I have asked all over IRC and no one is answering me. I don't believe it is anything to do with the solutions / checks people have posted so far. 

My similar issues arose from a recent update (as far as I can tell). I can neither open "Computer" "Network" or "Trash" from the Places menu, receiving the following error:

[Could not display "computer:".] Nautilus cannot handle "computer" locations.

I think the problems are related. Could you click on these items from your Places menu and tell me if you have the same issue as me?

Thanks.
GB.

Nope. My nautilus is able to go to those places.

---

### Post by GenericBox on 2011-03-26
Np, my issue is solved. But thanks for confirming. Good luck with yours :)

---

### Post by lmarmisa on 2011-03-27
> **DaveS4 said:**
> Thank you. 
I believe that the 159.8 GB hard drive with errors *IS* my iPod. Am I going to have to erase/reformat it??


And secondly, When I get the contents of /media, I get....
"ipod
IPOD
passport"

Now I know that I created two of those entries. One when I successfully mounted my external HD (passport) and another when I unsuccessfully tried to mount my ipod (ipod). 

Thanks

My son has a 30 Gbytes iPod. Sorry. I did not know that other models have such a big hdd (160 Gbytes!).

My son has lent me his iPod for a few tests. The device is perfectly mounted here just like any other external USB device.

I attach a couple of captures of the folder **/media**. No folder exists here when no external device is connected and one folder is created after the iPod is mounted automatically. I have removed safely the iPod and the folder was automatically removed. This is the normal behaviour.

I think you have two problems:

1) You get some folders in the folder** /media** with no external devices connected. This is wrong. You should try to remove them. You could use this command (please,** _no external devices connected!!!!_**):

```

sudo rm -f /media/*

```2) The FAT32 partition of your iPod has some errors. You should fix those errors. I am not an expert on iPod. Maybe the command I proposed in a previous post could be useful.

---

### Post by DaveS4 on 2011-03-28
> **lmarmisa said:**
> My son has a 30 Gbytes iPod. Sorry. I did not know that other models have such a big hdd (160 Gbytes!).

My son has lent me his iPod for a few tests. The device is perfectly mounted here just like any other external USB device.

I attach a couple of captures of the folder **/media**. No folder exists here when no external device is connected and one folder is created after the iPod is mounted automatically. I have removed safely the iPod and the folder was automatically removed. This is the normal behaviour.

I think you have two problems:

1) You get some folders in the folder** /media** with no external devices connected. This is wrong. You should try to remove them. You could use this command (please,** _no external devices connected!!!!_**):

```

sudo rm -f /media/*

```2) The FAT32 partition of your iPod has some errors. You should fix those errors. I am not an expert on iPod. Maybe the command I proposed in a previous post could be useful.


Thanks for the continued help. 
So after some trial and error, I was able to clear my media folder. I plugged the iPod in just now, and it still doesn't work. Neither Gtkpod nor Banshee are able to detect an iPod, and nautilus doesn't see anything new either...

I don't understand the "command you proposed in a previous post". What command?..... And don't worry about not understanding iPods. The problem is universal - I can plug in any external hard drive, ipod, or flash drive, and my computer won't recognize them at all. 
But like I said, I was able to manually mount my passport and transfer files. So it's not like the USB connection is dead or anything. It just doesn't auto-mount. 

Any thoughts or questions?
Thanks
-Dave

---

### Post by DaveS4 on 2011-03-29
Just to confirm... when I type in
```

ls -l /media

```

... I get

> total 0

Thanks again

---

### Post by lmarmisa on 2011-03-29
Your folder **/media** is cleared now. I think this was your first problem but I would like to verify that issue.

Forget your iPod at the moment.

Try to check if other external USB devices different to your iPod are automounted **now, after you have cleared the folder /media.** Check if your external hard drive or an external flash drive are automatically mounted by Ubuntu.

We will drive the iPod problem later.

Best regards,

Luis

---

### Post by DaveS4 on 2011-03-29
Ok, 
So I checked my passport external hard drive, and it did not mount. I was not able to see or access it. 
However, it is worth noting that I screwed around with the passport on another computer a few weeks ago to disable some auto-run software that comes on all WD Passports. The auto-run software was not compatible with linux, so I had to disable it in order to be able to use the HD. So that may be the problem with that. 

I also checked a USB flash drive and it DID auto-mount. I was able to see it in nautilus and access it. 

-Dave

---

