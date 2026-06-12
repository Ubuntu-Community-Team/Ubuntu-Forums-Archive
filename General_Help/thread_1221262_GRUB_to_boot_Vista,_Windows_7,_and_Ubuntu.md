---
title: "GRUB to boot Vista, Windows 7, and Ubuntu"
date: 2009-07-23
forum: General Help
---

### Post by pwhipped on 2009-07-23
I currently have two hard drives. On the first drive I loaded Vista. On the second drive I partitioned space for Win 7, and then for swap/ubuntu. I installed in that order thinking that GRUB would recognize vista and win 7 separately. On my GRUB menu however, under "other" I have Vista (loader) listed but no win 7. The worst part is, when you select vista, it boots to 7... I know I'll probably get questions regarding why I'm booting vista and 7, but I want to keep it that way. Is there any work around for this? I've tried googling but I honestly haven't been able to find a similar problem. I'm very new to linux as well so my terminal skills are not the best. Thanks for any help ahead of time guys. :)

---

### Post by pwhipped on 2009-07-23
bump :)

---

### Post by merlinus on 2009-07-23
What is the boot order of your hdds?

Also, post results of these commands from a terminal.  Best to copy and paste.

```
sudo fdisk -l
cat /boot/grub/menu.lst
```

---

### Post by intx on 2009-07-23
I had a similar problem. Open your terminal and do:

```
sudo fdisk -l
```


Hopefully you can tell your partitions apart.

Note which sda Vista and Seven are(sda1,sda2 etc)

Now do this command:
```
sudo gedit /boot/grub/menu.lst
```

Find your Vista boot section and edit the root to the correct hard drive and partition(if it's on hd1, sda 2 it would be 0,2)

At the end add a separate one for 7:


```
title Windows 7
root (hdx,y)
savedefault
makeactive
chainloader +1
```


Try that :)

---

### Post by merlinus on 2009-07-23
The OP has vista on one hdd and 7 on another, so map statements will be needed for booting one of these oses.

And FWIW, best to use gksudo for graphical apps.

---

### Post by intx on 2009-07-23
> **merlinus said:**
> The OP has vista on one hdd and 7 on another, so map statements will be needed for booting one of these oses.

And FWIW, best to use gksudo for graphical apps.


Can't you just have the roots different?

For ex, 7 is on HD1 SDA2 and Vista is on HD2 SDA2.


7:

root(0,2)


Vista:

root(1,2)

?

---

### Post by merlinus on 2009-07-23
Windows always wants to be first, so it needs to be fooled into thinking that via map statements.

OTOH, it would not hurt to try your way.

BTW, numbering for these sorts of things begins at 0 (zero), not 1 (one), so sda2 would be (hd0,1).

Also, there needs to be a space between root and the numbers in parentheses.

---

### Post by intx on 2009-07-23
Oh yeah. I forgot.


OP Make sure you read his post :P

Also: This should work as I'm currently dual booting Seven, Ubuntu and Vista(sort of, it's a recovery partition)

---

### Post by merlinus on 2009-07-23
Do you have the three oses on one hdd, or two?

---

### Post by intx on 2009-07-23
Only one harddrive, which might be why your  map statements may be required.

---

### Post by pwhipped on 2009-07-23
I scrapped 7, after I tried editing menu.lst. After rebooting it started spitting out Bootmgr cannot be read or something similar. I repartitioned and reformated. I'm leaving the first drive as a shared drive between ubuntu and vista. This is what I have for fdisk -l.

```

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
224 heads, 19 sectors/track, 459004 cylinders
Units = cylinders of 4256 * 512 = 2179072 bytes
Disk identifier: 0x000a6248

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       43309    92160000    7  HPFS/NTFS
/dev/sda2           43310       61665    39061568   83  Linux
/dev/sda3           61666       65336     7811888    5  Extended
/dev/sda5           61666       65336     7811878+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6c304f05

   Device Boot      Start         End      Blocks   Id  System

``````

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        49fa20f2-7579-44bb-9f15-58d996ec022b
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=49fa20f2-7579-44bb-9f15-58d996ec022b ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        49fa20f2-7579-44bb-9f15-58d996ec022b
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=49fa20f2-7579-44bb-9f15-58d996ec022b ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        49fa20f2-7579-44bb-9f15-58d996ec022b
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=49fa20f2-7579-44bb-9f15-58d996ec022b ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        49fa20f2-7579-44bb-9f15-58d996ec022b
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=49fa20f2-7579-44bb-9f15-58d996ec022b ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        49fa20f2-7579-44bb-9f15-58d996ec022b
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title        Windows Vista
root        (hd0,0)
makeactive
chainloader    +1

```The Vista section I added. I got the BootMgr error again. :( Wtf?

---

### Post by pwhipped on 2009-07-23
bump

---

### Post by merlinus on 2009-07-24
Try supergrub:

[http:///supergrubdisk.org](http:///supergrubdisk.org)

If that does not fix your problem, you can use your vista cd, select restore, and fixmbr and/or fixboot. This works with xp, so the options might be a bit different for vista.

Then you can reinstall grub.

---

### Post by pwhipped on 2009-07-24
I know that I can do that and plan to. However, is that going to fix the problem...? This has happened to me twice in a row now.

---

### Post by merlinus on 2009-07-24
You might have to install bootmgr.exe as well, before restoring grub.  But supergrub might be able to do all of this.

---

