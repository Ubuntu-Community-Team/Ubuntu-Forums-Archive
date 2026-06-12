---
title: "moving master boot record/grub to new hard drive"
date: 2011-10-13
forum: General Help
---

### Post by carranty on 2011-10-13
Hi,

I have a PC with two hard disks (sda and sdb).  About a year ago I installed Windows XP on sda and then installed Ubuntu on sdb.  1 year later and I've barely used XP so would like to take drive sda out of the computer and put it into another computer (which is in need of a new hard drive).  The problem is, when I take it out and boot up, the computer doesn't find any operating systems (even though Ubuntu is installed on sdb, the one still in).  I don't know much about this area of Linux, but I'm guessing that grub is installed on sda.

Is there a way I can transfer this info to sdb so that I can remove sda without affecting the Ubuntu operating system on sdb? I don't care what happens to the data on sda, I'll be reformatting it anyway once its in the new PC.

---

### Post by ajgreeny on 2011-10-13
So put it back in for the moment and boot up to your ubuntu.  Now when running that ubuntu install use the command ```
sudo grub-install /dev/sdb
``` then try removing the disk again;  it should work this time.

Alternatively,  use the **boot-info-script** link in my signature to download and  run the script, and copy the RESULTS.txt that it produces back here between code tags (the # in  the toolbar above the entry box).  That  will tell us where grub really is, probably sda as you said.

---

### Post by carranty on 2011-10-13
Great, that did the job. Thanks a lot :p.

---

### Post by Mark Phelps on 2011-10-13
Just so you know ... that did not MOVE the MBR from one drive to the other; instead, what it did was INSTALL Grub to the second drive.  Same results, just different process.

---

