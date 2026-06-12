---
title: "FStab kicking my behind"
date: 2010-02-22
forum: General Help
---

### Post by Mahngiel on 2010-02-22
This was built following this guides:
bohdi.zazen's [HowTo FStab]("http://ubuntuforums.org/showthread.php?&t=283131")
Ubuntu's [How To Mount at Boot]("https://help.ubuntu.com/community/AutomaticallyMountPartitions")


```
# <file system>                 <mount point>       <type>      <options>               <dump>  <pass>
proc                            /proc                  proc        defaults                     0       0
/dev/scd0                       /media/cdrom0               udf,iso9660 user,noauto,exec,utf8 0       0
[COLOR=Silver]# Windows 7 Restore (/dev/sda1)[/COLOR]
UUID=98F0252BF02510D4                /mnt/Win7Restore    ntfs        noauto,ro              0      2
[COLOR=Silver]# Windows 7 (/dev/sda2)[/COLOR]
UUID=78E69E4CE69E0B10                /media/Se7en        ntfs-3g        auto,users,rw,uid=1000,gid=100,utf8,dmask=027,fmask=1 37 0 0
[COLOR=Silver]# Storage (/dev/sda3) [/COLOR]
UUID=AC6A824F6A82166C                /media/Storage        ntfs-3g        auto,users,rw,uid=1000,gid=100,utf8,dmask=027,fmask=1 37 0 0
[COLOR=Silver]# Backup (/dev/sda5)[/COLOR]
UUID=367D666E79DBCBE4                /mnt/Backup        ntfs-3g        auto,users,rw,uid=1000,gid=100,utf8,dmask=027,fmask=1 37 0 0
[COLOR=Silver]# Swap (/dev/sda6)[/COLOR]
UUID=3daf19c0-397b-41c8-acba-9c18444bb4a1    none                swap        sw                          0       0
[COLOR=Silver]# Boot Partition (/dev/sda7)[/COLOR]
UUID=967540d4-7ef8-45bd-a3c7-407f613a4fe4    /mnt/Boot        ext4        auto,users,rw             0     0
[COLOR=Silver]# Kubuntu (/dev/sda8)[/COLOR]
UUID=8428dd04-2e96-46cf-8f8a-5f078cfbd1df    /media/Kubuntu        ext4        auto,users,rw             0     0
[COLOR=Silver]# Ubuntu Studio Root (/dev/sda9) [/COLOR]       
UUID=6076410e-248d-4736-8c5b-d2f827eff785     /                   ext4           errors=remount-ro           0       1
[COLOR=Silver]# Tota Linux (/dev/sda10)[/COLOR]
UUID=742cf805-dd80-4e42-80c9-1b0b108a65be    /media/Tota        ignore        auto,users,rw             0     0
```
```
mahngiel@studio:~$ ls /dev/disk/by-uuid -alh
total 0
drwxr-xr-x 2 root root 240 2010-02-22 14:05 .
drwxr-xr-x 6 root root 120 2010-02-22 09:05 ..
lrwxrwxrwx 1 root root  10 2010-02-22 09:05 367D666E79DBCBE4 -> ../../sda5 [COLOR=RoyalBlue]Backup[/COLOR]
lrwxrwxrwx 1 root root  10 2010-02-22 09:05 3daf19c0-397b-41c8-acba-9c18444bb4a1 -> ../../sda6 [COLOR=RoyalBlue]swap[/COLOR]
lrwxrwxrwx 1 root root  10 2010-02-22 09:05 6076410e-248d-4736-8c5b-d2f827eff785 -> ../../sda9 [COLOR=RoyalBlue]Ubuntu Studio[/COLOR]
lrwxrwxrwx 1 root root  11 2010-02-22 09:05 742cf805-dd80-4e42-80c9-1b0b108a65be -> ../../sda10 [COLOR=RoyalBlue]Tota[/COLOR]
lrwxrwxrwx 1 root root  10 2010-02-22 09:05 78E69E4CE69E0B10 -> ../../sda2 [COLOR=RoyalBlue]Win7[/COLOR]
lrwxrwxrwx 1 root root  10 2010-02-22 09:05 8428dd04-2e96-46cf-8f8a-5f078cfbd1df -> ../../sda8 [COLOR=RoyalBlue]Kubuntu[/COLOR]
lrwxrwxrwx 1 root root  10 2010-02-22 09:05 967540d4-7ef8-45bd-a3c7-407f613a4fe4 -> ../../sda7 [COLOR=RoyalBlue]Boot[/COLOR]
lrwxrwxrwx 1 root root  10 2010-02-22 09:05 98F0252BF02510D4 -> ../../sda1 [COLOR=RoyalBlue]Win7Restore[/COLOR]
lrwxrwxrwx 1 root root  10 2010-02-22 09:05 AC6A824F6A82166C -> ../../sda3 [COLOR=RoyalBlue]Storage[/COLOR]


``````
mahngiel@studio:~$ ls /media/
[COLOR=RoyalBlue]cdrom  cdrom0  Kubuntu  Reeck  Se7en  Storage  Tota[/COLOR]
mahngiel@studio:~$ ls /mnt/
[COLOR=RoyalBlue]Backup  Boot  Win7Restore[/COLOR]

```> Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
[http://ntfs-3g.org/support.html#unprivileged](http://ntfs-3g.org/support.html#unprivileged)I would like everything mounted at boot, and the several accessible through Places.
Problem is, nothing automounts, and it creates multiple entries in Places, and Two of my FS's won't even mount. [see attachment]


Any help is appreciate.

---

### Post by bodhi.zazen on 2010-02-22
The partitions should auto mount, do you have errors in your logs ?

What happens when you run

```
sudo mount -a
```

You can look at the discussion in this thread fr: FAT / NTFS partitions.

[http://ubuntuforums.org/showthread.php?t=1409347](http://ubuntuforums.org/showthread.php?t=1409347)

---

### Post by wojox on 2010-02-22
What's 

```
sudo fdisk -l
```

Say?

---

### Post by Mahngiel on 2010-02-22
sudo mount -a works.

I'm still left with two versions of the disk, the ones with without the 500GB HD designation produce the errors I reported earlier - see two attachments.  Though I understand what it cannot dually mount a partition, why do i have 2 versions?  Is it due to the amount of partitions it's managing? I've never had this issue when I had less than 5.

```
  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       14036   112640746    7  HPFS/NTFS
/dev/sda3           14037       39532   204796620    7  HPFS/NTFS
/dev/sda4           39533       60801   170843242+   5  Extended
/dev/sda5           39533       42082    20482843+   7  HPFS/NTFS
/dev/sda6           42083       42344     2104483+  82  Linux swap / Solaris
/dev/sda7           42345       42363      152586   83  Linux
/dev/sda8           49659       56953    58597056   83  Linux
/dev/sda9           42364       49658    58597056   83  Linux
/dev/sda10          56954       60801    30909028+  83  Linux

```

---

### Post by bodhi.zazen on 2010-02-22
If mount -a works, then it is likely a problem with concurrency.

In an attempt to speed boot times, the boot scripts are probably trying to mount something too soon.

Edit /etc/rc.local

add

```
sleep 10
mount -a
```

You can sometimes reduce the sleep to 3 or 5 seconds.

---

### Post by Mahngiel on 2010-02-22
Editing rc.local didn't do anything except give me a black desktop and frozen cursor for 10 seconds.

---

### Post by bodhi.zazen on 2010-02-22
> **Mahngiel said:**
> Editing rc.local didn't do anything except give me a black desktop and frozen cursor for 10 seconds.

That sounds odd. I can not reproduce your problem, and, IMO, if mount -a works, the problem is not with fstab or your hardware but my guess would be with your init scripts.

I would not expect the behavior you describe from the edit I suggested to rc.local =(

You can try booting to recovery mode and watching for errors or checking your logs.

Other then that I suggest you file a bug report.

---

### Post by Mahngiel on 2010-02-22
Ok. Thanks for the reply.  This was replicate 3 times and once the edits were removed, my boot up was without the black wallpaper and cursor lock.  
 
I'll try and track down the cause. 
 
As far as the double mounting, do you have any clue or suggestion? Perhaps I should mount via label or partition number?

---

### Post by bodhi.zazen on 2010-02-22
> **mahngiel said:**
> perhaps i should mount via label or partition number?

+1

---

### Post by Mahngiel on 2010-02-23
> mahngiel@studio:~$ ls /dev/disk/by-label -lah
total 0
drwxr-xr-x 2 root root 180 2010-02-22 19:13 .
drwxr-xr-x 6 root root 120 2010-02-22 19:13 ..
lrwxrwxrwx 1 root root  10 2010-02-22 19:13 [COLOR=Blue]Backups[/COLOR] -> ../../sda5
lrwxrwxrwx 1 root root  10 2010-02-22 19:13 [COLOR=Blue]Kubuntu[/COLOR] -> ../../sda8
lrwxrwxrwx 1 root root  10 2010-02-22 19:13 [COLOR=Blue]Storage[/COLOR] -> ../../sda3
lrwxrwxrwx 1 root root  10 2010-02-22 19:13 [COLOR=Blue]Studio[/COLOR] -> ../../sda9
lrwxrwxrwx 1 root root  11 2010-02-22 19:13 [COLOR=Blue]Tota[/COLOR] -> ../../sda10
lrwxrwxrwx 1 root root  10 2010-02-22 19:13 [COLOR=Blue]Win7[/COLOR] -> ../../sda2
lrwxrwxrwx 1 root root  10 2010-02-22 19:13 [COLOR=Blue]Win7\x20Recovery[/COLOR] -> ../../sda1
```
# <file system>                 <mount point>       <type>      <options>               <dump>  <pass>
proc                            /proc                  proc        defaults                     0       0
/dev/scd0                       /media/cdrom0               udf,iso9660 user,noauto,exec,utf8 0       0
[COLOR=Silver]# Windows 7 Restore (/dev/sda1)[/COLOR]
LABEL=[COLOR=Blue]Win7\x20Recover[/COLOR]y                /mnt/Win7Restore    ntfs        noauto,ro              0      2
[COLOR=Silver]# Windows 7 (/dev/sda2)[/COLOR]
LABEL=[COLOR=Blue]Win7[/COLOR]                    /media/Win7        ntfs-3g        auto,users,rw,uid=1000,gid=100,utf8,dmask=027,fmask=1 37 0 0
[COLOR=Silver]# Storage (/dev/sda3) [/COLOR]
LABEL=[COLOR=Blue]Storage[/COLOR]                    /media/Storage        ntfs-3g        auto,users,rw,uid=1000,gid=100,utf8,dmask=027,fmask=1 37 0 0
[COLOR=Silver]# Backup (/dev/sda5)[/COLOR]
LABEL=[COLOR=Blue]Backups[/COLOR]                    /mnt/Backup        ntfs-3g        auto,users,rw,uid=1000,gid=100,utf8,dmask=027,fmask=1 37 0 0
[COLOR=Silver]# Swap (/dev/sda6)[/COLOR]
UUID=3daf19c0-397b-41c8-acba-9c18444bb4a1    none                swap        sw                          0       0
[COLOR=Silver]# Boot Partition (/dev/sda7)[/COLOR]
UUID=967540d4-7ef8-45bd-a3c7-407f613a4fe4    /mnt/Boot        ext4        auto,users,rw             0     0
[COLOR=Silver]# Kubuntu (/dev/sda8)[/COLOR]
LABEL=[COLOR=Blue]Kubuntu[/COLOR]                    /media/Kubuntu        ext4        auto,users,rw             0     0
[COLOR=Silver]# Ubuntu Studio Root (/dev/sda9)[/COLOR]        
UUID=6076410e-248d-4736-8c5b-d2f827eff785     /                   ext4           errors=remount-ro           0       1
[COLOR=Silver]# Tota Linux (/dev/sda10)[/COLOR]
LABEL=[COLOR=Blue]Tota[/COLOR]                    /media/Tota        ignore        auto,users,rw             0     0
```Tried changing to mount via LABEL and by Device, same results. Things come auto mounted now, but I still keep two Places references.  And again, only the ones with the 500GB HD designation are loadable.

Any more clues?

---

### Post by falconindy on 2010-02-23
An observation: you're having things mount in /media via fstab. Have you created those mount points? They're only created automatically for you when a program like Nautilus handles the mounting process.

---

### Post by Mahngiel on 2010-02-23
Yes. First thing i did.

---

