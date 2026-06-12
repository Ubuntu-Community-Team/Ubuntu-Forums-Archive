---
title: "Dual Booting Breezy and Vista"
date: 2006-04-06
forum: General Help
---

### Post by rowanparker on 2006-04-06
Hey,
I am trying to dual boot Breezy and Vista.

I did triple boot Breezy, XP and Vista which worked but then i decided to ditch XP.

I installed Vista first (as i'm meant to), this booted fine. I then installed Ubuntu, this also booted fine, but during the installation of grub it didn't detect another OS. I restarted and upcame grub showing Ubuntu which now works fine. 

I added:```

title           Windows Vista (Beta 2)
root            (hd0,0)
makeactive
chainloader     +1
```
To the /boot/grub/menu.lst file.

I restarted and selected Vista from grub.
"NTDRL (can't remember exactly) wasn't found
Press Ctrl-Alt-Delete to Restart"
and thats all i can do.

Please Help, Rowan.

---

### Post by Sutekh on 2006-04-06
Is Windows Vista on (hd0,0)?  Can you confirm this?
```
sudo fdisk -l
```will list the partitions on your discs.

If you have multiple hard discs, check the device.map
```
cat /boot/grub/device.map
``` to see what your hard drive with Vista (/dev/###) is mapped to (hd#).  

For example you might have Vista on /dev/hda1, with a device.map of "(hd0) /dev/hda"

You would then use
```
title           Microsoft Windows Vista
root            (hd0,0)
savedefault
chainloader     +1
```

But if Vista is on say /dev/sda1 and the device.map has "(hd1) /dev/sda", then you would need something like this
```
title           Microsoft Windows XP Professional
root            (hd1,0)
savedefault
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

```
With the extra **map** commands to trick Windows into thinking that it is on the first hard drive.

---

### Post by towsonu2003 on 2006-04-06
See [http://www.ubuntuforums.org/showthread.php?t=149680&highlight=boot+vista](http://www.ubuntuforums.org/showthread.php?t=149680&highlight=boot+vista)
which has the solution that works in Dapper (should work in Breezy as well). 

This is a bug, but was not reported as far as I know... While you're fixing yours, you might wanna file a bug report as well in ubuntu malone.

---

### Post by rowanparker on 2006-04-06
Vista is hda1.

EDIT:
I reinstalled Vista so it had a boot loader and then used rescue mode to grub-install to a floppy so now i can boot both. Its not exactly what i want but it's alright for now.

---

### Post by blake711 on 2006-09-14
Hello I have read the info provided by sutekh and I just can't figure out how to map my vista drive.  I have 3 drives install in my box.   2 are SATA and one is a IDE that I bought specifically to boot Vista and Ubuntu on.  Last night I installed Vista on it with my sata drive disabled so the vista boot loader wouldn't hose my xp install.  Then I installed ubuntu.. ubuntus grub picked up my XP install but not vista as this is a bug still.   

Here is a copy of my Fdisk-l

```
blake@nacho:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3916    31455238+   c  W95 FAT32 (LBA)
/dev/sda2            3917        9728    46684890    f  W95 Ext'd (LBA)
/dev/sda5            3917        9728    46684858+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS

Disk /dev/hdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        5354    43005973+   7  HPFS/NTFS
/dev/hdc2            5355       10708    43006005   83  Linux
/dev/hdc3           10709       30140   156087540    7  HPFS/NTFS
/dev/hdc4           30141       30401     2096482+  82  Linux swap / Solaris
blake@nacho:~$


```

My Vista is installed on /Dev/HDC1 and my Ubuntu is on dev/hdc2

Can you please tell me what I need to use as maps for my vista to be shown in by grub.  My current menu.lst looks like this. 
> 
title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdc2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdc2 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1 

So now I need to add something like 
> title		Microsoft Windows Vista
root		(hd0,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1 

I am guessing. 

Thanks,Blake

---

### Post by rowanparker on 2006-09-14
It's alright, I gave up on Vista ages ago, thanks anyway.

---

### Post by blake711 on 2006-09-14
ok well after seraching the net some more I found a very simple explination of how the harddrives are addressed along with the partitions.  So I have it all working now and booted into vista as I type this.. 
Thanks,
Blake

---

### Post by rowanparker on 2006-09-14
Well, glad you go it sorted.

---

