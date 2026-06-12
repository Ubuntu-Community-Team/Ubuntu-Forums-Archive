---
title: "How to make an backup to my external hard disk"
date: 2011-01-16
forum: General Help
---

### Post by romy.mathew on 2011-01-16
Hi 

My ubuntu login window seems to be chrased and seems no way to restore it. I was planning to move ahead with reinstalling it but could any1 tell me how can i copy data to external hard disk.

I am in Mannual restore section with promt staying at 
root@ubuntu :/#

---

### Post by DeMus on 2011-01-16
> **romy.mathew said:**
> Hi 

My ubuntu login window seems to be chrased and seems no way to restore it. I was planning to move ahead with reinstalling it but could any1 tell me how can i copy data to external hard disk.

I am in Mannual restore section with promt staying at 
root@ubuntu :/#

Install grsync, type original path in upper line and destination path in lower line, set options to your liking and execute.

---

### Post by Mortesins93 on 2011-01-16
You could just boot with a LiveCD, insert your external hard disk, then go on the file manager, mount the partition where you have your data and copy it to your hard disk.

---

### Post by James78 on 2011-01-16
You could also use dd to copy the disk byte for byte onto another hard drive (which will make a 100% copy of it). You can also boot into a livecd, mount the hard drive, and tar all the contents then transfer them somewhere else for safe keeping. Whatever's easiest for you. :p

---

### Post by romy.mathew on 2011-01-16
> **Mortesins93 said:**
> You could just boot with a LiveCD, insert your external hard disk, then go on the file manager, mount the partition where you have your data and copy it to your hard disk.

Hi Mortesins / James78

Thanks for the response

Before I reach the Login section I see  
"Type s for swith or M or mannual restore"

I tried S but nthing happend then I tried M. it took me to root@ubuntu:/#

How i restore it manually

---

### Post by ajgreeny on 2011-01-16
Is this a wubi installed version of ubuntu, ie installed inside windows?

---

### Post by vanadium on 2011-01-16
To restore manually, you first need to determine the device names of your partitions
```

blkid

```
The device names look like /dev/sda1, /dev/sdb1. I will take these names as example.

Mount the devices.
```

mkdir sda1 sdb1
mount /dev/sda1 sda1
mount /dev/sdb1 sdb1

```

Now, the contents of the drives will be accessible in the directories sda1 and sdb1, respectively. You can copy the contents of one to the other, e.g. from sda1 to sdb1 with either

```

rsync -av sda1/ sdb1/

```

or

[code]
cp -a sda1/* sdb1
[code]

---

### Post by romy.mathew on 2011-01-16
When I type blkid I get following 
1. Loop0: UUID "........." Type ="ext4"
2. sda1 : UUID "........." Type = "ntfs"
3. sda5 : UUID "........." Type = "ntfs"
4. sdb1 : UUID "........." Type = "ntfs"
5. sdc1 : UUID "........." Type = "vfat"

The 1st one is the partition for the Ubuntu. 2nd and 3rd are windows OS 
4th one is the external hard disk and finally 5th one is the pen drive.

When I type Mkdir at my promt : it warns me saying 
"MKDIR : cannot create directory loop0 : Read only file system"

---

### Post by vanadium on 2011-01-16
Your output would suggest that indeed, your Ubuntu install is a wubi install, i.e. an install of Ubuntu within Windows. Your Ubuntu file system is located within a file on the Windows partition. I am not sure how you could mount/recover such a file system.

---

### Post by vanadium on 2011-01-16
Perhaps take a look here for troublehshooting:
[https://wiki.ubuntu.com/WubiGuide#Cannot%20boot%20into%20Ubuntu](https://wiki.ubuntu.com/WubiGuide#Cannot%20boot%20into%20Ubuntu)
An improper shutdown of Windows could cause Ubuntu not to boot. The solution is to check and repair the windows drives. Maybe this might be all you need.

---

