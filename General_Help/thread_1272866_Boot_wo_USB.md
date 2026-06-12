---
title: "Boot w/o USB"
date: 2009-09-22
forum: General Help
---

### Post by txwooley on 2009-09-22
I installed an ISO image of Backtrack 4 to a 8GB USB drive.  I have Ubuntu 8.04 as my main OS on my laptop harddrive.  Now, I MUST have my USB plugged in to start my comp.  If I don't, it gives me a GRUB error (error code 21) and does not give me a boot menu or option to boot from SDA1 (laptop HDD).  How can I move the main grub to allow to boot from the laptop w/o the USB?

---

### Post by c0mput3r_n3rD on 2009-09-22
Burn a version of grub bootloader and boot from it. See if it shows your OS.

---

### Post by txwooley on 2009-09-22
Not real sure what grub bootloader is.  I still have access to the USB device where GRUB seems to live now though.

---

### Post by txwooley on 2009-09-22
Also, as long as the USB is plugged in when I start my comp, it gives me the option of which OS to boot.  My prob is I want to boot w/o the USB.

---

### Post by ks07 on 2009-09-22
See here: [http://ubuntuforums.org/showthread.php?t=62717](http://ubuntuforums.org/showthread.php?t=62717)

Super GRUB Disk is a fantastically handy tool, I've got one kept with my Live CD for when I get into trouble.

Otherwise, reinstalling GRUB may help you, if you don't feel like downloading and burning the above disk. [See here]("http://ubuntuforums.org/showpost.php?p=121355&postcount=5") to reinstall manually (you may lose your USB boot entry, but it shouldn't be too hard to edit menu.lst and add the entry back). If following that post and using an Ubuntu CD, use sudo grub instead of su then grub.

---

### Post by c0mput3r_n3rD on 2009-09-22
Google grub boot loader if you don't know what it is.

---

