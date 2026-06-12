---
title: "Change Swap Drive"
date: 2012-03-10
forum: General Help
---

### Post by amirfoad on 2012-03-10
When I was installing Ubuntu, I unfortunately, assigned a wrong 100 GB partition for swap in Ubuntu.
How can I change Swap drive now?
and do you know my data in that partition, have been removed or not?
Thank you.

---

### Post by lrgmmc on 2012-03-10
so you used a data partition as swap, and you had stuff still on there? I'm gonna have to say you probably lost the data that was originally on there. i will do some digging and see.

---

### Post by amirfoad on 2012-03-10
Thanks.

---

### Post by lrgmmc on 2012-03-10
i found this thread it sugested using testdisk. [http://ubuntuforums.org/showthread.php?t=1433685]("http://ubuntuforums.org/showthread.php?t=1433685")

---

### Post by sudodus on 2012-03-10
First you should try to save your data. Probably only the first part of the partition is overwritten, maybe very little, and the rest of the partition contains your file data. The file system with directories is probably damaged. If it can be restored with Testdisk or Gpart, fine! Otherwise you can use Photorec to recover the files reading directly from the disk surface. But the directory structure and the file names will be lost.

You can browse for Testdisk, Gpart and Photorec on the internet. There are several boot disk images (iso files) to be downloaded. See for example 
[[COLOR="Red"]_http://www.cgsecurity.org/wiki/TestDisk_Livecd_[/COLOR]]("http://www.cgsecurity.org/wiki/TestDisk_Livecd")

After you have saved the data, you can edit your (internal HDD) drive with gparted (booted from a live CD or USB drive), where you want to change the swap partition. Finally you should run
```
sudo blkid
``` to find the UUID of the new swap partition and edit fstab
```
sudo nano /etc/fstab
``` Use the UUID string without quotes!

---

### Post by amirfoad on 2012-03-10
> **sudodus said:**
> First you should try to save your data. Probably only the first part of the partition is overwritten, maybe very little, and the rest of the partition contains your file data. The file system with directories is probably damaged. If it can be restored with Testdisk or Gpart, fine! Otherwise you can use Photorec to recover the files reading directly from the disk surface. But the directory structure and the file names will be lost.

You can browse for Testdisk, Gpart and Photorec on the internet. There are several boot disk images (iso files) to be downloaded. See for example 
[[COLOR=Red]_http://www.cgsecurity.org/wiki/TestDisk_Livecd_[/COLOR]]("http://www.cgsecurity.org/wiki/TestDisk_Livecd")

After you have saved the data, you can edit your (internal HDD) drive with gparted (booted from a live CD or USB drive), where you want to change the swap partition. Finally you should run
```
sudo blkid
``` to find the UUID of the new swap partition and edit fstab
```
sudo nano /etc/fstab
``` Use the UUID string without quotes!


Here are the result of blkid :

```
/dev/sda1: UUID="afb4fda3-2c38-4229-bdb4-c1c2a57c711e" TYPE="ext4" 
/dev/sda5: LABEL="Data" UUID="5A4C4CA54C4C7E2F" TYPE="ntfs" 
/dev/sdb1: LABEL="New Volume" UUID="DE36D87136D84BE1" TYPE="ntfs" 
/dev/sdb3: UUID="79521ff7-1568-4d71-94d5-e4e863982925" TYPE="swap" 
/dev/sdb5: LABEL="New Volume" UUID="BE0638C706388307" TYPE="ntfs" 

```
How could I change the type of /dev/sdb3 to ntfs?

---

### Post by sudodus on 2012-03-10
> **amirfoad said:**
> Here are the result of blkid :

```
/dev/sda1: UUID="afb4fda3-2c38-4229-bdb4-c1c2a57c711e" TYPE="ext4" 
/dev/sda5: LABEL="Data" UUID="5A4C4CA54C4C7E2F" TYPE="ntfs" 
/dev/sdb1: LABEL="New Volume" UUID="DE36D87136D84BE1" TYPE="ntfs" 
/dev/sdb3: UUID="79521ff7-1568-4d71-94d5-e4e863982925" TYPE="swap" 
/dev/sdb5: LABEL="New Volume" UUID="BE0638C706388307" TYPE="ntfs" 

```
How could I change the type of /dev/sdb3 to ntfs?

Try to repair it with Testdisk or Gpart! Otherwise, try to save the files with Photorec ***before*** changing the partition to ntfs!

---

