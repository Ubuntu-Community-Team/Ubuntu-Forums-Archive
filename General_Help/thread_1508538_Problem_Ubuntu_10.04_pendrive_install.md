---
title: "Problem Ubuntu 10.04 pendrive install"
date: 2010-06-13
forum: General Help
---

### Post by surge031 on 2010-06-13
Hello everyone,
 
New Ubuntu user here.
 
I am attempting a ubuntu install via a 4GB pendrive. I was able to boot Ubuntu from the pendrive and all seemed well untill it was time for the installer to detect and mount the cd-rom. I got the message "Failed to copy file from cd-rom" but I'm trying to install Ubuntu from the pendrive there is no cd in the cd-rom drive. 
 
I would appreciate any help getting past this stage.
 
Thanks in advance,
surge

---

### Post by _khAttAm_ on 2010-06-13
It means it failed to copy file from the USB Pen drive. It might be corrupt.. get another one.

---

### Post by surge031 on 2010-06-13
I will try that now. Thanks for the quick reply.

---

### Post by cuberts on 2010-06-13
> **_khAttAm_ said:**
> It means it failed to copy file from the USB Pen drive. It might be corrupt.. get another one.Actually, that might not be the case. Can you tell me how you installed it onto the flash drive? Did you use a program, or did you just mount the ISO image on your own?

---

### Post by surge031 on 2010-06-13
> **_khAttAm_ said:**
> It means it failed to copy file from the USB Pen drive. It might be corrupt.. get another one.
 
> **cuberts said:**
> Actually, that might not be the case. Can you tell me how you installed it onto the flash drive? Did you use a program, or did you just mount the ISO image on your own?
 
I used a program called "universal usb installer." I also tried "UNetbootin" and got the same results.

---

### Post by wilee-nilee on 2010-06-13
> **surge031 said:**
> I used a program called "universal usb installer." I also tried "UNetbootin" and got the same results.

Try another thumb or if you have a cd reader burn a cd. Also checking the device at the boot prompt by holding down the shift key after hitting the start up. And also running a md5sum check. I suspect it is the thumb is it a sandisk?
[MD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by surge031 on 2010-06-13
The thumb is 4Gb imation. I do have a cd reader so I will try that. I had just wanted do my installs from a bootable usb instead of having to burn a cd/dvd everytime I need to do an install.

---

### Post by wilee-nilee on 2010-06-13
> **surge031 said:**
> The thumb is 4Gb imation. I do have a cd reader so I will try that. I had just wanted do my installs from a bootable usb instead of having to burn a cd/dvd everytime I need to do an install.

Yeah I like thumbs better myself, some just don't work well, I always use gparted to delete and reload the fat32 partition before loading them though.

---

### Post by C.S.Cameron on 2010-06-13
Check the MD5SUM of the iso.

---

### Post by surge031 on 2010-06-13
I just checked the MD5SUM, they are the same.

---

### Post by Puristaako on 2010-06-15
I have the same problem. Ubuntu 10.04 server, trying with 3 pendrives, create via universal usb installer all downloaded from ubuntu.com. PC is mini-ITX system. 
btw, I was install ubuntu 9.04 on that PC via pendrive and all ok.  But i need 10.04 server now

---

### Post by sireebob on 2010-06-22
I hate to be pessimistic, but this is the kind of thing that makes me lose confidence in Ubuntu and Linux in general.

I'm having the same problem with ubuntu-10.04-server-amd64.iso. MD5SUM is identical to the one on UbuntuHashes. I used the Universal USB Installer as recommended by the install..install guide. Tried it on a new 1GB flash drive, then a completely different brand, tried-and-true 2GB flash drive, the first formatted by the installer, and the second formatted manually by me. Same problem with both, at the same spot. "Failed to copy file from CD-ROM. Retry?" Very annoying... The server doesn't have a very good CD-ROM drive which, along with saving discs, is why I don't want to deal with it.

I rather dislike Universal USB Installer by the way. "Progress will not be updated until the process is complete. Please be patient." Say WHAT? Also took a fairly long time for Bob knows why...

Argh, I'm tired. Shouldn't have expected this to "just work."

Trying this from Win7 x64, by the way.

---

### Post by randomdes on 2010-07-14
Same story here. Mini-ITX system.  Ubuntu server x64 pendrive install.  Md5 ok, recreated and reformatted a couple times.  Keeps failing right after choosing language and keyboard options. "Failed to copy file from CD-ROM".

---

