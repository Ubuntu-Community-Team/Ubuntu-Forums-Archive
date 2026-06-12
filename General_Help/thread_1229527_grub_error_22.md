---
title: "grub error 22"
date: 2009-08-02
forum: General Help
---

### Post by ichundu on 2009-08-02
hi,
my friend had ubuntu 8.04 installed on his laptop (dual booting with windows vista) and decided to remove it for a while. he deleted the ubuntu partition from disk management tools in vista. after restart he's getting grub error 22, also the list where you choose which OS to start doesn't show up so he's not able to boot vista.
i've read that booting from a windows cd and entering the command line interface (through the repair option) would fix the problem by running this command: fixmbr, but we don't have any vista installation disk. i have a xp disk but it doesn't boot because it needs sata drivers to detect the hdd (another issue but not related with the current problem). so i guess the only option remains to boot from the ubuntu live cd. i want to remove the grub menu from showing up at startup and format the ex-linux partition with ntfs filesystem. how do i do that?
any suggestions are appreciated. thanks in advance! ;)

---

### Post by sigixv on 2009-08-02
[http://www.cyberciti.biz/faq/linux-how-to-uninstall-grub/](http://www.cyberciti.biz/faq/linux-how-to-uninstall-grub/)

> You can also use dd command from Linux itself (it removes partition table):
```
dd if=/dev/null of=/dev/sdX bs=512 count=1
```  Just remove MBR, without the partition table (see comment below):
```
# dd if=/dev/null of=/dev/sdX bs=446  count=1
```  Replace /dev/hdX with your actual device name such as /dev/hda. Use fdisk -l command to find out device name:
```
# fdisk -l
```Output: 
 ```
Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      104391   83  Linux
/dev/sda2              14       30384   243955057+  83  Linux
/dev/sda3           30385       30515     1052257+  82  Linux swap
```

---

### Post by dandnsmith on 2009-08-02
I suggest that that 'help' isn't, as all it can effect is the removal of the GRUB bootloader stage 1 code from the MBR - it won't restore bootability of the Vista.

That said, I don't know how you would overcome the SATA problem - I think I'd start by googling for a Vista boot CD, and hope the necessary tools were there. Alternatively try a Super Grub CD, to see if it can restore bootability.

---

### Post by sigixv on 2009-08-02
Otherwise, with an xp cd it is possible to (slip)stream it so that it includes the needed sata drivers or other things you might need  (just google it)

---

### Post by ichundu on 2009-08-02
> **dandnsmith said:**
> I suggest that that 'help' isn't, as all it can effect is the removal of the GRUB bootloader stage 1 code from the MBR - it won't restore bootability of the Vista.
i'm giving it a try though

> **sigixv said:**
> Otherwise, with an xp cd it is possible to (slip)stream it so that it includes the needed sata drivers or other things you might need  (just google it)
yes that's true, i can do that with nLite, but i've just been lazy and haven't found yet the right sata drivers for this laptop yet and the hp site is a bit confusing

> **sigixv said:**
> [http://www.cyberciti.biz/faq/linux-how-to-uninstall-grub/](http://www.cyberciti.biz/faq/linux-how-to-uninstall-grub/)
thanks for the link. i am unsure what to replace sdx with. the output of fdisk -l is:
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7ee3486f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12964   104133298+   7  HPFS/NTFS
/dev/sda3           12965       19458    52163055    f  W95 Ext'd (LBA)
/dev/sda5           12965       17771    38612196    7  HPFS/NTFS
/dev/sda6           17772       19458    13550827+   7  HPFS/NTFS
```
my friend told me he managed to format the deletet linux partition with ntfs filesystem through a utility booting disk (hirens)

---

### Post by egalvan on 2009-08-02
SuperGRUB LiveCD can fix this problem.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by ichundu on 2009-08-02
> **egalvan said:**
> SuperGRUB LiveCD can fix this problem.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

thanks (also thanks to dandnsmith who previously suggested that) that did fix it

---

### Post by egalvan on 2009-08-03
> **ichundu said:**
> thanks (also thanks to dandnsmith who previously suggested that) that did fix it

Good to hear that SuperGRUB fixed your problem.

Perhaps you may consider a small ($2) donation to the authors?

No, I am in no way affiliated or connected to them,
other than as a satisfied customer.
They are on my "Donate every six months or once a year" list.
along with 

gparted
PartedMagic
Doom9
fs-driver (ext2 for windows)

among others

---

