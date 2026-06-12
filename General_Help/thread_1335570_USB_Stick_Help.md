---
title: "USB Stick Help"
date: 2009-11-23
forum: General Help
---

### Post by bower4311 on 2009-11-23
Alright, I understand you receive a lot of these, and I did a search but I kept seeing conflicting ideas. I want to make this as simple as possible. 

I have a 2GB stick that currently has 9.04 installed as what I believe is a live CD version. I used a program and from windows I used the iso to install ubuntu to my drive. 

I am using it get around my schools firewall. Student firewalls are windows based so alternate OS's get around the main one, enough for me to do a project without every other website getting blocked. 

Problem is, I want to keep some files on it from open office and I also need to install flash player to use some websites. I'm not quite sure how to go about this when it comes to splitting the drive and allowing space to be used for files. 

I need to save files and save settings so I don't get reset every time I use my drive. 

I don't mind if I have to start over, I was just wondering if there was any way to do this while in windows or ubuntu from the drive. 

Also, from reading the other ones, I don't want my USB to be destroyed, from the writing but if it's the easiest way that is not a big problem. 

Thank you

---

### Post by t0p on 2009-11-23
I assume that at the moment the entire drive is just one big partition.  You'll need to make another partition.  So then partition 1 will have the Ubuntu live cd image on it; and partition 2 will be for the files you want to keep.

You can use Gparted to repartition the drive. (But you have to unmount the drive in order to partition it - so you'll need to do it on a computer that has Ubuntu on it.  Or you can use a Windows computer that has partition editing software.)  First of all you need to resize the partition that contains the live disk image - shrink it down.  This will leave you with some unallocated space.  So then use Gparted to make that unallocated space into another partition.

As you want to (I assume) use files in both Ubuntu and Windows, format the partition to something like fat32 that can be read by both OSes.

---

### Post by bower4311 on 2009-11-23
Can I obtain a free partitioning editing software online?

Also, will this allow me to save files and small programs on ubuntu?

---

