---
title: "internet problem in ubuntu 12.04"
date: 2012-06-04
forum: General Help
---

### Post by Needicla on 2012-06-04
hello i have a usb called tenda wireless network since my wired connection doesn't work, it's a usb that when you insert it a program gets installed automatically, its called tenda wireless network aswell, and that way i can connect to my router, but now in Ubuntu it doesn't work, please help

---

### Post by uylug on 2012-06-04
Does it not get detected?

Post the output of:
```

lsusb

ifconfig -a
```

---

### Post by Needicla on 2012-06-05
you dont quite get the problem

my usb is working at windows
but not working at ubuntu

im posting those stuff in windows, and i cant just copy and paste the output from ubuntu to windows.

---

### Post by zombifier25 on 2012-06-06
Just fire up Ubuntu, type those commands, copy and paste the output into a text file, come back to Windows and post the result.

---

### Post by Needicla on 2012-06-06
this is actually starting to **** me off, what will i get as an advantage when i just save a text file in ubuntu?
It wont like automatically go to windows

ubuntu and windows are 2 separate things, i need to shut down windows to go to ubuntu, and shut down ubuntu to go to windows

---

### Post by Mark Phelps on 2012-06-06
It's most likely working in Windows because, when you insert the USB, it is auto-running some Windows program.

Ubuntu can't DO THAT!

So, there will be some effort involve to find out what needs to be done to get it working in Ubuntu.  And, a lot of that effort will be on your part, providing details to help diagnose and fix the problem.

This is NOT going to be a point-and-click solution.

---

### Post by Kr0nZ on 2012-06-06
boot ubuntu,
type commands
save output to file
mount windows
save file to windows hardrive

to mount your windows,
You will need to know what your windows hardrive is (sda1,sda2,sda3,etc)
Then you need to type (I used sda2 as an example replace with yours)
```
sudo mount -t ntfs /dev/sda2 /mnt
```
this will mount your windows harddrive to /mnt

---

