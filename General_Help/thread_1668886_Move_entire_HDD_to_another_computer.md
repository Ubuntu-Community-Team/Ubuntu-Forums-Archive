---
title: "Move entire HDD to another computer"
date: 2011-01-16
forum: General Help
---

### Post by zhelev81 on 2011-01-16
Can i move the entire HDD with the installed 64 xubuntu from one computer to another.

Will it be any problems ,i use the os system just to run my game servers.

Extra is lampp and some Databases ...

will it intsall drivers automacicaly .

I just want to know if its possible to do it ,

thank you

---

### Post by Spr0k3t on 2011-01-16
If the architecture of both systems are compatible with each other, you shouldn't have any problems other than extremely minor issues.  You might have to reconfigure your network... or it may need to have some restricted drivers installed manually (through the additional drivers interface).  Outside of that... have at it.  I've moved a primary drive of mine through eight different computer systems just to test how compatible it might be.

---

### Post by zhelev81 on 2011-01-16
so if the hardware is different it may not work or it will work but i have to install the drivers again ,one of the machines have amd and the other have inter processsor 


both 64 bit ,ram is different 


so how about this ? will it work ?

---

### Post by efflandt on 2011-01-16
As long as both processors can do 64-bit, it does not matter if they are AMD or Intel.  And as long as the RAM is suitable for the computer it is in, that is not an issue.

The only thing that might make a difference is if you have proprietary video drivers installed and the other computer has totally different video (like ATI vs Nvidia).  Unless they have similar video hardware it would be best to uninstall proprietary video drivers and use default video drivers when switching it between computers.  Then if you need special video drivers you can activate them.

I use bootable USB hard drives on various computers.  When I got an SSD (solid state drive) I used my laptop to initially install Ubuntu to it and then switched the SSD to my desktop without any problems.  It was sda on the laptop and is sdb on the desktop, but it has grub on it and I currently boot my desktop from it.

---

### Post by zhelev81 on 2011-01-17
oki thankx i will try and get back here :)

---

