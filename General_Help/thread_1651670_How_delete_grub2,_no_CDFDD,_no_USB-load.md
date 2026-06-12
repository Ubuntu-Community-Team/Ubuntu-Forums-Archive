---
title: "How delete grub2, no CD/FDD, no USB-load"
date: 2010-12-23
forum: General Help
---

### Post by vital2013 on 2010-12-23
I have old laptop without CD (already it's dead), FDD was not from the beginning. This laptop have USB but can't load from USB.  I install grub2 but it's work not correct. It boot system only 1 per 3 times. Don't show text correctly - sometimes I saw black squears & not letters (only in this f*g grub2; why developers don't made normal uninstaller?).

---

### Post by oldfred on 2010-12-23
Welcome to the forum.

What are you trying to do? Just about any install or repair requires you to boot something. If hard drive does not boot then you need CD, floppy or USB. The only other choice is to remove hard drive and plug into another system where you can then work on it. 

If you can boot one time then you may be able to do some repairs from inside Ubuntu, but if you do it wrong then you will not be able to fix it without booting a repair disk.

---

### Post by vital2013 on 2010-12-23
Right now I just want compleatly uninstall grub2. I have no ability put out hdd and plug it to other comp.  I can load ubuntu. It's just happen not each time when I want it.

---

### Post by oldfred on 2010-12-23
You have to have something in the MBR to boot. If you remove grub2 then nothing will boot.

If you have a windows install you can use a windows repair CD to install the windows MBR. Without CD you cannot use windows repairs. You also need the windows CD to run chkdsk as windows will need that eventually. Ubuntu automatically runs its fsck every 30 boots.

You can install a window like boot loader to the MBR, but you have to have a working windows install with the boot flag. Again unless you do it just right, you will not be able to boot at all.

---

