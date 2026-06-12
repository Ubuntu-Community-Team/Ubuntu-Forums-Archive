---
title: "Adding windows xp to grub"
date: 2009-07-05
forum: General Help
---

### Post by acid_18 on 2009-07-05
how can i add windows xp to the grub loader?

the output of the[COLOR=Red] sudo fdisk -l[/COLOR] command is:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbadcbadc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18679   150039036   83  Linux
/dev/sda2           18680       19456     6241252+   7  HPFS/NTFS
john@john-desktop:~$
```please help

---

### Post by DeMus on 2009-07-05
> **acid_18 said:**
> how can i add windows xp to the grub loader?

the output of the[COLOR=Red] sudo fdisk -l[/COLOR] command is:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbadcbadc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18679   150039036   83  Linux
/dev/sda2           18680       19456     6241252+   7  HPFS/NTFS
john@john-desktop:~$
```please help

In which order did you install your operating systems? First Windows and then Ubuntu? In this case the Windows item should have been added automatically.
First Ubuntu and now Windows. This will destroy Grub since Windows thinks it is the only OS in the world and rewrites the MBR of your disk, the place where Grub settles.

---

### Post by DeMus on 2009-07-05
> **acid_18 said:**
> how can i add windows xp to the grub loader?

the output of the[COLOR=Red] sudo fdisk -l[/COLOR] command is:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbadcbadc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18679   150039036   83  Linux
/dev/sda2           18680       19456     6241252+   7  HPFS/NTFS
john@john-desktop:~$
```please help

Add this at the end of the menu.lst file.
Open a terminal (Application > Accessories > Terminal) and type:
```
sudo gedit /boot/grub/menu.lst
(type password)
```
at the bottom of the file add the following text:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP Professional x64 Edition [COLOR="Red"](change title to your version)[/COLOR]
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1
```

Save the file, quit it, close the terminal and reboot.
Now the Windows item should be inthe Grub menu when you boot.

---

### Post by acid_18 on 2009-07-05
first i installed ubuntu then Windows xp 
then i did this

root (hd0,0) 
setup (hd0) 
 quit 

to restore the grub and now windows is gone

---

### Post by DeMus on 2009-07-05
> **acid_18 said:**
> first i installed ubuntu then Windows xp 
then i did this

root (hd0,0) 
setup (hd0) 
 quit 

to restore the grub and now windows is gone

You can log in into Ubuntu? Ok, then do what I wrote in my second post.
This should work.

---

### Post by merlinus on 2009-07-05
+1

But if it still does not work, use gparted to remove the boot flag from sda1 and activate it on sda2.

---

### Post by acid_18 on 2009-07-05
its worked!
thank u

---

