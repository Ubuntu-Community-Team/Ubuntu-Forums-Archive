---
title: "Cannot mount MP3player/flash drive"
date: 2006-06-09
forum: General Help
---

### Post by justin2021 on 2006-06-09
When trying to open my CREATIVE MuVo TX FM flash drive, I get this error: 

Unable to mount the selected volume. The volume is probably in a format that cannot be mounted.

In Breezy it would pick it up instantly, but Dapper not so much. How would I be able to open it?

---

### Post by scxtt on 2006-06-09
have you tried something like:
```
sudo mount -t usbfs /dev/sda /media/CREATIVE
```which assumes the device is /dev/sda and the /media/CREATIVE directory exitsts ...

i was able to plug my LEXAR jumpdrive into dapper and have it automount ... same w/ my iRiver H300 jukebox ...

---

### Post by justin2021 on 2006-06-09
It says /media/CREATIVE does not exsist. How would I make one?

---

### Post by scxtt on 2006-06-09
sudo mkdir -p /media/CREATIVE

you don't have to use /media, but i think Ubuntu generally uses /media instead of /mnt - same difference tho ...

---

### Post by aysiu on 2006-06-09
When you have your MP3 player plugged in, can you post back the output of these two commands? ```
sudo fdisk -l
df -h
```

---

### Post by justin2021 on 2006-06-09
sudo fdisk -l gives me:


```
Disk /dev/hda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9824    78911248+  83  Linux
/dev/hda2            9825       10011     1502077+   5  Extended
/dev/hda5            9825       10011     1502046   82  Linux swap / Solaris

Disk /dev/sda: 255 MB, 255721472 bytes
8 heads, 61 sectors/track, 1023 cylinders
Units = cylinders of 488 * 512 = 249856 bytes

   Device Boot      Start         End      Blocks   Id  System
```

and df -h gives me:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              75G  2.3G   69G   4% /
varrun                252M   80K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
udev                  252M  108K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   19M  234M   8% /lib/modules/2.6.15-23-386/volatile
/dev/hdc              5.4G  5.4G     0 100% /media/cdrom-1

```

And scxtt, I tried what you said but it give me the following errors when trying to open the device:

error: device /dev/sda is already mounted to /media/creative

error: could not execute pmount

---

### Post by aysiu on 2006-06-09
Okay. That's weird. Do you see how there's no partition information about /dev/sda?

When I do *sudo fdisk -l* with my USB thumb drive in, I get this: ```
Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1911    15350076    7  HPFS/NTFS
/dev/hda2            1912       19457   140938245    5  Extended
/dev/hda5            1912       18174   130632516   83  Linux
/dev/hda6           18175       18295      971901   82  Linux swap / Solaris
/dev/hda7           18296       19457     9333733+  83  Linux

Disk /dev/sde: 512 MB, 512483328 bytes
255 heads, 63 sectors/track, 62 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
**/dev/sde1               1          62      497983+   b  W95 FAT32**
``` I have a line at the bottom that you're missing. It should be something like /dev/sda1 and type FAT32 or FAT16. There's no filesystem type.

Do you have important data on that drive already, or can you just reformat it?

---

### Post by scxtt on 2006-06-09
> And scxtt, I tried what you said but it give me the following errors when trying to open the device:

error: device /dev/sda is already mounted to /media/creative

error: could not execute pmountlooking at that it seems like once you plug it in, it's automounted and just waiting for you to do something with it ...

have you tried doing "ls -l /media/creative" and seeing if you see files on the drive?  and i get results similar to aysiu when i execute those command w/ my Lexar plugged in (/dev/sdc1 is the Lexar) ...```
$:> fdisk -l

Disk /dev/sdc: 259 MB, 259522560 bytes
65 heads, 32 sectors/track, 243 cylinders
Units = cylinders of 2080 * 512 = 1064960 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         244      253424    4  FAT16 <32M
Partition 1 has different physical/logical endings:
     phys=(249, 64, 32) logical=(243, 44, 32)
```

---

### Post by justin2021 on 2006-06-09
Well, when I typed ls -l /media/CREATIVE, I got a total of 0 so... i guess there is nothing on there now. There used to be a bunch of songs, but I have all of them saved on another computer anyway. So i guess I wouldnt care if it was reformated.

[edit] I may have found out what I have to do. I may have to assign a filesystem to it. The only thing is, i dont know how

---

### Post by scxtt on 2006-06-10
if you've put gparted on your install, you can use it to easily format the device ... you can easily install it via synaptic if it isn't installed ...

note that you'll need to make sure the device isn't mounted in order to format it ...

---

### Post by justin2021 on 2006-06-10
Thanks for the help, I finally got it working. I made it a FAT32 partition, so it could be read by both Windows and Linux.

---

### Post by sinaen on 2006-08-29
my problem is that i need to format my mp3player thats an usb-memory. to plug in. to get the /dev/sda1 device to be seen. when i plug it in and see it it only comes up /dev/sda and /dev/sg0 and when i format it /dev/sg0 is replaced with /dev/sda1..

weird every time. i can se the things in gparted and the storage consumption. but not until i format it there it is seen, and can be mounted. the filesystem it runs is fat16. 
in windows it pop-ups like an nagging old hag. why is it working in windows but not in linux?

---

