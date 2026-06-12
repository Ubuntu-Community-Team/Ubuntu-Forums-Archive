---
title: "Live CD and Email Recovery from HD"
date: 2006-02-26
forum: General Help
---

### Post by wthanna on 2006-02-26
I am trying to access information on a drive that will not boot. I have mounted the drive after booting from the Breezy Live CD. I can copy files to a USB drive without a problem. The only thing I would really like to recover now, is the contents of my Evolution Inbox! I can setup Evolution using the Live CD.. no problem..  How can I point the LIVE CD version of Evolution to my old data files so that I can forward the information from my inbox.. or how can I run evolution from the mounted but unbootable harddrive..  probably an obvious and easy answer to this, but it's 2:00 in the morning... I'm somewhat of a newbie.. etc.    ?

---

### Post by alamba on 2006-02-26
Copy .evolution folder in your home directory to an external HDD. If you want to use this data with the LiveCD you could try copying it to the LiveCD user home directory and then launching evolution.

A

---

### Post by wthanna on 2006-02-26
[QUOTE=alamba]Copy .evolution folder in your home directory to an external HDD. If you want to use this data with the LiveCD you could try copying it to the LiveCD user home directory and then launching evolution.

A[/QUOTE]
Worked perfect using the Live CD. Here's what I did:

_Boot Live CD_
[U]
Create mount point for my hard drive by:[/U]

Go to - Applications >> Accessories >> Terminal

Type in Terminal "Sudo Nautilus"

In Nautilus, browse to - File System - Media
Right Click in Folder "Media" and "Create Folder" named hda1

_Modify my fstab file to show mount point and drive by:_

in Terminal, type: sudo gedit /etc/fstab

Add the following line (or whatever is appropriate for your drive): 

/dev/hda1 /media/hda1 ext3

save the file
[U]
Mount the drive[/U]

In terminal, to mount the drive, type:  sudo mount -a

Browse to the drive that is now mounted, to MY home folder
Show Hidden Files
Copy the .evolution folder to the /home/ubuntu folder in the Live CD file system.
Start Evolution and run through the setup wizard
Once Evolution's quick setup wizard is complete, there's my inbox with all of my email.

---

