---
title: "Grub Error 25: Disk Read"
date: 2009-08-12
forum: General Help
---

### Post by looter211 on 2009-08-12
I have a dual boot setup with two separate hds.  Vista was installed first and is located on drive 1.  Ubuntu on drive 2.  I ran some updates in Ubuntu today and then booted back into Vista.  After running updates in Vista I rebooted and tried booting back into Vista only to see this error.  I can still boot into Ubuntu just fine.  I can even mount the drive with Vista on it from within Ubuntu so Im thinking that grub got jacked up somehow?  Anyways, not really sure and could really use some assistance.      Please help.  

Here is my grub conifg

```
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		8c83f501-9af2-4930-bdd5-da97c5fe3cdd
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=8c83f501-9af2-4930-bdd5-da97c5fe3cdd ro splash
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		8c83f501-9af2-4930-bdd5-da97c5fe3cdd
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=8c83f501-9af2-4930-bdd5-da97c5fe3cdd ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

#title		Ubuntu 8.10, kernel 2.6.27-7-generic
#uuid		8c83f501-9af2-4930-bdd5-da97c5fe3cdd
#kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8c83f501-9af2-4930-bdd5-da97c5fe3cdd ro quiet splash 
#initrd		/boot/initrd.img-2.6.27-7-generic
#quiet

#title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
#uuid		8c83f501-9af2-4930-bdd5-da97c5fe3cdd
#kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8c83f501-9af2-4930-bdd5-da97c5fe3cdd ro  single
#initrd		/boot/initrd.img-2.6.27-7-generic

#title		Ubuntu 8.10, memtest86+
#uuid		8c83f501-9af2-4930-bdd5-da97c5fe3cdd
#kernel		/boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista Business (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```


Here is my output from sudo fdisk -l
```
Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x14e2f572

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19174   154015123+  83  Linux
/dev/sda2           19175       19929     6064537+   5  Extended
/dev/sda5           19175       19929     6064506   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xec3b14ae

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488384001    7  HPFS/NTFS

```

---

### Post by Arand on 2009-08-12
This is what I am using for handing over to BCD (vista bootloader) from grub booted off a usb stick:```
title		Windows XP Home/Windows Vista (BCD loader)
rootnoverify	(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```I would assume that the conditions are similar to yours. So you could try using "rootnoverify" instead of "root" in your case. Or remove the "makeactive". My guess would be on the rootnoverify though, since according to grub documentation:> [rootnoverify] Similar to root (see root), but don't attempt to mount the partition. This is useful for when an OS is outside of the area of the disk that GRUB can read, but setting the correct root device is still desired. Note that the items mentioned in root above which derived from attempting the mount will not work correctly. 
- Arand

---

### Post by looter211 on 2009-08-12
Arand,  Thanks for the swift  reply,  I appreciate your insight very much.  I tried editing the menu.lst as you  advised however,  I am still  getting the same error from Grub.  Also worth mentioning, I did not run into this problem until updating ubuntu to 9.0.4  I will try to wait another day or so to see if anyone else can offer some help and then its off to drastic measures!  If you  or anyone else has any other thoughts on what I can try to  fix  the dual boot I would love to hear them.  Thanks again.

---

### Post by looter211 on 2009-08-15
Sorry but I have to bump. I could really use some advice as far as what to 
do next .  Should I attempt to reinstall grub?  Should I throw in the vista DVD 
and try to repair it that way?  Perhaps something else?  I really don't want 
to have to start reinstalling OSs

---

### Post by looter211 on 2009-10-09
I still dont know why this has happened but it has happened once since then.  Both times I booted into Ubuntu and then its update.  Then I booted back into Ubuntu one more time before restarting back to Vista and the problem was solved.  Again both times this has happened I had to update ubuntu reboot into ubuntu once more before I could get into Vista.  No clue, just thought I would follow up and add my two cents.

---

