---
title: "Disk Partitioning Help"
date: 2009-11-18
forum: General Help
---

### Post by Dkjones on 2009-11-18
Sorry if this has been covered or is being posted in the wrong section.
 
To start off, I am totally new to Linux. Used Windows for many years, but never Linux. What I am looking to do is install Linux onto the HDD but partition it so it has one partition for the system and another for data. I am also installing Ubuntu Server.
 
Now, I've tried the installation with LVM and I can't seem to figure out how to correctly partition this drive, if that was the right option to choose to begin with.
 
Any positive advice pertaining to this matter would be much appreciated.

---

### Post by RJ12 on 2009-11-18
Well for one thing Ubuntu should guide you through the other pretty easy with partitioning. But you could also use a Gparted CD for a graphical way of partitioning as I believe the server is text based. Ubuntu (and I think every distro) has three partitions that it uses. One swap (like pagefile in windoze), one root (apps go here), and a home directory (your and other users files will go here) but I think the guided way only makes two partitions the Swap and Root (Home is combined in the Root). Its easier to do it your self and set the mount points (someone else can tell you this) as when you reinstall (if something really bad happens) your files stay intact like your config files.


Welcome to the home of Linux

---

### Post by Dkjones on 2009-11-18
So should I reinstall Ubuntu with the selection of Guided  - Use Entire Disk then partition it in the GUI with Gparted?
 
Because like I said, I tried Guided w/ LVM and that didn't seem to do it. From what I've googled, LVM isn't what I am looking for either.

---

