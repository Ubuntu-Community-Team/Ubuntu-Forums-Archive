---
title: "Boot both Windows partitions from GRUB"
date: 2009-06-29
forum: General Help
---

### Post by itsjareds on 2009-06-29
Hi. I have a tri-boot system with Windows XP, Windows 7, and Ubuntu Jaunty installed on each chronological partition, respectively. GRUB is the boot manager that runs first when I boot up the computer. I have options for Linux, then another option for the first partition. This is my XP partition. But, for some reason, the Windows 7 boot loader seems to be running.

So basically, what happens is:
- Boot
- GRUB appears, then select Windows XP (hd0,0)
- Windows 7's boot manager appears, options are Windows 7 or XP

What I want to know is, can I boot directly into XP from GRUB rather than have to go to Windows 7's bootloader? I don't like how Windows 7 installed over Windows XP's boot manager. I just want GRUB, and I don't want Windows XP or 7's boot loader.

---

### Post by itsjareds on 2009-06-29
Bump

---

### Post by itsjareds on 2009-06-29
Bump :mad:

---

### Post by NikolaiKalashnikov on 2009-06-29
Yep you can usually edit things like that in the bios,but I never really had a problem with the multiple boot managers,because all I really use is Debian or Ubuntu,which I can select from my 1st boot menu anyways.More hassle than it's worth to fix this if you ask me.

---

### Post by louieb on 2009-06-29
> **itsjareds said:**
> 
- Windows 7's boot manager appears, options are Windows 7 or XP

What I want to know is, can I boot directly into XP from GRUB 

The short answer is no. When you installed Win7 it put its boot loader in XP. Thats just the way MS made it. Been that way since the NT days.   
[Understanding MultiBooting]("http://www.goodells.net/multiboot/index.htm") 
[Multi-Booting with Windows in an Extended Partition]("http://www.goodells.net/multiboot/principles.htm")

---

### Post by itsjareds on 2009-06-29
> **louieb said:**
> When you installed Win7 it put its boot loader in XP.

This is why I hate Windows. It rewrites files like this without any confirmation. I still need to use it though for some important programs. Thanks.

---

### Post by itsjareds on 2009-06-30
Found the solution. I had to change some things with Windows's boot manager. Here's the forum thread with the solution I discussed for my problem:

[http://windows7forums.com/windows-7-support/8342-install-bootmgr-two-partitions.html]("http://windows7forums.com/windows-7-support/8342-install-bootmgr-two-partitions.html")

I am the original poster, itsjareds, on that thread. I would mark this thread as solved.. but I can't find the button :-k

---

