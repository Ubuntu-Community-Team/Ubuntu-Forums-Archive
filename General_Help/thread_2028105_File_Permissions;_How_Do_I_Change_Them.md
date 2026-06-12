---
title: "File Permissions; How Do I Change Them?"
date: 2012-07-17
forum: General Help
---

### Post by Smallwheels on 2012-07-17
I'm using 10.04 LTS. I have an external hard drive that has files from Windows XP, Mac OS X, and Vista. I use the program called Mac Drive that allows this format to work on Microsoft computers. I bought it to transfer my files from XP to the Mac when I switched away from Windows in 2008.  

I have used the drive lately to save files from the Mac. It is connected to my Ubuntu computer sometimes. Ubuntu can recognize it and read all of the files. I want to do house cleaning on the drive using Ubuntu but can't delete any files. It says I'm not the owner of the files. When I click on the tabs in the properties box it says root is the owner of the files. 

How do I change this? I'm weening myself away from the Apple computer and using Linux more and more. Eventually I want to make the switch permanently. One part of this process must involve me being able to take control of the files on the external hard drive via Ubuntu. Please help me. This is probably simple for experienced people but I just haven't learned how this is done or if it can be done. Thank you.

Smallwheels

---

### Post by OM55 on 2012-07-17
The default mount of the drive miunts it as having 'root' the owner. So one option is to launch Nautilus as root:

sudo nautilus

or 

gksudo nautious

and then navigate to the folders/files you want to remove.

The other option is simply to moubt the drive with you user as the owner. You can do that in the /etc/fstab file by adding to the mount line the parameter (david is an example of a user name):  

useid=david

This will mount the drive with you as the owner and consequently you would be able to delete files/folders without any special permission.

Let me know if you need the format of the line in /etc/fstab and I'll poet it here too.

---

### Post by Smallwheels on 2012-07-17
One thing I probably should know before doing this step; will this affect the way the drive interacts with my other computers? Right now the drive works perfectly with the Mac and the HP running Vista.

---

### Post by OM55 on 2012-07-17
> **Smallwheels said:**
> One thing I probably should know before doing this step; will this affect the way the drive interacts with my other computers? Right now the drive works perfectly with the Mac and the HP running Vista.

One way or the other this is reversible. If there is any problem with the other machines, simply go back to the original settings and consider a different way.
However, I don't think there would be any problem since I guess it is an NTFS formatted drive (right?) so Windows can natively access it. So you wont have any permission issues with any other systems simply because they do not support that level of drive access. Linux does...

---

### Post by Smallwheels on 2012-07-17
Windows can access the drive because it uses Mac Drive 7 which is a program on Windows that allows it to access a drive formatted for the Mac platform. 

Is there a way to make this change on all files and folders at the same time or must it be done for each one? I want to delete a folder with numerous files. I don't want to be prompted to change the permission for each one. 

On my Mac I wanted to delete some files in the Trash. The process was halted due to individual Brother printer files being locked. The Mac command to unlock all the files in the Trash failed. I had to open each one and change the status to unlocked. That took a long time. Only then could I delete them.

---

### Post by OM55 on 2012-07-17
The mount option I suggested is done once, to mount the entire drive. You definitely do not need to do that for each file or folder. As long as you mount the drive when you (your user name) is the 'userid', then your user will have owner permissions to the entire drive and you will be able to do what ever you want with the files and folders in that drive.

---

### Post by trooperchix on 2012-07-25
> **OM55 said:**
> T

The other option is simply to moubt the drive with you user as the owner. You can do that in the /etc/fstab file by adding to the mount line the parameter (david is an example of a user name):  

useid=david

This will mount the drive with you as the owner and consequently you would be able to delete files/folders without any special permission.

Let me know if you need the format of the line in /etc/fstab and I'll poet it here too.

How do you mount the drive with me as the owner?  I'm a bit inept in terminal.  I do love my Ubuntu system though.  :)

---

