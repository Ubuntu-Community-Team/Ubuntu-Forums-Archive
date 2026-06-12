---
title: "Unknown keyword in configuration file: gfxboot"
date: 2011-01-12
forum: General Help
---

### Post by Handonam on 2011-01-12
Hey all, I recently got this message when USB booting:

Unknown keyword in configuration file: gfxboot

I used to have the "Unknown keyword in configuration file: ui" problem, which was spread throughout the forum.  I know people have fixed it by removing the "ui" in the config file.  This is what I did in /syslinux/syslinux.cfg


[INDENT]# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
gfxboot bootlogo[/INDENT]


I couldn't find the definitive answer on how to solve this.

I'm using Ubuntu 10.10 Maverick, running on a Foxconn NT-330i (intel atom, Nvidia ION, 4gb Ram, 500GB drive).  I have a DVD reader, however I've been having another error "[Errno 5] Input/output ..." .  I have to run via USB drive.

also, formatted to Fat32, used the usb-creator.exe in the installation disc.

---

### Post by Handonam on 2011-01-12
nobody?

---

### Post by thespacecraft on 2011-01-23
I have the same problem.  What's your hardware configuration?

---

### Post by Eric_imag on 2011-03-19
Hi,

I had the same problem with the same error message.

I created my USB driver with unetbootin instead of usb_creator and now, it works.

I hope it will help,

---

