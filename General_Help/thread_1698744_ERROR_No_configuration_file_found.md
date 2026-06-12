---
title: "ERROR: No configuration file found"
date: 2011-03-02
forum: General Help
---

### Post by elcocodrilos on 2011-03-02
Hello, I tried to install Ubuntu 10.10 with a USB stick, but when I start the computer with the USB stick I got this:

SYSLINUX 4.02 2010-07-21 CHS Copyright (C) 1994-2010 H. Peter Anvin et al
ERROR: No configuration file found
No DEFAULT or UI configuration directive found!
Boot: _
:confused:
I did a MD5SUM of my .iso file and it say "MD5 Check Sums are the same".

Please, help me.:)

---

### Post by turtle153 on 2011-03-02
Are you sure you've made the USB stick properly? Which program was it?

---

### Post by elcocodrilos on 2011-03-02
I used Universal USB Installer 1.8.3.4 and I'm almost sure that I did it correcly because I fallowed the instruction given here: [http://www.ubuntu.com/desktop/get-ubuntu/download]("http://www.ubuntu.com/desktop/get-ubuntu/download")

---

### Post by turtle153 on 2011-03-02
Have a go at creating the USB again, dodgy sticks/CD are common problems.

---

### Post by elcocodrilos on 2011-03-02
I intalled 3 times Ubuntu on my USB stick, it still doesnt work.

---

### Post by electr0n on 2011-03-13
move the syslinux folder into the boot folder.

---

### Post by elcocodrilos on 2011-03-14
> **electr0n said:**
> move the syslinux folder into the boot folder.

Doesn't work.:(

Someone has another idea?:confused:

---

### Post by electr0n on 2011-03-20
I had the same error and copying the folder into boot worked for me, bcuz my boot folder only had the grub folder and nothing more.
Read this and see if it help.
[http://www.pendrivelinux.com/error-could-not-find-kernel-image-linux/](http://www.pendrivelinux.com/error-could-not-find-kernel-image-linux/)

---

### Post by Script Warlock on 2011-03-20
try unetbootin...

---

### Post by vanwykn on 2011-10-13
> **electr0n said:**
> move the syslinux folder into the boot folder.
I burnt a dvds using two different methods to boot from and got same message each time.  Now what since DVD cannot be edited.?
First method was from Win7 ISO BURN  and second was from UBUNTU  suggested method.
:(

---

### Post by new123 on 2011-10-26
I have same problem booting Lubuntu and had same problem booting Ubuntu and Fedora :/
> **electr0n said:**
> move the syslinux folder into the boot folder.
On my USB there is no syslinux folder.

I used UNetbootin still not work.

---

### Post by Amartel on 2011-12-27
Found the solution here: [http://techie-buzz.com/how-to/syslinux-no-default-ui-error-fix.html]("http://techie-buzz.com/how-to/syslinux-no-default-ui-error-fix.html")
I just formatted my drive in FAT instead of FAT32 and everything worked.

---

### Post by roopeshmicasa on 2012-07-07
The root cause to this system error is FAT32. 
I think your Bios cannot understand FAT32 file system. May be your system is old one. Format the USB with FAT16, or simply FAT file system and then create the usb bootable stick that will definitely work....

If you face any other problem just message and I will get back to you...

---

### Post by oldos2er on 2012-07-07
Please don't bump old threads.

---

