---
title: "Automount HDs on Startup"
date: 2009-10-21
forum: General Help
---

### Post by joeyknuccione on 2009-10-21
Here's the deal, I have all my pictures on a separate hard drive, and so wallpaper-tray returns errors on startup because the drive is not mounted on startup (I guess).

So, I tried the mount utility in gnome (9.04 Jaunty updated to today), to no avail, I tried mountmanger (one word) and it returns errors, so then I tried pysdm and it won't auto mount my extra hard drives, one of which is a fat32.

Question:

Is there a...

FUNCTIONING

...application that will auto mount disks at startup?

I've tried the manual way of editing fstab and I admit my own dooficity prevents me from understanding how to do this.

---

### Post by joeyknuccione on 2009-10-21
Anybody? I can't even write to my fat32 now.

---

### Post by uncle-c on 2009-10-22
Can you show the output of :
```
 $ sudo fdisk -l 
```

This will list all your hard drives and their respective partitions. Once we know which partitions need mounting and to which filesystem they are formatted, the automount via /etc/fstab should be straightforward.

---

### Post by swerdna on 2009-10-22
If you want a fat32 drive to mount at startup, put a line defining the mount in the file fstab (located at /etc/fstab). Here's an example of syntax: ```
UUID=AD74-85CA     /path_to/mount_point     vfat     umask=0000,utf8     0 0
```
For further info: [HowTo Mount a Fat32 / Vfat Partition Read Write in Ubuntu & Kubuntu]("http://ubuntu.devel.org/ubufat32.html")

and just in case, for NTFS it's like this: ```
UUID=F028603828600048     /path_to/mount_point     ntfs-3g     defaults     0 0
```

FFI on NTFS: [HowTo Mount NTFS Partitions Read Write in Ubuntu & Kubuntu]("http://ubuntu.devel.org/ubuntfs.html")

---

### Post by bashphoenux on 2009-10-22
download pysdm !!! 
type
sudo apt-get install pysdm

and run pysdm as root
type:
su -c'pysdm'
a window will be prompted with all the partitions click on each partition,on the right side you should be able to see mount button click on it.. repeat the process for all partitions and VOILA ... your partitions are mounted for life !!! you have you unmount using pysdm only(if you want or editing fstab file)

---

### Post by alphaniner on 2009-10-22
If you want to have another go at learning fstab I recommend [How to fstab]("http://ubuntuforums.org/showthread.php?t=283131") right here on the Ubuntu forums.

---

### Post by joeyknuccione on 2009-10-22
I 'preciate the help y'all.

su -c'psydm' returns:

Authentication failure (I know my password :) )

So, then I try the /etc/fstab, and I have for vfat:

UUID=5D81-589E /media/disk vfat group, users, user 0 0


EDIT IN:

sudo fdisk -l returns:

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x73115db9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       10011    80413326    b  W95 FAT32

---

### Post by Zoot7 on 2009-10-22
Just to add, after you've edited fstab. Do this to test it.
```
sudo mount -a 
```
That'll mount all partitions, so you can check if your fat32 partition gets mounted. Saves you having to reboot. ;)

---

### Post by bashphoenux on 2009-10-22
> **joeyknuccione said:**
> I 'preciate the help y'all.

su -c'psydm' returns:

Authentication failure (I know my password :) )


i am guessing you entered your sudo password !!!
did you even create a password for su ???
if not do this
```

$:sudo -i //enter your sudo password
then type 
$:su
then type
$:passwd
it will prompt you to enter your new unix passsword !!! 
```the password that you entered will serve as your 'SU' password !! 
now re do the steps i posted previously
let me know if you are still facing any problems ?


screenshot of how it will look !!

---

### Post by tomapio on 2010-01-07
I had the same problem, but i found [this tutorial]("http://ubuntuforums.org/showthread.php?t=872197"). The guy uses a GUI application called PYsdm.



The basic steps are:


-Download and install pysdm


sudo apt-get install pysdm


-Open  System -> Administration -> Storage Device Manager


-Navigate to the partition you want to automount at startup
(in my case "sda4")


-If you're trying to mount a fat32 or ntfs partition, in the "options" textbox paste the following:



auto,users,uid=1000,gid=1000,utf8,dmask=027,fmask=137



-Click "Assistant" and UNCHECK "Mount file system in read mode only" -> click OK


-Apply the changes


-Unmount


-Mount


-Close the Storage Device Manager






That worked like a charm for me.
Good luck ;)

---

