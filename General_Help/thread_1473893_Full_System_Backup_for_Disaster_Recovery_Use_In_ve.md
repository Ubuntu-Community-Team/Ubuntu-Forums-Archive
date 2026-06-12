---
title: "Full System Backup for Disaster Recovery Use In ver. 10.4"
date: 2010-05-05
forum: General Help
---

### Post by scyntax on 2010-05-05
I want to be able to recover from a disaster by simply inserting a CD of my entire system, boot from it, and reinstall my system back to the way it was before the disaster. After much research here, I feel the need to ask this question directly. I apologize if I am duplicating another thread, but as a new user, I find it somewhat difficult locating information.

I have seen references to all sorts of backup software. I am trying to use Simple Backup. Each time I run this utility, it gives me a process ID and then apparently vanishes. I don't see the process running in System Monitor, nor do I see anything recognizable in /var/backups. Perhaps, being as new to Linux as I am, I am simply overlooking something. 

I must say though, that these are the friendliest user groups I have ever seen. It amazes me that so many people are so willing to post long, complicated solutions to someones problem. 

Thank you all.

---

### Post by mikewhatever on 2010-05-05
How do you expect the entire system to fit on a CD? Even a DVD wouldn't be large enough in many cases, which makes such an approach unrealistic. For backing up the entire system, I suggest getting an external hard drive and looking at imaging software, clonezilla, partimage, etc.

---

### Post by mike555 on 2010-05-05
Remastersys will put your whole system on a DVD (unless you have too much movies or pictures) ... 
[http://www.geekconnection.org/remastersys/ubuntu.html](http://www.geekconnection.org/remastersys/ubuntu.html)

---

### Post by Mark Phelps on 2010-05-05
You should check out clonezilla.  On their website, they have instructions for how to create a set of recovery disks -- which appears to be what you want.

I've NOT used clonezilla to recover using DVDs, but I have read about folks using other SW to do such recovery and be prepared to spend a lot of time swapping DVDs. To try to do this using CDs is simply insane.  It's better to use an external drive or a large USB stick.

---

### Post by scyntax on 2010-05-05
Perhaps my choice of backup media is incorrect. The concept however, remains the same. I do have an external USB SATA drive which appears to be a better fit for what I want to do. Also, perhaps backing up the entire system is not the way to go either. I would assume there are certain folders that contain all the unique settings I have made. I could back them up on a regular basis and just do a fresh install of 10.4 then overlay all the unique settings files. Would this be a better approach? Are there many folders containing these unique settings or just a few?

---

### Post by perspectoff on 2010-05-05
> **mike555 said:**
> Remastersys will put your whole system on a DVD (unless you have too much movies or pictures) ... 
[http://www.geekconnection.org/remastersys/ubuntu.html](http://www.geekconnection.org/remastersys/ubuntu.html)

Geekconnection got hacked. Remastersys is still available on Sourceforge, though.

The problem with Remastersys is that it creates a LiveCD and installs from that.

It is quite useful (and easy to use) for simple systems. However, I have a complex system with many background processes running, and when I back up the entire system with Remastersys, it attempts to run all the processes from the LiveCD as well as do an installation (which is not possible without a swap partition in order to extend memory capability). There is often just not enough RAM available to do both (since a LiveCD must do everything using only RAM).

A LiveCD remastering tool (like Remastersys) is therefore not the best way to back up a complex system for this reason.

I have tried Partimage and Clonezilla, and both back up the partition equally well. Clonezilla does more than Partimage, but has some quirks (like a wide array of saved files whose purpose is a little mystical.) If the generated partition image file (.iso) is greater than 4.5 Gb, though, it will not fit on a DVD. Both Partimage and Clonezilla are able to split an .iso image into parts, but AFAIK neither is not able to restore those split parts unless all the parts are within a single directory on a single medium (kind of defeating the reason for splitting them in the first place). Neither program can detect (and therefore does not prompt for) image segments on separate DVDs.

FSArchiver seems like a nice solution, although it cannot accommodate GRUB and MBR settings nor partition information (which usually is not a problem). It stores files, not the blocks of a partition. 

I have not figured out the split and restore capabilities of FS Archiver, though. My impression is that it will prompt for additional parts when they are stored on several CD/DVDs, though.

---

### Post by perspectoff on 2010-05-05
> **Mark Phelps said:**
> You should check out clonezilla.  On their website, they have instructions for how to create a set of recovery disks -- which appears to be what you want.

I've NOT used clonezilla to recover using DVDs, but I have read about folks using other SW to do such recovery and be prepared to spend a lot of time swapping DVDs. To try to do this using CDs is simply insane.  It's better to use an external drive or a large USB stick.

Insane? A DVD costs 20 cents. An 8Gb USB stick costs $20. Who's insane?

While a USB stick might be fine if everything is in house and small scale, if you have to send copies of the backup elsewhere (especially for cloning or archival purposes), a USB stick is insane. Far too expensive.

---

### Post by scyntax on 2010-05-06
Does anyone know which folders I should back up that contain all my system settings? That way I could do a reinstall then copy the settings folders over and end up with my old installation.

Thanks to everyone for responding.

---

### Post by J.G. on 2010-06-01
> **scyntax said:**
> Does anyone know which folders I should back up that contain all my system settings? That way I could do a reinstall then copy the settings folders over and end up with my old installation.

Thanks to everyone for responding.


This may not be the best way to do exactly what you are expecting but allow me to give a run down of how I keep my system in place.
Firstly I have all my documents, photos and what not in a separate partition> I deleted all my home folder directories and replaced them with bookmarks in the "places" section which point to the documents etc on the other partition.  The reason I do this is because I am more interested in simply backing up my system files with skype etc installed.  I also add a line at the end of the profile.ini file for thunderbird to access the one on the windows partition.  Saves me wasting space by not having two separate account folders for it.

Next I copy the system partition which is only about 7 gib onto both a DL DVD and a seperate partion on the HD using Gparted by simply choosing to copy the partition.

After that I create a bootable sd card with the grub backed up on it with the fstab file for reference on it.    (Saves me having to do it again if things go haywire)

In the event that I need to "backdate the system" I simply boot into the other partition or copy all the files from the dvd back into the original partition.

Just incidentallym if you are wishing to run a dual boot system for the first time and are worried about messing up the windows MBR, (assuming you have a sd card slot to boot from), when installing ubuntu for the first time on step 6 select "advanced" and direct the boot/grub loader to be installed on the sd card and boot from there each time you wish to run ubuntu.   It will not slow the system down.  Perfect of you wish to run ubuntu in the office without other novices knowing.  Simply insert your "private" SD card in and you are away..

---

