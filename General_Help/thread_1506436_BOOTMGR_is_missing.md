---
title: "BOOTMGR is missing"
date: 2010-06-10
forum: General Help
---

### Post by genesiow on 2010-06-10
The system worked fine for me until one fine day, when I boot up I get this message:

BOOTMGR is missing
Press Ctrl + Alt + Del to restart

I checked the BIOS to make sure it ran the correct drive first but no go.
I tried reinstall ubuntu but it doesnt seem to work. Anyone got any ideas? 

P.S. I dont have windows running on this machine.

Thanks

---

### Post by genesiow on 2010-06-10
bump

---

### Post by pricetech on 2010-06-10
Don't bump your thread so soon.  Once a day is plenty.

When you boot from the Ubuntu CD, choose the Try Ubuntu option and once it loads run Gnome Partition Editor.  (System - Administration - GParted)  See what it shows for drives and partitions.  That's probably the best place to start.

---

### Post by genesiow on 2010-06-11
/dev/sda - Empty harddisk
/dev/sdb - ubuntu 
/dev/sdc - External HDD

What kind of information am I supposed to look out for ?

---

### Post by WorMzy on 2010-06-11
That looks like a Windows bootloader error. Have you installed Windows recently, or just inserted a disk drive which once had Windows installed? Try entering bios and reordering the disk boot order.

---

### Post by genesiow on 2010-06-11
I figured as much. Windows was in this machine about 4 months ago? until i wiped it out. It was working even without windows. 

My BIOS is set to run sdb first then sda. Shouldnt grub get read and boot ubuntu first ?

Anyway i ran fdisk on a live CD and it shows that sdb doesnt have a * under the boot coloumn. could that be it?

---

### Post by pricetech on 2010-06-11
That would do it.  Any reason you don't have Ubuntu on your first drive ??  Just curious.

---

### Post by genesiow on 2010-06-11
It was originally windows till i got fed up. I bought another harddisk and got ubuntu on it. From there i removed windows. It worked with no problems until recently.

---

### Post by WorMzy on 2010-06-11
Have a look at this tutorial about reinstalling grub to the MBR: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by genesiow on 2010-06-12
Gosh! U people are gods. Fixed my problems with just one sentence. 

Thanks a bunch.

---

