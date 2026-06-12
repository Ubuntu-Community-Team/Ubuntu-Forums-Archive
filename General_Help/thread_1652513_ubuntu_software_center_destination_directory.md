---
title: "ubuntu software center destination directory"
date: 2010-12-25
forum: General Help
---

### Post by imransheth on 2010-12-25
Hi
I have windws 7 (Pre installed) laptop. 
I have installed ubuntu 10.10 on my pendrive. I am running ubuntu 10.10 on my Win7 PC using Pen Drive

I want to download few applications from ubuntu software center and I want to download on hard disk .
Is there any way using which I can download on hard disk ?
note : I can access harddisk using file browser.

Regards
Imran Sheth

---

### Post by mcduck on 2010-12-25
Sorry, but not really.

Software isn't installed into any single location on Linux. Instead all the files are put into different places, based on the purpose of the file. So all the executable files go to /usr/bin, library files to /usr/lib, icons to /usr/share/icons, documentation to /usr/share/doc, system-wide configuration files to /etc and so on...

It might seem strange, but once you learn the most common locations you'll find how handy this is, you never need to browse around trying to find a certain file, if you just know what the file is you'll automatically know where the file is located, no mater which package it belongs to.

(while you *could* mount a partition from the hard drive as /usr, which would move fair amount of program files into it, that would require it to be a Linux filesystem. A Windows partition wouldn't work, windows filesysyems lack many features that are required for things to work (like ownerships and permissions as they are used in Linux). So you'd have to create a new Linux partition on the hard drive, and at that point you'd probably find it easier to just install Ubuntu on that partition instead. ;))

---

