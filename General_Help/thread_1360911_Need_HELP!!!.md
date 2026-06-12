---
title: "Need HELP!!!"
date: 2009-12-21
forum: General Help
---

### Post by DTHCND on 2009-12-21
I have been using Ubuntu for a while and just got to a point where I want to install something which requires a 64-Bit OS... :(
 
 The thing is I don't even know why I don't have one since my machine is a 64-Bit machine! :( 

 And since I don't want to lose any of my work I was wondering if there is a way to "upgrade" without having to delete all your files... 

 PLEASE HELP!!!

---

### Post by dagarwal82 on 2009-12-21
you can upgrade from 32 bit to 64 bit ubuntu version

---

### Post by drs305 on 2009-12-21
You can't upgrade from 32-bit to 64-bit Ubuntu directly. A new installation is required.

Do you have enough space to create a new partition and install a second Ubuntu (64-bit) there?

Are the files you want to store on the same partition as your Ubuntu install? If they are not on the Ubuntu install partition, you can use your existing partition to install a new 64-bit version.

Are the files you want to save in your /home folder? If so, you can make/move your /home folder to a new partition and then install the 64-bit version on your existing / partition. Another option would be to transfer your data files elsewhere, install Ubuntu, and copy them back.

If your files are in your /home folder, the best solution would probably be to put /home on a separate partition and reinstall Ubuntu. This will not only save your data files, but most of your configuration files as well. *If you do this, make sure you designate the /home partition during the installation and DO NOT format that partition.*

Here are some links on making a separate /home partition:

[https://help.ubuntu.com/community/Partitioning/Home/Moving]("https://help.ubuntu.com/community/Partitioning/Home/Moving")

[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html]("http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html")

[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by DTHCND on 2009-12-21
Is there someway to backup my data on Ubuntu? Because I have an external hard drive just lying around. (I am thinking of backing up then restoring... Would that work?)|

---

### Post by sanemanmad on 2009-12-21
yes, that will work just fine. where is the data you need to backup located? /home, /mnt/something?

---

### Post by drs305 on 2009-12-21
> **DTHCND said:**
> Is there someway to backup my data on Ubuntu? Because I have an external hard drive just lying around. (I am thinking of backing up then restoring... Would that work?)|

You can copy your data to your external drive - normally it will be automatically recognized when you connect it. 

To give you a better answer, we'd have to know exactly what you mean by 'restoring', and what you want to restore. Give us this information and we can give you a more complete answer.

Data files can be copied and pasted without issue. If you want to copy/restore configuration files it can be a bit trickier. There are methods to record and reinstall your current programs and configuration settings before you begin your installation.

---

### Post by DTHCND on 2009-12-21
By Backup/Restore I mean backup my whole entire / drive, including configuration settings then being able to bring them back latter on.

---

### Post by drs305 on 2009-12-21
> **DTHCND said:**
> By Backup/Restore I mean backup my whole entire / drive, including configuration settings then being able to bring them back latter on.

No, that is not possible for your system files. 
 
You can save your entire /home partition by creating a separate /home partition, doing a clean install, and designating the /home partition and NOT formatting it in Step 4.

You can make a list of your currently installed apps and recreate that list on your new system, via Synaptic.

You can make a copy of your current installation and then selectively retrieve individual files or information stored in them (e.g. *now what did I have in my hosts file?*)  Some of your system files will work but some won't, so a universal import following a clean installation of the 64-bit system won't work..

---

