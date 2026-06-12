---
title: "broadcom wireless"
date: 2010-05-16
forum: General Help
---

### Post by 2roombas on 2010-05-16
When I had ubuntu 9.10 on my laptop, I had to do this to get my wireless to work.

[INDENT]1) Open Synaptic Package Manager
2) Ensure 9.10 LiveCd is in CD drive
3) Settings > Repositories > Ubuntu Software
4) Check the installable from cd and close
5) Refresh
6) Search for "bcmwl-kernel-source"
7) Mark for installation,  Install it
9) Reboot computer[/INDENT]

That worked perfectly, but now that I just fresh installed lubuntu, my wireless is gone again.:( So I looked up in my notes and tried those above steps, but this time there is no check-box to install from a CD. In fact, it doesn't seem to even recognize one is inserted at all.  All it says is "To install from a CD-ROM or DVD, insert the medium in the drive." It says this whether the CD is inserted or not. So with the CD inserted I proceeded to searchefor bcmwl-kernel-source. Nothing like that is found.

How can I get my wireless back?

---

### Post by Hman242 on 2010-05-16
I had a laptop that if I installed an OS without being connected to the internet via ethernet cable, it wouldn't work right including the Broadcom Wireless. Since it's a fresh install, you should try reinstalling it while connected to the internet.

---

### Post by StuartN on 2010-05-16
> **2roombas said:**
> 6) Search for "bcmwl-kernel-source"

I think you are supposed to be able to add your installation CD as a software source, but it seemed far easier to just connect using an ethernet cable to install the Broadcomm drivers. Everything runs fine for me once it is installed.

---

### Post by 2roombas on 2010-05-16
> **StuartN said:**
> I think you are supposed to be able to add your installation CD as a software source, but it seemed far easier to just connect using an ethernet cable to install the Broadcomm drivers. Everything runs fine for me once it is installed.

OK, thank you both....  I'll just do that. That's easy enough to do.:)

---

