---
title: "Removing Ubuntu for W7 (NTFS problem)"
date: 2012-07-31
forum: General Help
---

### Post by AliasEll on 2012-07-31
Hey,

I have a advent netbook which is my girlfriends. She got a laptop so she gave the netbook to me - I installed Ubuntu on it.

However she now needs it back, and thus needs Windows 7 back on the thing.  After installing windows onto many other pc's from USB, I thought it would be easy...

The laptop doesn't like FAT32 formats on the USB, and when using FAT16 I get a "cannot find install.wim" message.  The only way to get around this is to format it with NTFS.  I successful did all of that, however when coming to install windows, it says that the main system partition is not NTFS (I assume its FAT32 because of Ubuntu).

I literally have no clue what to do now.

Basically I want:

1) Remove Ubuntu completely
2) Make the main drive as NTFS
3) Install windows back onto the main drive

Anyone got any ideas?

---

### Post by drmrgd on 2012-07-31
Are you not getting the option to format the drive prior to installing Windows?  I believe if you just want to replace Ubuntu with Windows, it's simply a matter of choosing to do a full install, including formatting the drive, from the Windows installer.  

If, for some reason (and it's a bit hard to imagine), you can't get Windows to format the drive, you could try a 3rd party tool like [Gparted Live]("http://gparted.sourceforge.net/livecd.php/").  You'd then boot from the live CD that you made, and format the drive as NTFS (or you could just use the drive to wipe all partitions and let Windows do the partitioning for you!).  Then load up the Windows installer and you should be good to go.

---

### Post by black veils on 2012-08-03
you need to use gparted to delete everything on the harddrive before using the windows installer, it wont work otherwise. i know that was partially said already.

---

### Post by Ubun2to on 2012-08-03
You should use GParted Live Disk to wipe the drive. Then, let the Windows disk take the wheel.  The reason you can't use Windows for this is simple-Windows can only recognize and work with NTFS and FAT32 partitions. Ubuntu uses either the ext2, 3, or 4 filesystem (although, if you just recently installed it, it would be ext4).

---

