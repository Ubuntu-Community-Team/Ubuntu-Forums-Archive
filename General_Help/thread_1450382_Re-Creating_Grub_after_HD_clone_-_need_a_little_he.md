---
title: "Re-Creating Grub after HD clone - need a little help"
date: 2010-04-09
forum: General Help
---

### Post by cilbuper on 2010-04-09
I tried to recreate my Grub setup after restoring a backup tar file to a new hard drive.  Here is what I did.  

I created a tar backup of my working 9.10 server install.  I used fdisk to create the same partition structure as the old hard drive:

**sda1** Primary  bootable ext4 (83)
**sda2** Extended
**   sda5**  Linux / swap  (82)

I mounted the new drive with the newly created partitions on the current system and extracted the tar backup to the new sda1 partition.  I then recreated all the directories which were excluded in the tar backup (mnt, media, home, proc, sys, etc).

I then shut down, unplugged the old OS hard drive, plugged the new hard drive into the same cable as the old OS HD and powered it up.  It told me that there was a GRUB error.  

I did some looking around and found that I could use an Ubuntu Live CD to fix/install Grub on that hard drive.  I burnt a 9.10 desktop CD, booted, installed Grub and here I am.  

I am having a difficult time figuring out the GRUB commands.  

This is what I was planning on doing:
```
1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot.
```

The problem is that I don't know what my hd#,# are.  I also don't know how to figure it out.  my boot drive is sda1 if that helps at all.  

I appreciate any help anyone can provide here.  I'm frustrated that I got this far and am stuck!  Thanks!

---

### Post by darolu on 2010-04-09
sda1 = hd0,0

I am not sure that method to restore GRUB will work though, if I recall correctly that installs GRUB legacy, 9.10 uses GRUB2 by default.

Follow this instructions to reinstall GRUB2:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

If your installation does have GRUB legacy (i.e. you upgraded from 9.04) you may try reinstalling GRUB legacy using an older version LiveCD (9.04 or previous), when you run "grub" on your terminal run this command to find out where to install it:
```
grub> find /boot/grub/stage1
```

---

### Post by cilbuper on 2010-04-09
Before you respond, I'm trying the GRUB2 - Installing GRUB from the Live CD section of the link you supplied.  Thanks!
> **darolu said:**
> sda1 = hd0,0

I am not sure that method to restore GRUB will work though, if I recall correctly that installs GRUB legacy, 9.10 uses GRUB2 by default.

Follow this instructions to reinstall GRUB2:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

If your installation does have GRUB legacy (i.e. you upgraded from 9.04) you may try reinstalling GRUB legacy using an older version LiveCD (9.04 or previous), when you run "grub" on your terminal run this command to find out where to install it:
```
grub> find /boot/grub/stage1
```

thank you for the response!  Before you posted, I booted to the LiveCD and tried 
```
grub>  find /boot/grub/stage1
```
and get an Error 15:  File not found.  

I also tried:
```
grub>  root  (hd0,0)
```

I have also looked for the menu.lst file within the original OS install and did not find it.  I was going to make a copy of it and install it on the new HD, but I figured it should have been copied during the backup procedure.  

I looked at this page to find some more info but have not come up with anything:
[https://help.ubuntu.com/community/GrubHowto#Backup,%20Repairing%20and%20Reinstalling%20GRUB]("https://help.ubuntu.com/community/GrubHowto#Backup,%20Repairing%20and%20Reinstalling%20GRUB")

Would doing a DDrescue eliminate the GRUB setup?  I can do all of this with DDrescue instead of restoring from a tar backup.  

The kicker is now that I tried to run the new OS/HD and switched back to the old HD I get a GRUB 15 error and can't boot to the old HD.  I didn't even change anything on it!
Any thoughts?

---

### Post by john newbuntu on 2010-04-09
Now, on the new drive, you used the karmic liveCD.  So, follow step 13 from the following post:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

I am thinking that your old drive had legacy grub and so use the method here to restore it:
[http://stringofthoughts.wordpress.com/2009/05/25/grub-error-15-debianubuntu/](http://stringofthoughts.wordpress.com/2009/05/25/grub-error-15-debianubuntu/)

---

### Post by cilbuper on 2010-04-09
I tried the process here:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")

after I ran this command:
```
sudo grub-install --root-directory=/mnt/ /dev/sdX
``` I got a response that it had been run succesfully and said to check the output of device.map which has been set to:

(hd0)  /dev/sda

I thought that there was supposed to be something like (hd0,0), which identifies the hard drive and partition.  anyway, I left it as is and rebooted.  No luck.  I went through the whole procedure again and then edited the device.map file and changed the (hd0) to (hd0,0) hoping that that might fix it, but I still get the GRUB Error 15 on boot.

On step 6 of the tutorial here: [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202") it says reboot and step 7 is: "Refresh the GRUB 2 menu with sudo update-grub".  I don't know where to do this.  Do I reboot to the Live CD or to the hard drive.  If it is to the hard drive, I can't run step 7 because of GRub Error 15.  

Man this is frustrating!  I apologize for asking so many questions and all help is greatly appreciated!

---

### Post by darolu on 2010-04-09
Lets get some stuff clear first. Boot with your LiveCd, and run:
```
$ sudo fdisk -l
```
Post your results. This would give us a better idea of your hard drives and partitions.

Mount your hard drive, and run:
```
$ cd /media/<yourhardrive>
<yourhardrive>/$ ls /boot/grub
```
Post your results, this should help us to determine what GRUB version you have.

About the "Error 15" you are getting at *grub>* try this (if you indeed are using grub legacy):
```
grub> find /grub/stage1
```

---

### Post by cilbuper on 2010-04-09
> **john newbuntu said:**
> Now, on the new drive, you used the karmic liveCD.  So, follow step 13 from the following post:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

I am thinking that your old drive had legacy grub and so use the method here to restore it:
[http://stringofthoughts.wordpress.com/2009/05/25/grub-error-15-debianubuntu/](http://stringofthoughts.wordpress.com/2009/05/25/grub-error-15-debianubuntu/)


Thanks. I tried step 13 and got to the point of it asking which kernel of Linux I wanted to run.  It gave me 3 options of regular, 3 for rescue adn 2 for memtest.  None worked correctly so I'm giving up.  It is time to just do a fresh install and migrate config files later.  I'll have to come back to this and trouble shoot it later.  

Thanks to everyone who has helped.  I never thought GRUB could be so difficult to get to work!

---

### Post by wilee-nilee on 2010-04-09
If it is grub2 that you have this is a more concise description, go to step 11. This will show you how to identify the partitions and how to mount the one you need,then install grub in the MBR.
[https://help.ubuntu.com/community/Grub2#Upgrading](https://help.ubuntu.com/community/Grub2#Upgrading)

Do you really have the primary ext4 outside of the extended or am I missing something?

Edit: Step 11 is exactly the same as step 13 in the posted grub2 thread, I just noticed.

---

### Post by oldfred on 2010-04-09
When ever you copy the system over you have to reinstall grub and change the UUIDs in fstab to get the system to boot.

You should know the versions you are using.
Grub version
grub-install -v
lsb_release -a
dpkg -l 'grub*'

And if you want lots of detail on boot issues, what is in the MBR and all the info on fstab, UUID and versions, nothing beats the boot-info script:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

