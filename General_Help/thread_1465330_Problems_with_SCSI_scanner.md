---
title: "Problems with SCSI scanner"
date: 2010-04-29
forum: General Help
---

### Post by jebradley on 2010-04-29
My desktop machine is an dual amd64 machine with a Tyan K8SPro motherboard with an Nvidia GeForce 6200 PCI video card and adaptec scsi card. I am running 64bit ubuntu 10.04 (RC+upgrades) using the proprietary Nvidia-current driver.

I recently followed a post that I found to enable use of my epson scsi scanner. This has worked with previous ubuntu releases. 

First, the file, /etc/sane.d/dll.conf, was edited to uncomment #epson  to epson.

At this point, using sudo sane-find-scanner will show the scanner, but will not find it by a "normal" user.

A scanner group was then added, and user added to that group.

The permissions for the scanner were changed with the following commands:
sudo chgrp scanner /dev/sg3
sudo chmod 660 /dev/sg3

The file /etc/udev/rules.d/45-scsi-scanner.rules was created with the following:

# permissions for EPSON ES-1200C SCSI Scanner.
SUBSYSTEM=="scsi_generic",ATTRS{vendor}=="EPSON SC",A TTRS{model}=="ANNER GT-9000",
NAME="%k", SYMLINK="scanner%n", MODE="0660", GROUP="scanner"

Now, this worked in the past, but now, the presence of the .rules file causes the keyboard and mouse to be locked out. I get the gdm prompt, but can't do anything with it.

If I log into my machine via NoMachine's nxclient, I can use the scanner by the user. If I delete the .rules file, I have to sudo xsane to allow usage of the scanner, but on bootup, I'm not locked out. I'd like to be able to use the scanner from a normal user, so I don't have to chown all the files to allow the user to use them, but I'd also like to use my machine from its keyboard and not have to log in remotely.

---

### Post by jebradley on 2010-05-18
I finally figured out the problem. Thanks for all the responses. ;)

The file /etc/udev/rules.d/45-scsi-scanner.rules was the problem.
It should have been all in one line, and the "A TTRS{model} should have been "ATTRS{model}

Everything is working great, now. Hope this helps someone else.

---

