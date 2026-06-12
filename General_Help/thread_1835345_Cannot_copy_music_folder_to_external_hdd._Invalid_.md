---
title: "Cannot copy music folder to external hdd. Invalid filename encoding."
date: 2011-08-29
forum: General Help
---

### Post by RideTheSpiral on 2011-08-29
So I'm trying to transfer my music folder (110gB) and immediately it stopped and said it could not transfer because of the filename encoding. I rescued the folder using testdisk.

Downloaded utf8 migration tool and it is giving me the following error: Your current encoding was not found, or you are using the C locale.  Please pick a supported language from /usr/share/i18n/SUPPORTED and log in again.

I have English Canadian selected... :confused:

---

### Post by RideTheSpiral on 2011-08-29
The external is formatted with fat32 and had the files on it in the first place

laptop is formatted with ext4

---

### Post by ajgreeny on 2011-08-29
Are there any files in the folder that are larger than 4GB, eg an archive or something similar that you have made, as there is a file size limit of 4GB for fat32.

---

### Post by RideTheSpiral on 2011-08-29
No, it is saying the filenames are invalid. 
its usually just one character in the name that shows up as a weird symbol and wont get copied. but I can see them fine on the laptop itself..

---

### Post by RideTheSpiral on 2011-08-29
Anybody? I'm getting frustrated here :confused:

I've tried just about everything google came up with

---

### Post by dcstar on 2011-08-30
> **RideTheSpiral said:**
> No, it is saying the filenames are invalid. 
its usually just one character in the name that shows up as a weird symbol and wont get copied. but I can see them fine on the laptop itself..

Windows filesystems are **not** Linux filesystems, you just cannot copy things that contain legal Linux filesystem names to primitive filesystems like FAT.

---

### Post by tredegar on 2011-08-30
> I'm getting frustrated here
How is the drive being mounted? Is it being "auto-mounted", or are you mounting it yourself?

Please mount the FAT32 drive, and then tell us the output of **mount**

---

### Post by RideTheSpiral on 2011-08-31
I don't think it's being mounted automatically, but nautilus does it when I click the icon in places

```
justin@justin-lenovo:~$ mount
/dev/sda6 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /var/lib/ureadahead/debugfs type debugfs (rw,relatime)
/dev/sdb1 on /home type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/justin/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=justin)
/dev/sdd1 on /media/4-13mdv2010 type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sdd5 on /media/Large files + backups type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1 on /media/7b34a0ae-0e4d-4461-91e6-066a164d9907 type ext2 (rw,nosuid,nodev,uhelper=udisks)
```
/dev/sda is ssd
/dev/sdb1 is the ext4 partition on my laptops hdd
/dev/sdd1 is the FAT32 partition on external

---

### Post by tredegar on 2011-08-31
> /dev/sdd1 on /media/4-13mdv2010 type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,**utf8=1**,showexec,flush)
Looks like it is being mounted with the utf8 option, but that's not helping.

You could unmount it then try mounting it manually with the iocharset=utf8 option:
```
sudo umount /dev/sdd1
sudo mkdir /mnt/test
sudo mount /dev/sdd1 -o iocharset=utf8,umask=000 /mnt/test
```
Don't forget to unmount it when you have finished with it.

---

### Post by coffeecat on 2011-08-31
> **RideTheSpiral said:**
> So I'm trying to transfer my music folder (110gB) and immediately it stopped and said it could not transfer because of the filename encoding.

> **RideTheSpiral said:**
> No, it is saying the filenames are invalid. 
its usually just one character in the name that shows up as a weird symbol and wont get copied. but I can see them fine on the laptop itself..

@RideTheSpiral, you haven't responded to this:

> **dcstar said:**
> Windows filesystems are **not** Linux filesystems, you just cannot copy things that contain legal Linux filesystem names to primitive filesystems like FAT.

There are a number of characters that Linux filesystems allow, which FAT32 doesn't. These are illegal in FAT32 / : ; * ? " < > |. It could be that the copy is simply choking an an illegal character. What is the filename of the file that is causing the error message to appear?

> **RideTheSpiral said:**
>  I rescued the folder using testdisk.

I hope you didn't. Testdisk is for recovering lost partitions.

---

### Post by RideTheSpiral on 2011-08-31
I switched my windows 7 lenovo y560 w/ 32GB SSD and 500GB HDD over to ubuntu. I copied my music folder to an ntsf file partition (yes, all of these files were once on an ntsf partition as well as the fat32 (main media folder))on an external hdd to back it up. Once I did this, I proceeded to install ubuntu. 

Copied the music to the laptop, and cool it worked or so I though. I then deleted the old copy from the backup partition as well as the fat32 partition. It didn't copy anything and just went whack

Next I copied it back to the fat32, were it really screwed up and all the files went missing, leading to the testdisk part which recovered the files off the external since they seemingly go lost on my laptop. some of the filenames show invalid characters where there are spaces..



NOW I've arrived at the point where my music is all here on my laptop, but now I cannot transfer it to the fat32 partition. Once again, these were all originally from windows partitions

---

### Post by RideTheSpiral on 2011-08-31
> **80aless said:**
> maybe try this
convmv -r --notest -f windows-1255 -t UTF-8 *

This has saved my life. Only 2 files were not able to be copied after running this in the offending folder. 

Thread solved I think

---

