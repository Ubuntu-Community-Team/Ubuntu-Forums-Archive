---
title: "Restoring image to a larger partition"
date: 2012-06-02
forum: General Help
---

### Post by Cpierce on 2012-06-02
I am a huge fan of Ubuntu, and have converted so many of my friends and family. Instead of doing a fresh install each time, I have used Clonezilla or ReDo to make a backup image. I then restore the image to the new larger hard drive. 

The issue I have is that the image doesn't use the entire disk. I have used gparted to try and expand the partition to the entire disk, but it won't let me. I can make it smaller, but not bigger. 

I read about a "-k" extension in Clonezilla, but don't know how to use it. I would prefer to use gparted after the restore if I could.

How can I do this ?

---

### Post by wilee-nilee on 2012-06-02
> **Cpierce said:**
> I am a huge fan of Ubuntu, and have converted so many of my friends and family. Instead of doing a fresh install each time, I have used Clonezilla or ReDo to make a backup image. I then restore the image to the new larger hard drive. 

The issue I have is that the image doesn't use the entire disk. I have used gparted to try and expand the partition to the entire disk, but it won't let me. I can make it smaller, but not bigger. 

I read about a "-k" extension in Clonezilla, but don't know how to use it. I would prefer to use gparted after the restore if I could.

How can I do this ?

Post a screenshot of gparted of the HD that wont expand.

---

### Post by traditionalist on 2012-06-02
> **Cpierce said:**
> I am a huge fan of Ubuntu, and have converted so many of my friends and family. Instead of doing a fresh install each time, I have used Clonezilla or ReDo to make a backup image. I then restore the image to the new larger hard drive. 

The issue I have is that the image doesn't use the entire disk. I have used gparted to try and expand the partition to the entire disk, but it won't let me. I can make it smaller, but not bigger. 

I read about a "-k" extension in Clonezilla, but don't know how to use it. I would prefer to use gparted after the restore if I could.

How can I do this ?

You might like to try this instead;

[http://www.remastersys.com/](http://www.remastersys.com/)

brilliant software.

---

### Post by Cpierce on 2012-06-02
Wilee- nilee, I will post a pic as soon as I can. The computer I am playing now is a mac restore. Would that make a difference ? I experience the same issues with the Ubuntu restore. 

traditionalist, That looks very promising for my Ubuntu image, but I am concerned about the 4gb limit. Most of my complete installs are larger than that. I do like that it blacklists the video drivers and omits the personal info. very cool. 

I still think there is something in gparted that I am missing.

---

### Post by traditionalist on 2012-06-02
> **Cpierce said:**
> Wilee- nilee, I will post a pic as soon as I can. The computer I am playing now is a mac restore. Would that make a difference ? I experience the same issues with the Ubuntu restore. 

traditionalist, That looks very promising for my Ubuntu image, but I am concerned about the 4gb limit. Most of my complete installs are larger than that. I do like that it blacklists the video drivers and omits the personal info. very cool. 

I still think there is something in gparted that I am missing.

That is the maximum size of a DVD image, not the maximum size of data. The set up is compressed.  My present extremely extensive setup only uses 2.1 GB on a DVD.

That is the complete system with all programs, setups etc, but with no data.

---

### Post by Cpierce on 2012-06-03
Here is the picture of the drive on gparted:

[http://www.flickr.com/photos/mcp4416/7328269966/in/photostream](http://www.flickr.com/photos/mcp4416/7328269966/in/photostream)

---

### Post by ezsit on 2012-06-03
> but I am concerned about the 4gb limit

Regarding Remastersys:

This only applies if you include your /home folder with all your files in the BACKUP mode. Backup your data files SEPARATELY and use the DIST mode to backup the system. 

Using Remastersys correctly, your DIST mode remaster will probably never reach the 4GB limit and you restore your data files later, after re-installation of the system. 

Tips:
1. Make sure to use the same, exact username during re-installation and you will not encounter any permission issues when restoring your data files. If your /home directory is in its own partition (like it should always be), DO NOT format the partition during re-installation.

2. While using the Remastersys live system, just before beginning the reinstallation, mount your /home/username directory and delete all the . (dot) files and folders except your .mozilla folder. This ensures a clean re-installation and avoids any weird settings problems. However, you will need to re-set all your configuration options (desktop, wallpaper, login options, etc.,) after re-installation. Remember to unmount the /home/username directory before beginning re-installation.

3. Always put your /home folder in its own partition, separate from /.

4. Never leave the auto-login setting enabled before using Remastersys in DIST mode, it will always mess up your Live system.

5. Install Bleachbit before using Remastersys and clean the system immediately before creating the Remastersys DIST mode backup.

This method preserves your system and your data more safely than backing up your entire system in one huge image file. 

Re-installation on friends and family computers is safer in that their installs do not inherit ANY of your personal settings or information. 

This method also gives you a live system with all your downloaded software intact, something a clonezilla backup can never accomplish.

Lastly, you never have to worry about partition re-sizing ever again.

---

### Post by Cpierce on 2012-06-03
Ezsit, Thank you for the tips. I will have to give that a try.

But I would still like to know how to expand the partition once I do a restore with Clonezilla or redo. I tend to have multi-boot systems and this work well. I just need to learn how to resize the partitions. It's like the restored image gets locked to a certain size.

---

### Post by Cpierce on 2012-06-09
bump

---

### Post by Cpierce on 2012-06-14
Any help on this ?

---

### Post by jonnyboysmithy on 2012-07-28
The partition can't be in use when you resize it.
Boot off a livecd/liveusb and try to resize the partitions, should work then.

---

