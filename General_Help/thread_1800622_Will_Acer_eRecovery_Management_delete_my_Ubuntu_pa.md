---
title: "Will Acer eRecovery Management delete my Ubuntu partition?"
date: 2011-07-09
forum: General Help
---

### Post by dhuez on 2011-07-09
I have Ubuntu dual booted with Windows 7 on an Acer Aspire 5736z laptop.  When I start Windows, Acer eRecovery Management appears and gives me two options (summarized below):

1. Complete restore to system defaults.
and
2. Restore the operating system to factory defaults and store my personal files to a backup directory.

Will either of these options fix Windows without killing Ubuntu?  If not . . . any suggestions on how to recover files from my windows partition?

Thanks!

---

### Post by timgood on 2011-07-09
You should be able to mount your Windows partition from within Ubuntu and move over any recoverable files to your Ubuntu HD. 

The Acer Restore Utility may well delete the Ubuntu partition and restore the drive to 'factory'state. I'm not sure about the 'restore os' option, but it may well also reformat the drive.

But at least you should be able to recover any undamaged files from within Ubuntu.

Hope this helps.

---

### Post by Habitual on 2011-07-09
1. Complete restore to system defaults.

To the state it was in when you bought it, or it was sold the the retailer or vendor.

---

### Post by timgood on 2011-07-09
> **Habitual said:**
> 1. Complete restore to system defaults.

To the state it was in when you bought it, or it was sold the the retailer or vendor.

Perhaps you would like to read the original post?

---

### Post by dhuez on 2011-07-09
> **timgood said:**
> You should be able to mount your Windows partition from within Ubuntu and move over any recoverable files to your Ubuntu HD. 

The Acer Restore Utility may well delete the Ubuntu partition and restore the drive to 'factory'state. I'm not sure about the 'restore os' option, but it may well also reformat the drive.

But at least you should be able to recover any undamaged files from within Ubuntu.

Hope this helps.

Yes . . . I think that should be sufficient for me.  I'm not using Windows much, but there are some files I don't want to lose.  

Thanks for the help!

---

### Post by dragonfly41 on 2011-07-09
Have you considered the option of adding an external hard drive through USB?

you can then used gparted to partition the ext hard drive for 

[LIST]
[*]windows backup in one ntfs partition
[*]ubuntu in another partition (preferably extended)
[/LIST]

there is ample advice on this in forum

unetbootin can create a bootable USB drive.

---

### Post by Blasphemist on 2011-07-09
I see a direction that I think this is going. I think you are going to bite the bullet and be Linux 100%. I would too if what I had was Win XP in addition to Ubuntu. And especially with it not working, pitch it is my recommendation.

To start, do boot Ubuntu and copy any file you may want from windows, preferably to an external drive even if that is a usb key. 

Next, you are going to want to make considerable changes to your drive partitions. You may just want to wipe it and start over and that may be easier than deleting, creating and changing partitions. Think it out ahead of time down to diagramming it on paper or the program of your choice. When I finally shrunk windows down and had most of my drive for Linux I ended with 7 distro's installed. I did all of my partitioning before installing anything using GParted.

Before making these changes, back up Ubuntu. I have an external drive that I used to backup windows and Ubuntu. Turned out that good planning kept me from needing either backup, but I had it just in case.

I learned a lot from doing this. I learned about partitioning, grub and boot processes, distro installation and the distro's themselves. You may or may not want to do what I did or need to do that learning but it has been a big help to me.

---

