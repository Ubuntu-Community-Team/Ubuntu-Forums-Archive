---
title: "How to Copy multiple .iso files on one CD?"
date: 2009-11-28
forum: General Help
---

### Post by Danial on 2009-11-28
Hi,

Is there a way to copy multiple .iso files (each about 90MB) to once CD/DVD? 

I am not sure if my following approach will work or not, so let me ask first. If I copy all .ISO files (6 in total) to a folder on my HD and than create a CD data project and burn all those in one cd/dvd, will I be able to access (run as iso) all of those iso independently or not? And very importantly, I need access to those files in XP environment [-o<

Your advice and help is very appreciated.

Thanks in advance.

Danial

---

### Post by raktarok on 2009-11-28
Your approach should work fine. And what you burned will be compatible with windows XP, if you use brasero or similar programs. 
Go and give it a try, it should work!

---

### Post by east2idaho on 2009-11-28
If you copy multiple .iso files to a single CD or DVD, then the files will just be seen as files not mounted file systems.  You can mount the .iso files as if they were CDs, but you will have to do this manually - it will not happen automagically.

For instance, under linux if your CD/DVD holding .iso files (e.g., myfirst.iso, mysecond.iso) is mounted as /media/cdrom0, then you would mount the iso files by creating mount points and invoking the mount command as:

mkdir myfirstimage
mkdir mysecondimage
sudo mount -o ro,loopback /media/cdrom0/myfirst.iso myfirstimage
sudo mount -o ro,loopback /media/cdrom0/mysecond.iso mysecondimage

---

### Post by oldfred on 2009-11-28
Some multiboot CD's and some info on how to create:
[http://tazbuntu.blogspot.com/2008/11/multiboot-linux-cd-and-automake-script.html](http://tazbuntu.blogspot.com/2008/11/multiboot-linux-cd-and-automake-script.html)


USB version, I am not sure how to convert for CD.
If you want to boot each:

[http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/](http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/)

---

### Post by raktarok on 2009-11-28
oh danial, are you looking to boot all the isos? I thought you were not...

---

### Post by Danial on 2009-11-28
Thank you much guys... Sorry, I just got back to my putter.

> **raktarok said:**
> Your approach should work fine. And what you burned will be compatible with windows XP, if you use brasero or similar programs. 
Go and give it a try, it should work!

I am getting ready to give it a try.  I have been using K3B (under gnome) and comfortable with it - so I will check that first.

> **east2idaho said:**
> If you copy multiple .iso files to a single CD or DVD, then the files will just be seen as files not mounted file systems.  You can mount the .iso files as if they were CDs, but you will have to do this manually - it will not happen automagically.

For instance, under linux if your CD/DVD holding .iso files (e.g., myfirst.iso, mysecond.iso) is mounted as /media/cdrom0, then you would mount the iso files by creating mount points and invoking the mount command as: ... 

I understand this is under linux only...

[QUOTE=oldfred;8402840]Some multiboot CD's and some info on how to create:
[http://tazbuntu.blogspot.com/2008/11/multiboot-linux-cd-and-automake-script.html](http://tazbuntu.blogspot.com/2008/11/multiboot-linux-cd-and-automake-script.html)


USB version, I am not sure how to convert for CD.
If you want to boot each:

[http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/](http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/)

Thanks for the links, I am going to check this information. 

> **raktarok said:**
> oh danial, are you looking to boot all the isos? I thought you were not...

You are right - I am not booting.  My scenario is that in my office there were some learning CDs and my peers wanted those.  So with the proper permission I brought those home.  When I checked those CDs, I found out that those are ISO files and none of it is bigger than 90MB. Given that fact, if I can compile those in one CD, it will save a lot more CDs and time.  So, in my mind, I want to create a clickable menu and link those ISOs.  I guess, this is a logical approach, practically - I will find out (soon) !!!

Once again, thanks a lot for your guidance and useful help :)

Danial

---

### Post by bluestar14 on 2009-11-28
i'd just burn each one at a time, if i am wrong let me know, but i like your approach

---

### Post by efflandt on 2009-11-28
What you probably need to do is create a directory for each iso, loop mount each to its own directory (so you can see the files in the iso), then web search "create an iso in linux" to see how to assemble that loop mounted content to create one iso with all the contents.  Burn the resulting iso to a CD.

---

### Post by Danial on 2009-11-30
> **bluestar14 said:**
> i'd just burn each one at a time, if i am wrong let me know, but i like your approach

> **efflandt said:**
> What you probably need to do is create a directory for each iso, loop mount each to its own directory (so you can see the files in the iso), then web search "create an iso in linux" to see how to assemble that loop mounted content to create one iso with all the contents.  Burn the resulting iso to a CD.

Okay, here is a partial failure story - :sad:
**I** was unable to find a linux program for CD menu creation.  Brassero/K3B does not offer that particular functionality.  For some good unknown reasons, handbrake does not want to load on Karmic (I know Handbrake does the menus for videos - not sure if that works for other formats) - anyhow, searched and found something for win platform.  Installed a trial version on laptop, after much of reading and frustration, I was able to create and complete the project - successfully tested in virtual drive and all - but when burned the CD, that failed - So, I decide to let go for the moment - As efflandt mentioned, it is looping the same folder (IMHO).  As of now, I don't feel like to sit down and start a VB or dos base menu program and honestly I don't know much in Linux environment.  Another fact is that it is just a temp. project I volunteered for - I will just copy all folders and let them know (in writing) to go into file manager > open desired folder and run setup from there for each individual subject.

I do want to thank all of you for the ideas and help - it is very appreciated and also makes me believe that when in need of help, I am not alone.

Thanks a bunch...
Danial

---

