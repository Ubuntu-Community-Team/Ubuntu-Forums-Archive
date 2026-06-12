---
title: "new to ubuntu"
date: 2011-12-21
forum: General Help
---

### Post by alan89mx on 2011-12-21
Hello people from ubuntu forums,

I just installed ubuntu on my computer and can't access that OS, it will automatically load in to windows. I know it's installed because my hard drive is 50gb short. Anyone know what I did wrong or if I need to do something else? 
Thank you.

---

### Post by mikewhatever on 2011-12-21
To know what may have gone wrong, you first need to tell what's been done in more detail. How have you installed Ubuntu (in Windows/separate partitions)? Have you created partitions manually or let the installer do its job? Have you changed any of the defaults in the process?

---

### Post by alan89mx on 2011-12-21
Well, I didn't have my hard drive partition so i let the installer do the job, and i didn't change anything or the defaults. I just ran ubuntu from my thumbdrive.

---

### Post by N00b-un-2 on 2011-12-21
please post the output of 
```
sudo fdisk -l
```
we'll go from there.  I'm guessing you might just have issues with GRUB.  Did you by any chance install Ubuntu using WUBI (Windows Ubuntu Installer)?

---

### Post by QIII on 2011-12-21
Hmmm...  A bit hard to use the Linux terminal without being able to boot to Linux.:D

I think your question about Wubi is the right place to start.  Anything in the terminal will have to be in a live session.

---

### Post by mikewhatever on 2011-12-21
> **alan89mx said:**
> Well, I didn't have my hard drive partition so i let the installer do the job, and i didn't change anything or the defaults. I just ran ubuntu from my thumbdrive.

Please run Ubuntu from your thumbdrive again, and use the [Boot Info]("http://sourceforge.net/projects/bootinfoscript/") script to collect the essential information.

Post the result on [http://pastebin.com/](http://pastebin.com/) or here.

---

### Post by alan89mx on 2011-12-21
I'm using the Universal-USB-Installer 1.8.6.8 to make the image. I have a new partition and it's emty. Everytime a try to install ubuntu on that drive it gives me en error at the end of the installation. I will post the error I get.

---

### Post by alan89mx on 2011-12-21
Here is the error I get    [http://i.imgur.com/zGgcp.jpg](http://i.imgur.com/zGgcp.jpg)

---

### Post by alan89mx on 2011-12-21
I can't run the bootinfo script because I need to have ubuntu installed. That's what I read in the description.

---

### Post by mikewhatever on 2011-12-21
> **alan89mx said:**
> I can't run the bootinfo script because I need to have ubuntu installed. That's what I read in the description. 

No you don't. just boot from the thumb drive and run the script, though, if it was a wubi installation, it won't show much.

As for the installation error, check out the log it tells you to.

---

### Post by alan89mx on 2011-12-21
I got it to work!!
I think the universal-usb-installer had something wrong so I downloaded daemon and used that one.
Everything is working now, just need to do the updates and learn more about Ubuntu.
Thank you guys for all the help.

---

