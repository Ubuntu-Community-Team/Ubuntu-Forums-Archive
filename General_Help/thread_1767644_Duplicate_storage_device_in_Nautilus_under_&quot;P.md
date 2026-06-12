---
title: "Duplicate storage device in Nautilus under &quot;Places&quot;"
date: 2011-05-26
forum: General Help
---

### Post by RaskloP on 2011-05-26
I had troubles with my NTFS external hdd mounting without becoming root until I changed my fstab file.

However after changing my fstab file I created an error in the place of the one I had fixed. Now since the change I have two entries of my external hard drive in Places.

I'd like to know how to remove the duplicate entry.

Provided is my current fstab and screenshot of duplicate:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sda1 :
UUID=219f23c6-9079-4297-a7b3-ee41a264780b    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sdb1 :
UUID=486E622C6E62134C /media/Beast ntfs-3g auto,users,uid=1000,gid=100,utf8,dmask=027,fmask=137 0 0
#Entry for /dev/sda5 :
UUID=064020c3-cf2f-4ba5-b0b6-49667fee4f27    none    swap    sw    0    0
```[IMG]http://i.imgur.com/ktPmT.png[/IMG]

Thanks for being of help! :D

---

### Post by RaskloP on 2011-05-26
I realize the fix is probably something stupefyingly easy although some sort of guidance would be great. :popcorn:

---

### Post by RaskloP on 2011-05-27
Anyone with some knowledge want to add their input?

---

### Post by nightfever on 2011-07-31
I'm having the same problem.
No help?

---

### Post by Habitual on 2011-07-31
If you unmount graphically right click "Safely Remove Drive", what happens in Nautilus?
Do both disappear?

In terminal 
sudo ```
mount -a
```
what happens in Nautilus?

Terminal > 
```
sudo blkid
``` says what about the drive/device/volume?

---

### Post by hantms on 2012-02-05
I'm having this exact same problem too; using 12.04

---

### Post by aasdfasdfg on 2012-02-05
> **RaskloP said:**
> I had troubles with my NTFS external hdd mounting without becoming root until I changed my fstab file.

However after changing my fstab file I created an error in the place of the one I had fixed. Now since the change I have two entries of my external hard drive in Places.

I'd like to know how to remove the duplicate entry.

Provided is my current fstab and screenshot of duplicate:


Interesting. Some areas to explore:

[LIST]
[*]How many partitions and what are their labels on the drive containing the /media/Beast partition?
[*]What are the contents of the /media directory?
[*]Try replacing /media/Beast with none in your fstab; if the drive label is Beast, nautilus should mount it to that directory anyway
[/LIST]

---

### Post by dcstar on 2012-02-06
> **aasdfasdfg said:**
> Interesting. Some areas to explore:

[LIST]
[*]How many partitions and what are their labels on the drive containing the /media/Beast partition?
[*]What are the contents of the /media directory?
[*]Try replacing /media/Beast with none in your fstab; if the drive label is Beast, nautilus should mount it to that directory anyway
[/LIST]

People should **never, ever** use **/media** to mount things. **/media is a system folder** for the system to use and manage, not users.

Use /mnt - or whatever - to mount things, **never use system folders**.

---

### Post by Sepero on 2012-03-01
I was able to solve this problem on my system by starting nautilus as root user, and then unmount/remount the filesystems. Make sure you have no files open on the filesystem.

sudo nautilus

---

### Post by savebart on 2012-05-14
I solved the problem by substituting "UUID=..." with "/dev/disk/by-uuid/...", according to the following thread in Launchpad: [https://bugs.launchpad.net/ubuntu/+s...fs/+bug/442130](https://bugs.launchpad.net/ubuntu/+s...fs/+bug/442130)

But I still have to understand if it caused some freeze problem at logout...

---

### Post by savebart on 2012-05-14
... I forgot to give the link to the related thread in launchpad: [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/442130](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/442130)

---

