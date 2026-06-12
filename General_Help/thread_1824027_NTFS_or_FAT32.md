---
title: "NTFS or FAT32"
date: 2011-08-13
forum: General Help
---

### Post by gaurish108 on 2011-08-13
Hello I am trying to recover my data ever since my BIOS is faliing to mount my hard drive /dev/sda1/ 

Hence I am running the live CD right now as I type this message. 

Can any one tell me how to find out what partition I have whether ntfs or FAT32 through the Terminal. 

I am getting the following fdisk command......> 

root@ubuntu:~# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00057b64

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59272   476097536   83  Linux
/dev/sda2           59272       60802    12285953    5  Extended
/dev/sda5           59272       60802    12285952   82  Linux swap / Solaris


I should have thought that NTFS ir FAT32 would have come under System but it hasn't.

---

### Post by McLinux O'Debian on 2011-08-13
Sda3 uses code 5 which normally means a Fat32 drive. That's your best bet.

---

### Post by Ozymandias_117 on 2011-08-13
```
blkid
``` should tell you the label, UUID and partition type.

---

### Post by mcduck on 2011-08-13
Based on the fdisk output, there are no FAT or NTFS partitions on that drive. Only single Ext partition, and a swap partion (which is a logical partiiton, contained within the extended partition)

Based on the reported cylinder count of the drive, and the start/end points of those partitions, there doesn't even seem to be any unused/unrecognized space so the FAT/NTFS partition you are looking for not showing there can't even be a result from broken partition table or anything like that.

Are you absolutely sure that you are looking a the right drive, and that there really is supposed to be a FAT/NTFS partition somewhere?

---

### Post by -kg- on 2011-08-13
Have you tried running "sudo fdisk -l"?  "Sudo" is usually required for that command.  I can't even get any output at all without it.

OK, with that thought, you obviously already were under "su" privileges, so there likely is no other hard drive installed in your computer.  Under those circumstances, mcduck is right...you have no NTFS ***OR*** FAT partitions on that drive.

The "fdisk -l" command would have listed all partitions on all hard drives connected to the computer (or nothing, without "su" privileges).

<edit> > root@ubuntu:~# fdisk -l

If I had read more closely...

---

### Post by coffeecat on 2011-08-13
> **McLinux O'Debian said:**
> Sda3 uses code 5 which normally means a Fat32 drive. That's your best bet.

Code 5 (properly 0x05) is for an extended partition, which is what sda2 is, not sda3 - there is no sda3 in the OP's output.

The code for FAT32 is 0x0B (it would appear as b in fdisk) and for NTFS 0x07 (appearing as 7).

[http://en.wikipedia.org/wiki/Partition_type](http://en.wikipedia.org/wiki/Partition_type)

I agree with mcduck - there are no NTFS or FAT32 partitions in that output.

---

### Post by gaurish108 on 2011-08-13
Thank you friends for your helpful replies. I said NTFS or FAT32 because I thought they were the only types of file systems out there. Silly me :P

Anyway, taking [Ozymandias_117]("http://ubuntuforums.org/member.php?u=805682")'s suggestion the output of *blkid* is 

```

root@ubuntu:~# blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="acbb0dc4-e9dd-468d-b243-d269eb04db74" TYPE="ext4" 
/dev/sda5: UUID="81370ae0-6002-42f7-8301-7807f0ba1b73" TYPE="swap" 
root@ubuntu:~# 
```Based on this output which is my partition type? *squashfs, ext4 or swap?*

Here is the ouput of fdisk -l again for your reference
```

root@ubuntu:~# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00057b64

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59272   476097536   83  Linux
/dev/sda2           59272       60802    12285953    5  Extended
/dev/sda5           59272       60802    12285952   82  Linux swap / Solaris
root@ubuntu:~# 

```

---

### Post by coffeecat on 2011-08-13
> **gaurish108 said:**
> Based on this output which is my partition type? *squashfs, ext4 or swap?*

Squashfs is to do with your live CD. You have two partitions (apart from the extended), which are ext4 and swap, as already explained. If you are trying to recover data, then I guess it's the ext4 sda1 you need to mount. But the filesystem type is (almost) immaterial. From the live CD simply identify which is the sda1 partition in the left pane of Nautilus, click on it and it will be mounted. Of course, permissions issues may mean that you will need to open a "gksu nautilus" window to access and copy the files.

---

### Post by McLinux O'Debian on 2011-08-13
> **coffeecat said:**
> Code 5 (properly 0x05) is for an extended partition, which is what sda2 is, not sda3 - there is no sda3 in the OP's output.

The code for FAT32 is 0x0B (it would appear as b in fdisk) and for NTFS 0x07 (appearing as 7).

[http://en.wikipedia.org/wiki/Partition_type](http://en.wikipedia.org/wiki/Partition_type)

I agree with mcduck - there are no NTFS or FAT32 partitions in that output.


That's what I originally thought but the code shows as a DOS-based partition, even with the extended, I was sceptical.

---

