---
title: "original desktop vs new partition desktop"
date: 2010-11-13
forum: General Help
---

### Post by danatcsm on 2010-11-13
I recently created a separate partition for my /home folder, and I copied all the contents of the original home folder into it. I mount it to /home with the "mount /dev/sd3 /home" command. I can cd to the Desktop folder, which contains 30 different files and stuff, but none of them show up on the actual desktop, nor are they visible if I use a file browser to navigate to /home/dan/Desktop. How to I get the items in the Desktop folder on the /home partition to show up on the graphical desktop?

---

### Post by sohlinux on 2010-11-13
did you also change your home location using  admin - users/groups - advanced settings?

---

### Post by danatcsm on 2010-11-13
I am not sure what I should change my home directory to........If the /dev/sda3 partition is mounted to /home, shouldn't the computer treat it just the same as the old attached /home folder? In user settings, my home folder was set to /home/dan. If I mount the partition to a new folder on the desktop, I can browse in it with the graphical file manager, but not if it is mounted to /home. I wonder if it needs to be configured in the /etc/fstab to mount on start?

---

### Post by sohlinux on 2010-11-13
make a copy of your home files 

use mountmanager or manually add the new drive to your /etc/fstab

then boot up and move the files to your new home, you cant have 2 home folders

---

### Post by danatcsm on 2010-11-13
I used mountmanager to edit the fstab, rebooted, and it worked! All my stuff on the desktop is back, thanx, sohlinux!

---

### Post by sohlinux on 2010-11-14
> **danatcsm said:**
> I used mountmanager to edit the fstab, rebooted, and it worked! All my stuff on the desktop is back, thanx, sohlinux!

glad to hear it :)

---

