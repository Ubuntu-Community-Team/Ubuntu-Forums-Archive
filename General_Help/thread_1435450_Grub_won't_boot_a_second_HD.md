---
title: "Grub won't boot a second HD"
date: 2010-03-21
forum: General Help
---

### Post by JuanKawada on 2010-03-21
I have a new installation of ubuntu and when I installed it grub didn't recognize my previous installation of windows 7. 

I installed ubuntu on a 320 GB HD and I have windows 7 installed on a 1TB HD. If I boot directly to the windows 7 HD (through the bios boot menu) I get a flashing underscore and nothing happens (I assume that's because there is no boot loader on that HD)

Sudo fdisk-l outputs this: ```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x724bd9dc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38162   306536233+  83  Linux
/dev/sda2           38163       38913     6032407+   5  Extended
/dev/sda5           38163       38913     6032376   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
240 heads, 63 sectors/track, 129201 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x0007ae9d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      129202   976759808    7  HPFS/NTFS
```

I tried adding this to my grub menu.lst file

```
 title		Windows 7
 root		(hd1,0)
 makeactive
 chainloader	+1
```

but it didn't let me boot my windows partition when I tried to. Any Ideas on what I'm doing wrong?

---

### Post by phen0m on 2010-03-21
If you're running grub2 menu.lst is obsolete.
try running
```
sudo update-grub
```

---

### Post by JuanKawada on 2010-03-21
> **phen0m said:**
> If you're running grub2 menu.lst is obsolete.
try running
```
sudo update-grub
```


I've tried sudo update-grub and it still only recognized the kernels on the 320GB HD, and doesn't recognize windows 7 on the 1TB HD

I also made sure that I mounted the windows 7 HD before running update-grub. 


I'm not entirely sure that I'm running grub2, is there someway I can make sure? I'm running a variant based off ubuntu 9.04 with openbox.

---

### Post by psusi on 2010-03-21
How did you have windows booting before you installed grub?  Windows will not boot from the second disk in the system.  Because of this, if you moved windows to the second disk then installed grub on the first, you have to have grub use the map command to swap the disks around before chainloading windows so it thinks that it is still on the first disk.

---

### Post by JuanKawada on 2010-03-21
Before this I had the windows 7 loader installed on the first HD which I was just using as backup.

How do I use the map command to swap discs?

---

### Post by psusi on 2010-03-21
IIRC it is:

map (hd0) (hd1)
root (hd0,0)
chainloader +1

---

### Post by JuanKawada on 2010-03-21
> **psusi said:**
> IIRC it is:

map (hd0) (hd1)
root (hd0,0)
chainloader +1

I changed the entry to include that, and got "Error 13: invalid or unsupported exe form". 

I looked it up and found advice to change the entry to 

```
title              Windows 7
root               (hd1,0)
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```

Problem is that now I get an error that says "Boot MGR is missing Press ctrl+alt+del to restart"

Does this mean that grub can't manage as the boot loader for windows 7? I really don't know what to do now.

---

### Post by psusi on 2010-03-22
You have to do the map BEFORE root.  Also make sure that your windows partition has NTLDR and BOOT.INI there.

---

### Post by Mark Phelps on 2010-03-22
> **psusi said:**
> You have to do the map BEFORE root.  Also make sure that your windows partition has NTLDR and BOOT.INI there.

This is advice for Windows XP -- not for Win7!

Instead, look for the boot folder and the bootmgr file.  Note that in Win7, these are considered operating system files and are hidden by default.

---

