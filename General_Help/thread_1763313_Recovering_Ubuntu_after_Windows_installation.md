---
title: "Recovering Ubuntu after Windows installation"
date: 2011-05-20
forum: General Help
---

### Post by coffeholikas on 2011-05-20
Trying to follow [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
But something is failing [http://pastebin.com/kiZWwLAC](http://pastebin.com/kiZWwLAC)

---

### Post by Lateralis on 2011-05-20
Try changing the mount point from "/media/Ubuntu HDD" to something like "/media/Ubuntu".  The space appears to be confusing the Grub install step, even though you've escaped it with a backslash in one of your attempts.

---

### Post by coffeholikas on 2011-05-20
```
ubuntu@ubuntu:~$ sudo umount /media/Ubuntu\ HDD
ubuntu@ubuntu:~$ sudo rmdir /media/Ubuntu\ HDD
rmdir: failed to remove `/media/Ubuntu HDD': No such file or directory
```trying to do [https://help.ubuntu.com/community/MoveMountpointHowto](https://help.ubuntu.com/community/MoveMountpointHowto)

---

### Post by coffeholikas on 2011-05-20
Also theres no sda1 in fstab
```
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0 
```

---

### Post by Lateralis on 2011-05-20
> 
```

ubuntu@ubuntu:~$ sudo umount /media/Ubuntu\ HDD
ubuntu@ubuntu:~$ sudo rmdir /media/Ubuntu\ HDD
rmdir: failed to remove `/media/Ubuntu HDD': No such file or directory

```
trying to do [https://help.ubuntu.com/community/MoveMountpointHowto](https://help.ubuntu.com/community/MoveMountpointHowto)


Ah, OK.  I will assume that you have set the partition label to be "Ubuntu HDD."  If that is the case, then Ubuntu will automagically put the mount point to be "/media/Ubuntu HDD".  To change the mount point, you will need to know the /dev/sdXY designation of the partition.  Or, what you could do is bind the partition to another directory.  

First, remount the partition.  If you are in Ubuntu 10.10 or earlier, click Places and select "Ubuntu HDD" from the list.  That will remount the drive to "/media/Ubuntu HDD."  If you are in 11.04, click on the Home folder in the Unity launch bar and click on the "Ubuntu HDD" drive in the left hand pane.  

When the drive is mounted, open up a terminal and type:

```

mkdir ~/Ubuntu
sudo mount --bind /media/Ubuntu\ HDD ~/Ubuntu
sudo grub-install --root-directory=/home/$(whoami)/Ubuntu /dev/sda1
sudo umount ~/Ubuntu
rm -ri Ubuntu

```


**Edit:** 

> Also theres no sda1 in fstab

If you are using the LiveCD, there won't be an entry for sda1 in fstab, as the LiveCD has no knowledge *a priori* over your hard drive configuration.  But if the hard drive is being mounted OK, then that is fine.  If you want to check that your drives and partitions are being detected properly, you can type:

```

blkid

```

This will give you the /dev/sdXY designations of all your connected storage devices, their labels, UUIDs and file system types.

---

### Post by coffeholikas on 2011-05-20
```
ubuntu@ubuntu:~$ mkdir ~/Ubuntu
ubuntu@ubuntu:~$ sudo mount --bind /media/Ubuntu\ HDD /Ubuntu
mount: mount point /Ubuntu does not exist
ubuntu@ubuntu:~$ 
```

and this does nothing
blkid

---

### Post by coffeholikas on 2011-05-20
```
mount: mount point /Ubuntu does not exist

```
This is horror movie

---

### Post by Lateralis on 2011-05-20
> **coffeholikas said:**
> ```
mount: mount point /Ubuntu does not exist

```
This is horror movie

Ah, that is entirely my fault.  There's a typo in my code box.  There should be a ~ before /Ubuntu in the second line.

```

mkdir ~/Ubuntu
sudo mount --bind /media/Ubuntu\ HDD **~/Ubuntu**
sudo grub-install --root-directory=/home/$(whoami)/Ubuntu /dev/sda1
sudo umount ~/Ubuntu
rm -ri Ubuntu

```

Also, 

```

sudo blkid

```

Sorry! :redface:

---

### Post by coffeholikas on 2011-05-20
```
ubuntu@ubuntu:~$ sudo mount --bind /media/Ubuntu\ HDD ~/Ubuntu
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/home/$(whoami)/Ubuntu /dev/sda1
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partitionless disk or to a partition.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: will not proceed with blocklists.
```Everyone makes mistakes, I'm just glad, that someone is helping me :]

also 
```
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/loop1: UUID="8a933f44-f817-4564-af73-2f03017ed3ca" TYPE="ext3" 
/dev/sda1: LABEL="Ubuntu HDD" UUID="d3a0bc4c-9348-4f22-b563-c711f283729b" TYPE="ext4" 
/dev/sda2: UUID="6D7CD2BD31F52815" TYPE="ntfs" 
/dev/sda5: UUID="556ba151-5980-47b8-8ead-59e5da74dfa0" TYPE="swap" 
/dev/sdf1: UUID="56F4-4048" TYPE="vfat" 
```

---

### Post by coffeholikas on 2011-05-20
Just try'ed
```
sudo grub-install --root-directory=/media/d3a0bc4c-9348-4f22-b563-c711f283729b /dev/sda1

```
 output:
```
/usr/sbin/grub-probe: error: cannot stat `aufs'.
```

---

### Post by coffeholikas on 2011-05-20
Went to FreeNode IRC, got some help, fixed problem. Still thanks for trying to help.

---

