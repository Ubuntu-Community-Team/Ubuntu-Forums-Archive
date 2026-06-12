---
title: "Cannot move to trash on ext4 partition"
date: 2009-09-28
forum: General Help
---

### Post by hwttdz on 2009-09-28
So I have much of my music and video stored on a separate hard disk, however a user (me) cannot move files to trash from this hard disk.  I get a "Cannot move file to trash, do you want to delete immediately?" when I attempt to delete from nautilus.  I think it may be due to the options that I am using to mount the drive.  Can anyone give me some advice as to what I need to do in order to be able to move files to trash as a user?

---

### Post by hwttdz on 2009-09-28
So a solution I found (at least between restarts), say the drive in question is sda1

cd /media/
sudo chmod 777 sda1
cd sda1
touch example
nautilus .
(delete example & close nautilus)
cd ..
sudo chmod 755 sda1

This allows the os to create the trash directory structure on the filesystem.  I don't know if a restart will somehow break this, but I can't imagine so.

---

### Post by AlexanderDGreat on 2010-09-05
Hey thanks for ANSWERING your OWN question! THIS worked like a charm, as simple as it is.

:)

---

### Post by malapradej on 2011-08-03
> **hwttdz said:**
> So a solution I found (at least between restarts), say the drive in question is sda1

cd /media/
sudo chmod 777 sda1
cd sda1
touch example
nautilus .
(delete example & close nautilus)
cd ..
sudo chmod 755 sda1

This allows the os to create the trash directory structure on the filesystem.  I don't know if a restart will somehow break this, but I can't imagine so.

I have been at it forhours and you provide the solution in a jiffy. I was all into editing the fstab etc.

Thanks a million:D

---

