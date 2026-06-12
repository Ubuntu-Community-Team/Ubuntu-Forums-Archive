---
title: "Updated ubuntu, lost dual boot option, cannot load windows"
date: 2009-07-31
forum: General Help
---

### Post by Lenny212 on 2009-07-31
Hi, I dual boot Vista and Unbuntu 9.04. I downloaded updates via the standard update Manager. Now Vista is not an option when booting. The files still exist, I just can't boot up in Vista.
I believe the answer has something to do with 'grub' but need a bit more specific instructions on what to do.
Please help, I have some Windows specific applications that I need to use.
Thanks

---

### Post by matey3 on 2009-07-31
sorry I am not an expert may be someone shows up who knows exactly what is wrong but...(in my experience);
You are right, it is the grub that sometimes for some reason changes your menu.lst file!?

You can go to /boot/grub/ and edit menu.lst file or look for a backup of the menu.lst, be sure you copy the menu.lst (the current one) into you home folder or some place for safe keeping before editing it.

Read the instructions inside of the menu.lst file because some of the items are kept hidden etc. it tells you what to do (ie hit escape at boot etc.).

Good Luck!

---

### Post by Lenny212 on 2009-07-31
Hi matey3,

Yep, you have pointed me in the right direction, thanks.
Now I am there I am not sure what to do.
As you can see below I have five options to run Ubuntu but none for Vista.
I do not know what to type in to have Vista as an option.

Cross fingers someone can help with the next step.


## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		f650d612-4b85-4547-bb31-b1069a0d5c71
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=f650d612-4b85-4547-bb31-b1069a0d5c71 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		f650d612-4b85-4547-bb31-b1069a0d5c71
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=f650d612-4b85-4547-bb31-b1069a0d5c71 ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		f650d612-4b85-4547-bb31-b1069a0d5c71
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=f650d612-4b85-4547-bb31-b1069a0d5c71 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		f650d612-4b85-4547-bb31-b1069a0d5c71
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=f650d612-4b85-4547-bb31-b1069a0d5c71 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		f650d612-4b85-4547-bb31-b1069a0d5c71
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=f650d612-4b85-4547-bb31-b1069a0d5c71 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		f650d612-4b85-4547-bb31-b1069a0d5c71
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=f650d612-4b85-4547-bb31-b1069a0d5c71 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		f650d612-4b85-4547-bb31-b1069a0d5c71
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by matey3 on 2009-07-31
oh this is tough because I do not see your windows partition listed!?

I think to start you should do an fdisk -l to see where the Vista partition is located then find the UUID then manually put it in this menu.lst file.
It is a pretty cumbersome task (to do it this way) But there may be an old copy of menu.lst there in the grub folder?

Sorry I do not have any other OSes on my box or I could give you a copy to get an idea from.

Hopefully someone with similar configurations will post their menu file.

Regards;

btw in order to get the uuid you can cd /dev/disk/by-uuid than do an ls -l to see which id belongs to which partition,

---

### Post by matey3 on 2009-07-31
Btt

---

### Post by UltraZone on 2009-07-31
This is what my menu.lst has at the end:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1

In grub to boot into windows I have to specify the Windows Vista Loader, then that takes me into another menu choice between Vista and Ubuntu.  I don't know how yours was originally set up.  Proceed with caution.

---

### Post by merlinus on 2009-07-31
If you post results of

```
sudo fdisk -l
```

there may be a very easy solution.

---

### Post by oldfred on 2009-07-31
If you look at your fdisk -l list you will see something like this:
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7179    57665286    7  HPFS/NTFS

In grub the drive,partition is one less than in linux. i.e. sda1 is (hd0,0), sda2 is (hd0,1) etc. The line with the * is the boot drive & partitition.
You can copy UltraZone's windows entry to the end of your menu.lst and adjust the (hd0,0) entry to match your linux drive & partition. 
If you have trouble figuring this out follow merlinus' advice and we can give you the exact entry.

---

### Post by Lenny212 on 2009-08-01
Hi,
I ran sudo fdisk -l

Here are the results:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x648cc122

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10836    87040138+   7  HPFS/NTFS
/dev/sda2           13699       14593     7189087+   7  HPFS/NTFS
/dev/sda3           10837       13698    22989015    5  Extended
/dev/sda5           10837       13676    22812268+  83  Linux
/dev/sda6           13677       13698      176683+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xefaa92e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241    7  HPFS/NTFS

---

### Post by merlinus on 2009-08-01
You might try adding this at the very end of menu.lst

title Vista
rootnoverify (hd0,0)
makeactive
chainloader +1

You can edit the file by entering this in a terminal:

```
gksudo gedit /boot/grub/menu.lst
```

and then restart.

---

### Post by Lenny212 on 2009-08-02
Woohoo! Thanks everyone for your help.
I tried merlinus' option and updated menu.lst.
And it worked.
Also, thanks for going the extra step and providing the code to edit easily via terminal.

---

### Post by merlinus on 2009-08-02
Glad to hear it is working.  Have fun!

---

