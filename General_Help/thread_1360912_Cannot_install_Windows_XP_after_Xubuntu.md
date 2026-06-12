---
title: "Cannot install Windows XP after Xubuntu"
date: 2009-12-21
forum: General Help
---

### Post by stroke on 2009-12-21
Hello,  I installed Xubuntu to try it out (use full disk mode). Then I decided to delete it and install Windows XP again. First, the WinXP install CD returned blank (black) screen after &quot;Inspecting hardware configuration&quot; so I found this solution on ubuntu forums to hide linux partitions. I don't remember the command exactly.  

Then I restarted and it didn't boot into Xubuntu anymore and Windows XP install still got stuck just like before.  

I inserted Windows 98 CD and tried FDISK /MBR but it only returned an empty line and the problem was still here.  

Then I used BartPE and Ultimate Boot CD to run TestDisk but that didn't help either.  

Then I used KillDisk CD to overwrite full HDD with zeros, tried to install Windows and still nothing.  

Now I'm stuck with MBR corrupted I believe and no OS.  

Ultimate Boot CD, KillDisk, Windows 98 still boot normally. 
Windows 2003 Server Edition doesn't even boot, Windows XP still gets stuck or even restarts my computer after "Inspecting hardware...". 

Xubuntu Live doesn't boot it just stucks on "Loding /something/vmlinuz....."Xubuntu install stucks on (initramfs) asking me only to type "help" to see commands.  

Now, is there a way to just use some tool  to fix these issues? All I want is to get my WinXP back. There is no important data to rescue on HDD. I just want to run WinXP install.  

Help anyone? Thanks.

---

### Post by cariboo on 2009-12-22
HAve you tried [Super Grub Disk]("http://www.supergrubdisk.org/") to fix your mbr?

---

### Post by oldfred on 2009-12-22
I would have thought that the blank disk should have worked. But windows would not have seen the ext3 partition left over from Xubuntu.

I would try using gparted from a liveCD and format the first partition to NTFS.

---

### Post by stroke on 2009-12-22
> **cariboo907 said:**
> HAve you tried [Super Grub Disk]("http://www.supergrubdisk.org/") to fix your mbr?

I get three options:

- Boot Ubuntu/GNU LInux returns error "no loaded kernel"
- Auto magic boot gets me back to menu without any error
- Other OS returns error invalid "signature"

> I would have thought that the blank disk should have worked. But windows would not have seen the ext3 partition left over from Xubuntu.

I would try using gparted from a liveCD and format the first partition to NTFS.GParted gets stuck just after I select any option from the menu.

---

### Post by stroke on 2009-12-22
Also tried:

Booting "Partition Magic 8 Boot CD" and I get this error: "Can't load BDOS kernel file."

Booting "OpenSuse" stops at error "Missing operating system".

---

### Post by stroke on 2009-12-22
Problem is solved.

I used KillDisk to erase whole HD again and then followed this tutorial [http://komku.blogspot.com/2008/11/install-windows-xp-using-usb-flash-disk.html](http://komku.blogspot.com/2008/11/install-windows-xp-using-usb-flash-disk.html) to install Windows XP from USB stick.

---

