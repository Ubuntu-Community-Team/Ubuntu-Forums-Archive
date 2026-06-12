---
title: "windows 7 boots automatically, no option to boot ubuntu"
date: 2012-09-19
forum: General Help
---

### Post by ssojjoss on 2012-09-19
I have just got a new Dell inspiron laptop which comes with windows 7. I wanted to setup up a windows 7/ubuntu 12.04 dual boot system. I used a USB stick which has a copy of ubuntu 12.04 64 and booted from the USB stick. It took me through the installation process (which involved partitioning the hard disk o make room along side of windows). Installation completed and then it restarted the computer.

After restarting, the computer booted straight into windows with no menu with the option of ubuntu or windows like I expected. Can anyone help me boot into ubuntu?

---

### Post by jrog on 2012-09-19
> **ssojjoss said:**
> I have just got a new Dell inspiron laptop which comes with windows 7. I wanted to setup up a windows 7/ubuntu 12.04 dual boot system. I used a USB stick which has a copy of ubuntu 12.04 64 and booted from the USB stick. It took me through the installation process (which involved partitioning the hard disk o make room along side of windows). Installation completed and then it restarted the computer.

After restarting, the computer booted straight into windows with no menu with the option of ubuntu or windows like I expected. Can anyone help me boot into ubuntu?
If your computer is new, it is somewhat likely that it is using UEFI to boot rather than the traditional BIOS. In that case, if Windows is installed in UEFI mode, Ubuntu needs to be too -- otherwise, it will do exactly what it is doing in your case. Have a read here, particularly step #4 of the first four listed steps: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by ssojjoss on 2012-09-20
Thanks this seems likely. However I have looked through the documentation and can't see how to fix my problem. I can't boot into ubuntu to run boot repair (which I think one of the options was). I am fairly new to all this so don't completely understand the terms used (UEFI, BIOS etc) but do you know of a simple way of explaining how to fix my problem? Thanks.

---

### Post by YannBuntu on 2012-09-20
Welcome among us :)

> **ssojjoss said:**
> I can't boot into ubuntu to run boot repair

you can:
1) boot on a [Ubuntu-Secure]("https://help.ubuntu.com/community/UbuntuSecureRemix")-**64bit** disk (which is Ubuntu with preinstalled Boot-Repair),
2) then choose "Try Ubuntu",
3) then run Boot-Repair (click the Ubuntu icon at the top-left corner of the screen, type "boot", click the Boot-Repair icon).
4) Click the "Recommended repair" button
5) tell us the URL that will appear
6) reboot and tell us what you observe

---

### Post by jrog on 2012-09-20
> **YannBuntu said:**
> Welcome among us :)



you can:
1) boot on a [Ubuntu-Secure]("https://help.ubuntu.com/community/UbuntuSecureRemix")-**64bit** disk (which is Ubuntu with preinstalled Boot-Repair),
2) then choose "Try Ubuntu",
3) then run Boot-Repair (click the Ubuntu icon at the top-left corner of the screen, type "boot", click the Boot-Repair icon).
4) Click the "Recommended repair" button
5) tell us the URL that will appear
6) reboot and tell us what you observe
^ That. :)

---

### Post by ssojjoss on 2012-09-20
Thanks a lot for your ideas. It ended up I sorted it out with a really good guide I will leave a link to. Dual boot working perfectly :)

[http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/](http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/)

---

