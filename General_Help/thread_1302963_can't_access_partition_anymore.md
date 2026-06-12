---
title: "can't access partition anymore"
date: 2009-10-27
forum: General Help
---

### Post by Rah66Comanche on 2009-10-27
Hi,

My system is currently running a dual boot setup, so I have a windows partition, the linux partitions and a main partition for my data. That main partition is in NTFS. Now, I have tried to mount that partition in linux and something must have gone wrong. I dont have acess to it in linux or in windows.

Windows asks me if I would like to format that partition.
In linux, I can see the partition with fdisk -l   , as well *** with geparted.
fdisk -l:     /dev/sda4           10199       38912   230645173+   7  HPFS/NTFS

trying to mount the drive now:
mount -t ntfs /dev/sda4 /media/E
gives me this erreor:
Unexpected clusters per mft record (-1).
Failed to mount '/dev/sda4': Invalid argument
The device '/dev/sda4' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

I am sure that there is still data on the partition because I have a recovery tool for flash drives which managed to find some pictures on it, but its not been made to work with hard drives.

any ideas?

---

### Post by martrn on 2009-10-27
If you look at your mtab file located at /etc/mtab, then this should be properly written so it can mount and unmount your disks as you need or require them.  There are several files located at /etc/ that the kernel will look at when mounting its virtual file system (one that the OS) can call upon when it needs to look at files and these are :
       /etc/fstab file system table
       /etc/mtab table of mounted file systems
       /etc/mtab~ lock file

type : ```
sudo gedit /etc/mtab
```

and add a line that says  :
/dev/sda4 /media/e ntfs-3g rw,user,gid=users 0 0

and you should be able to mount the drive after reboot with natalius --> right_click--> mount.

---

### Post by Rah66Comanche on 2009-10-27
I tried that, but the line I'm adding to /etc/mtab keeps vanishing after reboot.

---

### Post by alphaniner on 2009-10-27
I'm pretty sure you're not supposed to edit /etc/mtab.

Are you sure you don't mean /etc/fstab?

---

### Post by martrn on 2009-10-27
> **alphaniner said:**
> Are you sure you don't mean /etc/fstab?

They are both very simular.  Yes OK you could mount them is fstab.

[https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab")

---

### Post by Rah66Comanche on 2009-10-27
I tried following the instructions for the fstab

but I could not get the UUID,

when I m using "sudo blkid" the /dev/sda4 drive does not show up

---

### Post by martrn on 2009-10-27
Have you installed the ntfs config package ?

```
sudo apt-get install fuse-source
sudo apt-get install ntfs-config
```

I can't see any other problem.
[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G]("https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G")

---

### Post by mechro on 2009-10-27
Some thoughts...

If you're using Ubuntu, should you sudo mount?

Do you need to create /media/E before mounting?

The partition may be corrupted due to power outage or disk drive on its way out or a mistaken format.

You can recover partitions using Testdisk. You may be able to recover data using Photorec (included with Testdisk)

---

### Post by Rah66Comanche on 2009-10-27
[FONT=monospace]i m getting an error with the fuse-source
E: Couldn't find package fuse-source

but blkid can actually find my other ntfs partition.
I think that the mounting point is somewhat corrupted, because I cant see this partition in windows nor in linux, I m just wondering why fdisk -l or geparted can see it.
[/FONT]

---

### Post by alphaniner on 2009-10-27
> **Rah66Comanche said:**
> 
I think that the mounting point is somewhat corrupted, because I cant see this partition in windows nor in linux, I m just wondering why fdisk -l or geparted can see it.


I doubt Windows 'can't see it.'  If you open Windows Disk Manager I'm sure the partition will show up, just like it shows up in gparted.  Being able to mount it (Linux) or assign a drive letter to it (Windows) is a different matter.  I think the filesystem (not the mount point) is corrupted.  There are plenty of resources around to help you troubleshoot this.  I would start with windows tools such as chkdsk.

---

### Post by louieb on 2009-10-27
> **Rah66Comanche said:**
> [FONT=monospace]... I m just wondering why fdisk -l or geparted can see it.[/FONT]

fdisk is listing what is in the partition table. Does not check to see if the partition has a valid file system. 

BTW: +1 for testdisk and photorec.

---

### Post by Rah66Comanche on 2009-10-28
hm, I m running photorec right now, but it doesnt look like its going to save much, any other solutions??

---

### Post by mechro on 2009-10-28
> **Rah66Comanche said:**
> hm, I m running photorec right now, but it doesnt look like its going to save much, any other solutions??

Try and rescue the partition using Testdisk.

---

