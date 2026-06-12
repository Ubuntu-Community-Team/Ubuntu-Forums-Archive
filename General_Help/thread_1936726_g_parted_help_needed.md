---
title: "g parted help needed"
date: 2012-03-06
forum: General Help
---

### Post by kevinorourke2008 on 2012-03-06
Hello everybody, after my recent hard drive swap I now have a spare 160 gig hdd. My question is what is the best format for this drive ? is it ext, fat , fat32. I just don't know. It will be used on my linux system only. Any suggestions greatly appreciated. 
Kev

---

### Post by Script Warlock on 2012-03-06
for linux only you can use ext.

---

### Post by howefield on 2012-03-06
I'd format with ext4, same as my system drive.

Although I have a ntfs partition for running Windows VMs, not that it needs to be ntfs or is required, just a preference for running VMs from their native file system.

But really it is down to your personal choice.

---

### Post by dave2001 on 2012-03-06
If it's a linux box, then use the native ext4 filesystem. If it will be interacting with other windows/mac computers a lot, you might want to put in a smaller FAT partition for easy file transfers, etc.

---

### Post by kevinorourke2008 on 2012-03-07
So let me get this right if I use the ext4 format I won't be able to transfer from the spare drive to a windows based machine or vice versa ?
kev

---

### Post by howefield on 2012-03-07
> **kevinorourke2008 said:**
> So let me get this right if I use the ext4 format I won't be able to transfer from the spare drive to a windows based machine or vice versa ?
kev

You will be able to do that with Samba.

Windows on it's own can't read the ext file system. Although there are drivers out there that supposedly can, but I believe they are not very robust.

---

### Post by oldfred on 2012-03-07
Samba is for connecting two different computers.

If installed in the same computer then Linux reads NTFS & FAT, but Windows does not read Linux formated partitions. Then a separate NTFS shared data partition is suggested. 

If an external drive Windows will only read the first partition, so if you need to use drive with other Windows systems create a NTFS partition as the first partition. Only if using with an xbox or Mac then you may need FAT formating. FAT does not have a journal so repairs/ckhdsk can be time consuming for large partitions and FAT32 cannot store files over 4GB.

---

### Post by MisterGaribaldi on 2012-03-07
I would avoid FAT if possible. There are some pretty significant (especially these days) file size limitations. Your best bet is to format it as NTFS. Windows boxen can *obviously* handle that, and Macs can read (and, if you install OSXFUSE + NTFS-3G, they can also write to) NTFS partitions.

---

### Post by garyed on 2012-03-07
It really depends on what your plans are. If you format it ext you can copy files to & from your Windows drive to it but only while booted into Linux. If you want to copy files to & from it while booted into Windows then you need to format it ntfs.

---

### Post by dave2001 on 2012-03-07
> **oldfred said:**
> 
If an external drive Windows will only read the first partition, so if you need to use drive with other Windows systems create a NTFS partition as the first partition. .

In my experience, Windows 7 recognizes multiple partitions on an external hard disk drive, even when connected through USB. It still will not, however, recognize multiple partitions on an external flash drive.

---

