---
title: "Can't Mount External Drive"
date: 2009-11-03
forum: General Help
---

### Post by SammichDinosaur on 2009-11-03
I'm having trouble mounting my external drive (NTFS). When I plug it in I receive the following message (Screen1.png): 
[INDENT]
"Error mounting: mount exited with exit code 1: helper failed with: mount: only root can mount /dev/sdb1 on /media/sdb1"[/INDENT]

I tried changing a few things with Storage Device Manager (pysd I believe), which only resulted in the following (Screen2.png):

[INDENT]"Error mounting: mount exited with code 1: helper failed with: Unprivileged user can not mount NTFS block devices using the external FUSE library. Either mount the volume as root, or rebuild NTFS-3G with integrated FUSE support and make it setuid root. Please see more information at http://ntfs-3g.org/support.html#unprivileged"[/INDENT]

I visited the link...but couldn't follow what I was to do.

Help?

---

### Post by SammichDinosaur on 2009-11-03
So I was able to mount the drive using sudo mount /dev/sbd1

And was told that I need to edit fstab...but am not sure exactly what I need to do after reading man fstab.

---

### Post by SammichDinosaur on 2009-11-03
Here is what fstab looks like right now:

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                 0  0  
# / was on /dev/sda5 during installation
UUID=b52c2dff-af33-4730-83ca-8f33c99f383d  /              ext4         errors=remount-ro        0  1  
# swap was on /dev/sda6 during installation
UUID=8d704d86-c225-45bb-b9f3-39992e8aa33a  none           swap         sw                       0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8    0  0  
/dev/sdb1                                  /media/sdb1    ntfs         defaults                 0  0  
/dev/sda7                                  /media/sda7    ntfs         nls=iso8859-1,umask=000  0  0  

---

### Post by SammichDinosaur on 2009-11-04
So restarted. Plugged in external drive. Auto-mounted. Have read/write access. But still popped up the dialog from Screen1.png. And I can't unmount it.

---

### Post by Crafty Kisses on 2009-11-04
Do you have ntfs-3g installed?

---

### Post by SammichDinosaur on 2009-11-04
Yes, I believe so

---

### Post by SammichDinosaur on 2009-11-04
If I have the drive plugged in on startup it appears to mount fine.

---

### Post by Crafty Kisses on 2009-11-06
While the external drive is plugged in, run the following command:
```
fdisk -lu
```
Post the results back here.

---

### Post by albannach1 on 2009-11-06
I got the same error while trying to mount a NTFS partition on my HD. Editing the fstab and adding a folder to mount the drive to in /media worked for me. I don't know how it would work with an external drive but here is the link that explained fstab to me.
[http://www.tuxfiles.org/linuxhelp/fstab.html]("http://www.tuxfiles.org/linuxhelp/fstab.html")

---

### Post by SammichDinosaur on 2009-11-08
> **Crafty Kisses said:**
> While the external drive is plugged in, run the following command:
```
fdisk -lu
```
Post the results back here.


No output. Perhaps I'm doing it wrong?

---

### Post by conradin on 2009-11-08
when using fdisk you must specify a device
```

fdisk -l -u /dev/sda

```

I just used /dev/sda as an example if you want to find out more about your 
specific filesystems try:
```

ls /dev/sd*

```

---

### Post by conradin on 2009-11-08
Boy Do i feel Dumb.
you have to run fdisk as root
 try:
```

sudo fdisk -lu

```

---

### Post by conradin on 2009-11-08
try:
```

sudo fdisk -lu

```

---

### Post by SammichDinosaur on 2009-11-08
ok sudo fdisk -lu output:

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbed4bed4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    62974799    31487368+   7  HPFS/NTFS
/dev/sda2        62974800   488375999   212700600    f  W95 Ext'd (LBA)
/dev/sda5        62974863   117676124    27350631   83  Linux
/dev/sda6       117676188   125853209     4088511   82  Linux swap / Solaris
/dev/sda7       125853273   488375999   181261363+   7  HPFS/NTFS

Disk /dev/mmcblk0: 2032 MB, 2032664576 bytes
64 heads, 63 sectors/track, 984 cylinders, total 3970048 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1             249     3967487     1983619+   6  FAT16

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe8900690

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63  1953520064   976760001    7  HPFS/NTFS

---

### Post by conradin on 2009-11-08
Ok, I'm not certain, but it looks like /dev/sdb1 is the volume you want to mount.  

try:
```

sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1

```
then try to access the data with:
```
 
sudo nautilus /media/sdb1

```

---

### Post by SammichDinosaur on 2009-11-11
It mounts fine. I plug it in, it pops up the error message, but then proceeds to mount and I have read/write access. 

Unmounting produces an error message as well. For example yesterday, I used the usb drive, tried to unmount, received error message, unplugged anyways. The icon for the usb drive remains. Later I tried to use a flash drive. Mounting it was impossible because it thought the flash drive was /dev/sdb1. Or something.

---

### Post by DigitaLink on 2009-11-29
I was getting the message too.  I set fstab to mount my USB drive to /media/Storage.  I created the dir as root ... did a chown to my user, rebooted, error was gone.  Worked for me at least.  Might be the same issue for you.

---

### Post by ikiryo on 2010-02-22
I had the very same problem as well and the chown didn't help me out. 

You should also check the file structure. I had entered vfat into fstab, but it turned out to be a ntfs! After I changed that, the mount -a worked like a charm!

---

### Post by cmcanulty on 2010-05-08
Can poster #17 please give a beginners instruction to do as you suggested. I have had no luck understanding fstab

---

### Post by tg3793 on 2011-01-28
> **cmcanulty said:**
> Can poster #17 please give a beginners instruction to do as you suggested. I have had no luck understanding fstab

Hello cmcanulty . I know that this thread is about five years old but since I ran across it I figured that others could benefit from the answer if you ever found one.

I too am having this problem, incidentally also with sdb1; though I'm working with Lucid 10.04

It sounds like I might end up playing with FSTAB soon. I found a great set of [instructions on it here]("http://www.tuxfiles.org/linuxhelp/fstab.html"). I'll look at that after I work on another unrelated issue I'm having.

---

### Post by doctor82 on 2011-03-30
I had the same problem and landed upon this page. The following is what worked for me.

First see [http://maketecheasier.com/auto-mount-your-ntfs-partition-in-ubuntu/2009/04/14](http://maketecheasier.com/auto-mount-your-ntfs-partition-in-ubuntu/2009/04/14) to install and use pysdm.

Plug in your usb / external drive

Once installed, go to System -> Administration -> Storage Device Manager.

Once you have located sdb -> sdb1 partition, click on the Assistant button.
Choose the first option which says "allow any user to mount the file system"
 
But I had to use the terminal and type sudo nautilus to copy files into the mounted drive.

---

### Post by BryanFRitt on 2012-06-05
#I figured this out some time ago(Sorry, if this no longer applies, I didn't retest/memory fades, etc...), and I think it went like this:

#For external USB NTFS drives to automatically mount on attachment the mount directory needs to NOT exist, and the drive NOT to listed in /etc/fstab, but...
#to mount it automatically at boot it needs to be in /etc/fstab AND the mount directory needs to exist. 
#NOTE: These are Opposite Requirements! Take which one you prefer: Mounted at plugin, or Mounted at boot.
#((NOT A) AND (NOT B) for mounted at plugin) OR (A AND B for mount at boot)

---

### Post by sffvba[e0rt on 2012-06-06
*Old thread **closed**.*


404

---

