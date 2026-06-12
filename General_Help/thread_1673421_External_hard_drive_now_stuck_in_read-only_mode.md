---
title: "External hard drive now stuck in read-only mode"
date: 2011-01-22
forum: General Help
---

### Post by gspawn69 on 2011-01-22
Ok, so here's my issue and what I think is causing it right now. I have a 1TB external usb hard drive that has worked perfectly, but recently I set it up a mount point for it in fstab so that I could create a SMB share on the drive so I could stream videos and pictures to my TV through my Wii using WiiMC. This now works perfectly, but now the hard drive has been set into read-only mode. When I use sudo to try to chmod the drive or the folders on it, it does nothing. When I right-click on the drive and check the permissions tab, it says the owner is root and all the options are greyed out.

I've read through several posts on similar topics to this, but none of them have been very helpful as they suggest using command line tools that I don't know how to use, so I'm hoping someone here can give me concise, step by step instructions of what to type in, or what settings to change in fstab to solve my little problem so I can start copying stuff back onto my drive. I'm running Ubuntu 10.10 and the filesystem on the external drive is FAT32. Here's some more info you might need:

sudo fdisk -l:
```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ab78f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112412672   83  Linux
/dev/sda2           13995       14594     4805633    5  Extended
/dev/sda5           13995       14594     4805632   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00075bda

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001    b  W95 FAT32

```

Contents of /etc/fstab:
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
/dev/sdb1 /media/media auto rw,auto,user
# swap was on /dev/sda5 during installation
UUID=950623b7-ab08-44eb-8476-d5eaf6e358bf none            swap    sw              0       0

```

If there's any more info you need, just let me know. Your help is greatly appreciated. :)

---

### Post by drewsus on 2011-01-22
While I am no fstab guru and I just got up after a long night of rock and roll bowling and late night inner city sledding (lol) I will give you a portion of my fstab for one of my internal NTFS drives: 
```
UUID=2E31CC297EDEA813 /media/DREW2000	ntfs	users,defaults,locale=en_CA.utf8,uid=1000,gid=46,umask=000	0	0
```

You will notice that I added it in by UUID instead of /dev/sd*#. This is so if you attach it differently it will still be added properly. 

You can list your drivers UUID's with this command: 
```
sudo blkid
```

You will also see that in fstab I put my user id (uid) and group id (gid). 
You would have to use "vfat" instead of "ntfs" as the type though and change the mount point of course. 
Network file sharing works fine on those drives for me. They work on my Wii and XBMC, etc.

[COLOR="RoyalBlue"]That being said, you wouldnt be using chmod to change it the way you want. You would want to use chown and chgrp first. 
So:
```
sudo chown -R 1000:1000 /media/media
```
Will change the media mount to be owned by you and your group. You could change "1000" to your user name, but if you are the only user on the system, then you should be good. From there you can change folder and file modes with chmod. But this blue section shouldnt be needed if you did what I mentioned above. Just giving you some info on that.[/COLOR]

---

### Post by gspawn69 on 2011-01-22
Ok, that's much more helpful. Just a quick follow up question though. How do I determine my UID and GID so that I can make the necessary changes in fstab?

---

### Post by drewsus on 2011-01-22
If you are the only user, you will be uid=1000 and gid=46 is the plugdev group for usb mounting I believe which you should be a member of, but you could probably just use gid=1000 as well. 

But, if you want to be sure, open terminal and issue this command to find your user id:
```
echo $UID
```
and for your group id:
```
echo $GROUPS
```

Again, you can just use it like I had in my example fstab entry just changing to the appropriate UUID for your USB drive and filesystem type (change **ntfs** to **vfat**). 
Give 'er a whirl anyway. 
Feel free to ask any other questions you have and mark this thread solved once you have solved it!

---

### Post by gspawn69 on 2011-01-22
Ok, got it to work finally. When I tried copy & pasting what from your fstab and restarted the computer, it wasn't recognizing the drive anymore. I modified it by replacing vfat with auto, and I removed the location and now it works fine. Here's what my fstab entry looks like now:

```

/dev/sdb1 /media/media auto users,defaults,uid=1000,gid=1000,umask=000	0	0

```

I haven't set it by UUID, but I haven't had any problems with it this way. If for some reason it decides to mount differently someday, I'll change it but for now it works fine, and my ability to copy files to the drive has now been restored. Thanks so much for your quick assistance. I am now marking this thread solved.

---

### Post by drewsus on 2011-01-22
The community has always helped me full out or pointing me in the right direction, so I am more than happy to peruse the forums and help where I can! Plus, many times I learn new things from helping others. 
Glad we got you sorted out!

---

