---
title: "URGENT: Vista &amp; Karmic Dual boot just installed; Not showing Vista at startup"
date: 2009-12-21
forum: General Help
---

### Post by emigrant on 2009-12-21
hi all,
just installed MS Vista and then ubuntu karmic.
but at startup the system directly goes to ubuntu.
how to solve this please? im in friends house advocating them to use ubuntu side by side with linux :(

thank you very much.

---

### Post by drs305 on 2009-12-21
> **emigrant said:**
> hi all,
just installed MS Vista and then ubuntu karmic.
but at startup the system directly goes to ubuntu.
how to solve this please? im in friends house advocating them to use ubuntu side by side with linux :(

thank you very much.

In Ubuntu, run "sudo update-grub". Sometimes Windows is not picked up on the initial install but running the above command will normally find it. Watch the terminal as the command executes and see if it finds Windows.

Grub 2 is designed to boot directly into Ubuntu if it doesn't find another OS, which is what is happening in your situation. Hopefully running the command will pick it up and on the next boot you will see the Grub 2 menu and both systems.

---

### Post by emigrant on 2009-12-21
thanks for your quick reply.
it doesnt show the windows :(

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin

```

---

### Post by drs305 on 2009-12-21
Probably the quickest thing to try next is to make a custom menu entry for your Windows partition.

Open /etc/grub.d/40_custom for editing:
```


gksudo gedit /etc/grub.d/40_custom

```
Windows is normally on the first or second partition of the first drive (sometimes the recovery partition is first. Grub 2 counts the first drive as 0, the first partition as 1). So if your Windows install is on sda1, the root address would be (hd,0,1).
Add this:
> 
menuentry "Windows" {
set root=(hd0,1)
chainloader +1
}

Save the file and update grub:
```

sudo update-grub

```
Reboot, see if the custom Windows entry is visible, and try it.

If it just automatically boots to Ubuntu without seeing a menu, reboot and hold down the SHIFT key as the computer boots to display the menu. We can then tweak the menu timeout settings if necessary.

---

### Post by sanderj on 2009-12-21
> **emigrant said:**
> thanks for your quick reply.
it doesnt show the windows :(


Make sure you didn't wipe Windows with "sudo fdisk -l /dev/sda"; it should show something wiht NTFS and/or FAT. If there's only ext3, ext4 and/or swap, your Windows is gone.

See the example output below of my netbook with WinXP on it

```
sander@quirinius:~$ sudo fdisk -l /dev/sda

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa6e508e7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         784     6297448+  12  Compaq diagnostics
/dev/sda2   *         785       10059    74495096    7  HPFS/NTFS
/dev/sda3           10059       12694    21168328+   7  HPFS/NTFS
/dev/sda4           12695       19457    54323797+   5  Extended
/dev/sda5           12695       19175    52058601   83  Linux
/dev/sda6           19176       19457     2265133+  82  Linux swap / Solaris
sander@quirinius:~$ 


```

---

### Post by sanderj on 2009-12-21
PS:

the GUI method to check for a NTFS/FAT partition (with possibly Windows on it): System -> Administration -> Disk Utility.

See screendump

---

