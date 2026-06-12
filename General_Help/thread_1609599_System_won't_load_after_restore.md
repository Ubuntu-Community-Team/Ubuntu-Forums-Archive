---
title: "System won't load after restore"
date: 2010-10-30
forum: General Help
---

### Post by TheGravyOne on 2010-10-30
Hello.  I restored my laptop to an image created the 1st time I used the  laptop.  Since restoring the system won't load.  After the  initial boot screen and check to boot from cd it just resets.  It never  makes GRUB menu were I can choose the OS I want.  I'm dual  booting Vista and ubuntu but can't get into either.  Any ideas?

---

### Post by Irony on 2010-10-30
Do the following from the ubuntu live CD (the one you used to install ubuntu);

```
sudo mount /dev/sda2 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
sudo chroot /mnt
sudo grub-install /dev/sda
```

Replace sda2 and sda with your actual devices. When you get to the boot screen press e for edit and replace kernel version numbers with the one you currently have then boot up.

Once into ubuntu do; 

```
sudo update-grub
```

---

### Post by TheGravyOne on 2010-10-30
Thanks for the quick reply.  I'm quite new to ubuntu and don't really understand your advice.  I'm running ubuntu of the live disc like you said.  Do you mean to enter those codes into the terminal?  Also what exactly do you mean "replace sda2 and sda with your actual devices"?

---

### Post by Old_Grey_Wolf on 2010-10-30
If you ran restore from the MS Windows restore partition or the MS Windows CD you may have lost your Ubuntu partition.

Enter this command in a terminal using the live Ubuntu CD, and post the results, so people can tell what has happened to your partitions.

```
sudo fdisk -l
```

---

### Post by TheGravyOne on 2010-10-30
Windows was installed on my C drives and ubuntu on my D drive.  The system restore only wiped and restored my C drive.  I typed your command and got this-

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf75e0444

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1306    10485760   27  Unknown
/dev/sda2   *        1306       20116   151089152    7  HPFS/NTFS
/dev/sda3           20116       37609   140514172+   7  HPFS/NTFS
/dev/sda4           37609       38914    10480641    5  Extended
/dev/sda5           37609       38852     9986048   83  Linux
/dev/sda6           38852       38914      493568   82  Linux swap / Solaris
ubuntu@ubuntu:~$ ^C

Does this help?

---

### Post by Old_Grey_Wolf on 2010-10-30
Looks like Windows and Ubuntu are still there. Will need to put GRUB back on the computer. What release of Ubuntu are you using? The procedures are different for GRUB and GRUB 2.

---

### Post by TheGravyOne on 2010-10-30
That's good to know.  I'm using ubuntu 10.10.

---

### Post by Old_Grey_Wolf on 2010-10-30
Use this procedure from the Ubuntu Community Documentation [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

I think you want to mount sda5.

This is basically what Irony said above with a little explanation of the commands used.

---

### Post by Quackers on 2010-10-30
On the occasions when I have restored a Clonezilla backup image I have also needed to re-install grub to the mbr of the drive. It's a bit curious, in that Clonezilla says it's backing up the mbr at some point, but it definitely doesn't seem to restore it.

---

### Post by TheGravyOne on 2010-10-30
Thanks for all the help.  Everything's runnin smoothly now.

---

