---
title: "Ubuntu has no disk space left?"
date: 2011-09-03
forum: General Help
---

### Post by raptorzx on 2011-09-03
I just installed Ubuntu today, before that my primary operating system  was XP, which is still on this computer. After quite a few checks, my  computer has about a 230GB hard drive, which about 25GBs are used up on.  So i have a lot of room left. But Ubuntu (10.04) tells me that I only  have 38 MB left on the whole comp in an error message and it will not  download anything. But when checking my disk space with the Disk Usage  Analyzer program, it shows the correct amount (~200GB left).
here is a screenshot of the error message: [http://www.flickr.com/photos/65957665@N06/6108257336/](http://www.flickr.com/photos/65957665@N06/6108257336/)

I posted this question on Yahoo answers, (got no responses) but since then I tried to repair some game or piece of software I was downloading from their Software Center, which probably filled up the rest of the space (It didn't even end up repairing it). So now it says I have zero bytes left. Also it may help that when I installed Ubuntu (got 10.04 from their website) I selected 3GB download as opposed to what the preselected one was (15GB), and I think the max one was 30GB. I was just thinking fast, so maybe it only gave this OS 3GB of disk space total? I would take a screenshot of my disk usage analyzer, to show that it has 200GB left on the comp, but this OS has 0 bytes of disk space left. Also I tried deleting stuff from this (but all I put on it was the screenshot and a game [which won't uninstall]), and deleting stuff from the XP system on this computer. Please help!

---

### Post by Old_Grey_Wolf on 2011-09-03
Did you install using WUBI?

---

### Post by WorMzy on 2011-09-03
Run these commands and post the output here:
```
sudo du -hxd 1 / | sort -h
```

```
df -h /
```

---

### Post by raptorzx on 2011-09-03
The first one results in it asking for my password (which I type in correctly) and then it says:
du: invalid option -- 'd'
Try `du --help' for more information.

The second code results in:
Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0            2.7G  2.6G     0 100% /

---

### Post by raptorzx on 2011-09-03
No, I don't think so, and I don't know what it is anyway. But I can't download anything from the Software Center because I have no disk space left and it keeps giving me a message about trying to repair something (which it can't do because there is no space).

---

### Post by michaelb28 on 2011-09-03
EDIT: My post (below) may not be relevant. From the information above, it looks like Ubuntu is installed on a loopback device, maybe using Wubi? I was assuming a partition scheme.


From your post, it sounds like when you installed Ubuntu, you made a 3 GB partition for it.  That is rather small for a full Ubuntu install. I believe the minimum requirement is 5 GB. I'd go for 10 - 30 GB depending on how much space you have available.

One option you can pursue is to boot from a Ubuntu Live CD and use the GParted (Gnome Partition Editor) to resize your Windows partition somewhat smaller and then use the remaining space to make your Ubuntu partition larger. I think this utility will show up on the drop down menu under System. Before you do this, you should backup your files to an external drive or other media, because there is a chance of data loss.

You can read documentation for GParted at [http://gparted.sourceforge.net](http://gparted.sourceforge.net)

When you use GParted, you'll need to determine which partitions are which.  The Windows partition will probably show a filesystem listed as NTFS. For Linux, it will probably show Ext4 with a mount point of '/', assuming you only created one partition for your Ubuntu installation. You may also see a small partition called linux-swap and possibly one with a mount point of /boot.

As suggested above, I'd try first making the Windows partition smaller and then making the Ubuntu Ext4 partition larger (the one with the '/' mount point). If GParted works correctly, it should be able to do this without destroying data. However, there is always the possibility of an error, so please backup your hard drive first.

---

### Post by raptorzx on 2011-09-03
Do you think I can just remove Ubuntu and choose a 10 or 15GB partition for it when I reinstall it? (I don't have any files at all stored on Ubuntu, so I think that would be pretty easy to do)

---

### Post by michaelb28 on 2011-09-03
I think we need to first determine if you did a Wubi install. Wubi allows you to install Ubuntu when you already have Windows installed on your computer, and you don't want to go to the trouble of changing the partition sizes of your drive. It creates a virtual partition that is stored within the Windows drive.

Within Windows, go to the Add/Remove Programs dialog in the Control Panel. See if there is an entry there for Ubuntu.

If there is, then I think you have a Wubi install. I haven't ever used Wubi, so you may wish to confirm this with someone who has more experience on the subject.

If you don't have any data in the Ubuntu install you wish to keep, it looks like it is pretty simple to uninstall it, and then reinstall with a larger virtual partition.

You can see this page to read about Wubi:

[https://wiki.ubuntu.com/WubiGuide]("https://wiki.ubuntu.com/WubiGuide")

And here about uninstalling it:

[https://wiki.ubuntu.com/WubiGuide#Uninstallation]("https://wiki.ubuntu.com/WubiGuide#Uninstallation")

---

### Post by WorMzy on 2011-09-03
Thanks for letting me know that Ubuntu's version of du doesn't support the -d flag. I'll bare that in mind for future topics. For now though, it looks as though we've identified the problem anyway. You've installed Ubuntu using Wubi (basically, you've installed Ubuntu inside Windows), and didn't create a big enough virtual disk during the installation procedure.

This guide will show you how to create a bigger virtual disk and transfer Wubuntu over to it: [https://wiki.ubuntu.com/WubiGuide#How_do_I_resize_the_virtual_disks.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_resize_the_virtual_disks.3F)

Although, personally, I recommend that you install Ubuntu to it's own partition.

---

### Post by raptorzx on 2011-09-03
Okay, thanks for your help. I uninstalled Ubuntu (the Ubuntu folder was in my C: drive, I just stumbled upon it, and there was an "Uninstall" program within it, so I just did that and reinstalled it with a 30GB partition this time. I guess I did use WUBI the first time (and again this time). Now everything is working correctly.

---

### Post by Old_Grey_Wolf on 2011-09-04
> **raptorzx said:**
> Okay, thanks for your help. I uninstalled Ubuntu (the Ubuntu folder was in my C: drive, I just stumbled upon it, and there was an "Uninstall" program within it, so I just did that and reinstalled it with a 30GB partition this time. I guess I did use WUBI the first time (and again this time). Now everything is working correctly.

It appears that what is asked in post #2 turned out  to be correct. Sorry I wasn't able to finish helping you. I injured myself falling down the stairs at my home and was unable to use my computer yesterday. One of my grandchildren left something on the stairs that caused me to slip and fall. Could you mark the thread as solved?

Thanks.

---

