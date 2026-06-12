---
title: "How can I create a full system image backup within ubuntu ?"
date: 2011-07-31
forum: General Help
---

### Post by ahmadka on 2011-07-31
Hi all ... Well I've decided to move all my data from one VPS to another, and I wanted to know if there was a way from within Ubuntu to make a full system image backup, which I can then just transfer to the new Ubuntu VPS, and restore it there ...

Unfortunately my VPS control does not have any working backup option right now, so I can only make the backup manually from within Ubuntu, if there is a way to do it ...

So does someone know who can I do this from within Ubuntu ?

---

### Post by tigerlxxv on 2011-08-01
Others may correct me if I'm wrong, but for a full-system backup, I don't believe there's a built-in facility for this. I've had good luck with Clonezilla, though. That is a free download, and will take a full system image, if you ask it to do so, and IIRC it has the ability to span across multiple CDs/DVDs without much fuss.

---

### Post by Megaptera on 2011-08-01
I use Remastersys to create ISOs of my system and burn to DVD for backups, having transfered the ISO to an external drive. Quaint and perhaps old fashioned I know but it works for me!

[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

---

### Post by ahmadka on 2011-08-01
The Ubuntu machine I want to backup is a remote VPS, and so I cannot burn CDs/DVDs on it ..

The only thing I can do is create the backup, and then upload it somewhere, which I can then download from the new VPS ..

So is CloneZilla easy to use, and will it make a full system image, that if restored, will restore the compute to the *exact* same state as before ?

---

### Post by tigerlxxv on 2011-08-01
I found CloneZilla to be pretty easy to use, and you should be able to take a snapshot of the system, just like Windows System Restore, or what have you. Here's the site: [http://clonezilla.org/](http://clonezilla.org/)
Natrually, you'll want to test it to make sure it does everything you need it to, before counting on it... You never know when you might forget to check something.

---

### Post by whitethorn on 2011-08-01
I don't know if it's possible to do a backup of /root while it's running usually the best way is to start a live cd and then run the backup. Probably the best way to do what you want is to get a list of installed programs, save your settings, /home /root /var /etc and maybe /opt . Then on the new VPS install ubuntu copy over all the settings reinstall the programs and done. The program I'd use to copy all the files would be rsync over ssh.

---

### Post by ahmadka on 2011-08-01
Well I read CloneZilla's limitations, and I found this:

> Online imaging/cloning is not implemented yet. The partition to be imaged or cloned has to be unmounted.

Since I don't have physical access to the VPS, I obviously cannot switch it off and then run the backup ...

So whatever backup scheme I use, it has to support Online backing up mechanims ..

---

Okay I understand that taking a complete system backup may be difficult while the system is online, but is it possible to at least take snapshots of specific software installed, so that I can restore the complete state of that software in the new machine, so that the software thinks nothing has happened ..

Simply fresh installing the program I have in mind will not work as its configuration would have to be done from scratch, which I want to avoid ..

---

### Post by aeiah on 2011-08-01
i think rsync can backup everything. it isnt as simple as copying everything from the root level recursivley though - you need to leave out /proc, /dev etc. there should be a howto or something though.

really though, wouldnt it be best just to back up your data and apache config files?

---

### Post by Spitfire1900 on 2011-08-15
> **ahmadka said:**
> Well I read CloneZilla's limitations, and I found this:



Since I don't have physical access to the VPS, I obviously cannot switch it off and then run the backup ...

So whatever backup scheme I use, it has to support Online backing up mechanims ..

---

Okay I understand that taking a complete system backup may be difficult while the system is online, but is it possible to at least take snapshots of specific software installed, so that I can restore the complete state of that software in the new machine, so that the software thinks nothing has happened ..

Simply fresh installing the program I have in mind will not work as its configuration would have to be done from scratch, which I want to avoid ..
True that, I am working on a backup command similar to what is found here that could allow you to quickly restore your system by installing scratch Ubuntu then extracting a backup tar to root.

[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

---

### Post by Duncan Williams on 2011-08-15
This method may work. I tried it out and it created a directory with everything onboard in deb format. You then reinstall your distro from livecd and use the directory (which can be copied to another machine/partition to rebuild your current setup:
[http://ubuntuforums.org/showthread.php?t=819396](http://ubuntuforums.org/showthread.php?t=819396)

---

### Post by bodhi.zazen on 2011-08-15
Wow, this thread got off topic fast, people this is a VPS, not a Desktop.

1. First you probably do NOT need an image, just back up the data. Depending on what you are running, for web sites, this is often php config files, /var/www , apache config files, and a mysql database.

2. Second, you can easily back up your full VPS, but it sort of depends on what VPS you are using. openvz ? LXC ? Xen ? 

For openvz there is vzdump.

If all else fails, you can use tar.

[http://wiki.openvz.org/Debian_template_creation#Preparing_for_and_packing_template_cache](http://wiki.openvz.org/Debian_template_creation#Preparing_for_and_packing_template_cache)

---

