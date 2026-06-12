---
title: "Remove Dual boot"
date: 2006-04-08
forum: General Help
---

### Post by DirtyJay on 2006-04-08
How do I remove a dual boot system and just get back to a Ubuntu only operating system.  I have a two hard drive system, one with Ubuntu and one with WindowsXP.  I think the grub is loaded onto the Windows drive.  I wish to remove the windows drive altogether and have Ubuntu load up on it's own.

thanks for any help

---

### Post by llamakc on 2006-04-08
What does the output of `sudo fdisk -l /dev/hda` and `sudo fdisk -l /dev/hdb` report?

Also, in your /boot/grub/menu.lst file it says precisely where grub is installed. For me this entry is at:

```

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

```

Which is the first partition of the first IDE device (on my box). hd0,0 is the same as /dev/hda1.

What does yours have?

---

### Post by DirtyJay on 2006-04-09
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9729    78148161    7  HPFS/NTFS

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       19376   155637688+  83  Linux
/dev/hdb2           19377       19457      650632+   5  Extended
/dev/hdb5           19377       19457      650601   82  Linux swap / Solaris

My grub.lst has:

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

Thanks for the help

---

### Post by Snocrash on 2006-04-09
Any reason you want to pull the windows drive????

Since Linux does not care witch drive it is on (unlike windoze) it would be easier to leave it and just set grub to default to linux with no boot menu. Then you could reformat the windows partition to ext2,3 or whatever and mount it as a storage drive in you /etc/fstab.

Otherwise, if there is a problem with the windows drive, you can remove it and then use a set of grub floppies or (I think) the Ubuntu CD to install grub to a different drive and then set it up. If there is no problem with the drive, you can change it in the grub config and then just re-install grub.

[Grub online manual]("http://www.gnu.org/software/grub/manual/grub.html")

[Ubuntu wiki info for grub]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows")

-Sno

---

### Post by aysiu on 2006-04-09
I would use a live CD to delete the Windows partition and format it as Ext3, and  [reinstall Grub](https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub) to the MBR and then reboot and modify the /etc/fstab for the new ex-Windows Ext3 partition.

---

### Post by llamakc on 2006-04-09
According to what you've posted, Grub is installed on the 2nd hard disk which is where Ubuntu is also. Therefore all you have to do is reformat /dev/hda and partition as you want; remove the entry for booting Windows in your menu.lst and then run `sude update-grub`

No reason to bother with a livecd when you already have all of the tools at your disposal.

---

### Post by oscarmeyer51 on 2008-03-10
OK, all of the above is good and well, but many people have installed dual boot with only a single hard drive. Is there any tutorial/how-to for moving from a single HD dual boot system (Ubuntu & Windows (various flavors) or Ubuntu & Mac OS) to an only Ubuntu boot? I have been looking for such a tutorial/how-to since version 6.10 and have not been able to locate anything better than this thread. 

Anyone else out there wanting to drop their Windows or Mac partition(s), keep their data, and only have Ubuntu on their system? Or am I the Lone Ranger here? 

If there is enough interest in this, perhaps this could be something included in the Ubuntu documentation....?? 

Comments? Thoughts? Musings? ....

---

