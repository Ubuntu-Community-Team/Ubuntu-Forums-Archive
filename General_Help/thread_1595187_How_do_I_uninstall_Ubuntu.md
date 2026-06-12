---
title: "How do I uninstall Ubuntu?"
date: 2010-10-13
forum: General Help
---

### Post by trisemigistus on 2010-10-13
I'm not happy with ubuntu. I want to run Windows along side it. I have ubuntu installed and nothing else. I've tried running the windows XP installation disk, Ubuntu refuses to recognize it during start-up, and won't give me permission to run it while logged in on ubuntu.

What do I do?

---

### Post by James78 on 2010-10-13
You can't run a Windows XP disk inside Ubuntu and expect it to actually work. Boot the CD from BIOS, and install it.

Warning: Windows XP will overwrite the MBR, and you won't see Grub, thus not being able to select Ubuntu to start up from, however, there are ways to restore the Grub loader even after installing Windows.

Personally, I'd suggest removing Ubuntu, installing XP, and then install Ubuntu inside XP using Wubi (if you still want Ubuntu that is), that way when you don't want it, removing it is as simple as removing a program from Windows.

---

### Post by HereInOz on 2010-10-13
Or, you can leave Ubuntu exactly as it is, install VirtualBox, and then install XP inside VirtualBox.  So you have the best of both worlds.

---

### Post by trisemigistus on 2010-10-13
Um. What is the BIOS?

I'm running on a Dell, btw. And I've tried having the disk in the tray on start-up, and it won't even recognize that theres a disk in the cd-rom drive during start up. Even if I press f12 and specify to boot from the cd-rom drive.

Edit: Oh, that'd be nice. How do I get this VirtualBox?

---

### Post by HereInOz on 2010-10-13
From here:

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

But if your machine doesn't recognise a bootable CD in the CD-ROM drive, then you are going to have to fix that problem first.

I have been running Ubuntu with VirtualBox and Windows XP and Windows 7 as virtual machines for some time.  It is a great way to test software, as you can take a quick snapshot of the virtual machine, test what you need to test, and if it borks your Windows system, then you just restore from the snapshot and you are back where you were beforehand.

You can even copy the virtual machine to another Ubuntu computer running VirtualBox, and presto - two virtual machines, one on each computer.

---

### Post by trisemigistus on 2010-10-13
My computer recognizes disks when I'm in Ubuntu, but it won't boot from the CD-rom drive during start-up.

Will the upgrade to 10.10 be any interference if I wanted to install the VirtualBox? (currently updating to 10.10 [an hour remaining on the new package download] and want to install the VirtualBox at the same time, would that be a problem?)

---

### Post by HereInOz on 2010-10-13
Wait for the update to finish, make sure all is well, then download the appropriate version of VirtualBox.  Make sure that you get the correct one - either 32 bit or 64 bit.

I don't know how much RAM your machine has, but you will need around 1GB to successfully run XP in a virtual machine.  You would configure the Virtual Machine to have 512MB RAM (more if you have more than 1GB) and set a disk size of at least 10GB for XP.  

The HDD size depends on how much you want to install, and where you are going to put your documents.

I have all my documents on my Ubuntu machine, and share that folder using Samba, and then point the My Documents folder on the XP machine to it.  I don't know what your current knowledge level is, so if this is too much, then ignore this last bit.

You will have some hiccups, in all probability, but once you get it right, it is all good fun.

---

### Post by trisemigistus on 2010-10-13
oh... Well, I only have 512MB of ram, total. My computer is old.

---

