---
title: "Question: are these bugs?"
date: 2006-03-08
forum: General Help
---

### Post by Kapitan on 2006-03-08
First of all.

I have a notebook with a Turion 64-bit.
I've downloaded and installed ubuntu-5.10-amd64.

Installed...since from start i've seen it would be
so easy...

I have an optical USB mouse plugged into his port,
and i've tried to install ubuntu...on kernel loading the error was:

CPU 0 Machine Check Exception: 4 Bank 4 b200000000070f0f
TSC 498a5b6f5c
kernel panic - not syncing Machine check


I've unplugged the USB mouse and the install goes on.
Installed all. launching gnome...no problem.Even plugging
the USB mouse now works. 
But if i plug on boot...first that kernel loads...kernel panic!

Go on....
Go on synoptic to install packages,after inserting my user psw
the synaptic window doesn't work.
So i've logged into root account and i've launched /usr/sbin/synaptic:

Gtk+ warning **: cannot open display:

All root programs doesn't work! I've tried disks-admin and other,
both into normal user and root.

Someone has the same problems?

---

### Post by Jason_25 on 2006-03-08
First, you should never need the root account in ubuntu.  Read this: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

Does your bios have an option for toggling legacy usb?  You might give that a try.

---

### Post by Kapitan on 2006-03-08
The problem is that even with gksudo /usr/sbin/synaptic
the problem is the same...nothing starts.

No i have not the legacy usb mode on my bios.

---

### Post by Kapitan on 2006-03-09
noone? It's only my problem?

Is not possible, i made the expert installation
without removing nothing critical i think...

---

### Post by mdmarmer on 2006-03-09
Laptops have special problems.  They frequently have proprietary configurations to save space, power, etc.

[http://www.linux-on-laptops.com/forum/](http://www.linux-on-laptops.com/forum/)

[http://www.linux-on-laptops.com](http://www.linux-on-laptops.com)

[https://wiki.ubuntu.com/HardwareSupportMachinesLaptops](https://wiki.ubuntu.com/HardwareSupportMachinesLaptops)

Need to know specific make and model of laptop

Also, it's not uncommon for Xserver to have problems with the root account, since the system is set up to logon to gnome as user, not root. 

Mike

---

