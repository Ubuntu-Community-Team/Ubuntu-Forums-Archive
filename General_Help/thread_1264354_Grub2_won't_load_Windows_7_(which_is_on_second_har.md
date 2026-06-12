---
title: "Grub2 won't load Windows 7 (which is on second hard drive)"
date: 2009-09-12
forum: General Help
---

### Post by Mardok45 on 2009-09-12
I have two hard drives, the primary one has a couple OSs, and the slave with just Windows 7.  

I've tried the following entries:

```

menuentry "Windows 7"{
 set root=(hd1,1)
 devicemap -s hd0 hd1
 chainloader +1
}
```

This gives me 'chainloader: command not found'.


```

menuentry "Windows 7"{
 devicemap -s hd0 hd1
 chainloader (hd1)+1
}

```

It loads the Windows boot loader, but it tells me 'Operating system not found'.


Does anyone know how to solve this problem?

---

### Post by duanedesign on 2010-02-03
anyone have any tips on dualbooting Windows and Ubuntu on separate Hard Drives. Spent some time this evening trying to help someone in the Beginners Team support channel with no luck. Ubuntu is the Primary and Win7 the slave.

this is what we tried in /etc/grub.d/40_custom


```
menuentry "Windows7 (loader) (on /dev/sdb1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 286cc2a6397a0f2a
	chainloader +1

}
```
and

```
menuentry "Windows7 (loader) (on /dev/sdb1)" {
	insmod ntfs
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 286cc2a6397a0f2a
	chainloader +1
```



blkid

```
/dev/sda5: UUID="0fddf3a4-dd16-4917-8ccd-cdc9be97a119" TYPE="swap" 
/dev/sdb1: UUID="30B4A220B4A1E894" TYPE="ntfs" 
/dev/sda1: LABEL="Ubuntu 9.10" UUID="4d0dcee9-780e-42a8-be34-e26ad6c3be49" TYPE="ext4" 
```

fdisk

```
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11661    93666951   83  Linux
/dev/sda2           11662       12161     4016250    5  Extended
/dev/sda5           11662       12161     4016218+  82  Linux swap / Solaris

Disk /dev/sdb: 30.1 GB, 30060527616 bytes
255 heads, 63 sectors/track, 3654 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1ece1ecd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3655    29352960    7  HPFS/NTFS
```

please any help would be appreciated.

---

### Post by linkingeek on 2010-02-03
Check the Bios settings and change the boot order to run windows 7

---

### Post by n0dix on 2010-02-03
Hi duanedesign. I don't understand where is from this number: 286cc2a6397a0f2a, in your blkid i don't see it.

---

### Post by Mark Phelps on 2010-02-03
Did you try just letting GRUB2 find Win7 and add its own entries? 

I have multiple drives, with Win7 NOT on the first drive, I boot from one of my Ubuntu drives -- and GRUB2 found the Win7 OS just fine when I ran update-grub.

---

### Post by madhur_ahuja on 2011-10-17
I am having the same issue. Any update on this one ?

---

### Post by drs305 on 2011-10-17
> **madhur_ahuja said:**
> I am having the same issue. Any update on this one ?

madhur_ahuja,

Welcome to the Ubuntu Forums! 

Please begin your own thread and describe your issue.

In this case, you should run the Boot Info Script. This script will tell us the status of your boot files. You can run it from Ubuntu or the LiveCD. Once run, it will generate a file called RESULTS.txt

Please post the contents of RESULTS.txt in your first post of the new thread. You can get the script and instructions from the "BIS" link in my signature line.

I'm closing this thread since it is old.

---

