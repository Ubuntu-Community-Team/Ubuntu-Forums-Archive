---
title: "How to Install Ubuntu -- Dual Processor"
date: 2006-05-17
forum: General Help
---

### Post by larry on 2006-05-17
Hi,
For my work I have just been given a new machine, running windows at the present. It is a dual-processor machine with plenty of RAM memory.
I would like to have Ubuntu installed on that and also some advice about how to partition the hard drive (so far I have always just hit enter many times when installing Ubuntu on other PCs).
I was advised to create a partition where to install the OS and another one as home, so that even if I had to reinstall from scratch, that would not affect my data. But I haven't figured out yet how to do it!
These are some data about the machine:
Intel(R)
Xeon(TM) CPU 2.80 GhZ
2.80 GhZ, 2.00 GB of RAM
Physical Address extension

The sysadmin is more experienced with Fedora, so he is pushing me to install that distro, but so far I have had a good time with Ubuntu.
Any suggestions?
Cheers

Larry

---

### Post by Sutekh on 2006-05-17
Do you plan to keep Windows on the PC and dual boot?

Creating a separate /home partition is something I would recommend.  It's not very hard to do this.  During the install, at the partition stage, you need to create two new partitions, one for / and one for /home.  When you create these partitions, you can then choose the mount points for them (/ and /home).

It's not as easy as the Fedora installer IMO, but not too hard.

This link will explain it a whole lot clearer, with screenshots to help out.

[http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

It has a section on dual booting with Windows and creating a separate /home partition.  Good luck.

---

### Post by mozkill on 2006-05-17
yes, there is a way to shrink the windows partition and then add a secondary and a swap partition for your linux distro.  i dont know exactly how though.  Ubuntu is definitely the way to go since after installation you can run that Automatix script that configures all the multimedia stuff for you...  its so much easier than Fedora... :-|

---

### Post by larry on 2006-05-17
[QUOTE=mozkill]yes, there is a way to shrink the windows partition and then add a secondary and a swap partition for your linux distro.  i dont know exactly how though.  Ubuntu is definitely the way to go since after installation you can run that Automatix script that configures all the multimedia stuff for you...  its so much easier than Fedora... :-|[/QUOTE]

I have heard about the Automatix script, but what is it and what does exactly do?
Cheers

Larry

---

