---
title: "How do i create bootdisk"
date: 2011-03-03
forum: General Help
---

### Post by Bigfatnoob on 2011-03-03
Hi there

How do i create a bootable CD to update my BIOS in ubuntu 10.04

---

### Post by bsntech on 2011-03-03
Ahh.. yes... I had this problem - and boy was it complicated.

You need to basically download the bios flash utility and the bios firmware.  Unfortunately, I have a laptop that dual-boots between Windows and Ubuntu - and I had to use Nero in Windows to create a bootable CD and add those files to it.

Then I was able to boot from the CD, run the bios flasher, and done.

Brian S.
[http://www.bsntech.com]("http://www.bsntech.com")

---

### Post by seawolf167 on 2011-03-04
BIOS will be system board specific - go to the manufacturer's website and search for your particular chipset

i.e. at the [link here ]("http://www.intel.com/p/en_US/support?iid=gg_support-en_US+home_support")for Intel boards, Chipsets -> Desktop Chipsets -> Select Family

You'll then get a list of boards, their drivers, bios, etc. There will be links and how-tos for flashing BIOS, recoverying BIOS, etc.

Most of the BIOS (.bio) files will be system independent that you can boot off a floppy, usb drive or cd (as long as you don't choose the Windows .exe flashing program)

---

