---
title: "Cannot run Ubuntu Customisation Kit"
date: 2010-07-10
forum: General Help
---

### Post by jingaling on 2010-07-10
Hey Guys,

I am trying to create a customised Ubuntu Live CD with a few apps pre-installed etc. I am using the Ubuntu Customisation Kit to try and create this. I have tried to create a CD twice and each time during the creation of the ISO it fails. Below is the log file, could you guys take a look please guys?

Thanks for your help in advance.

Jing

************ LOG FILE BELOW **************

Ubuntu Customization Kit 2.0.12
Starting CD remastering on  Sat Jul 10 21:07:48 BST 2010
Customization dir=/home/kev/tmp/customization-scripts
Removing remastering root dir...
rm: cannot remove directory `/home/kev/tmp/remaster-root/tmp': Device or resource busy
Removing ISO remastering dir...
Mounting ISO image...
Unpacking ISO image...
Unmounting ISO image...
Removing remastering root dir...
rm: cannot remove directory `/home/kev/tmp/remaster-root/tmp': Device or resource busy
Mounting SquashFS image...
Unpacking SquashFS image...
Unmounting SquashFS image...
Removing win32 files...
mount: mount point /home/kev/tmp/remaster-root/proc does not exist
Failed to mount /home/kev/tmp/remaster-root/proc, error=32
mount: mount point /home/kev/tmp/remaster-root/sys does not exist
Failed to mount /home/kev/tmp/remaster-root/sys, error=32
mount: mount point /home/kev/tmp/remaster-root/dev/pts does not exist
Failed to mount /home/kev/tmp/remaster-root/dev/pts, error=32

---

### Post by jingaling on 2010-07-10
Bump!

---

### Post by satyanash on 2010-07-13
hi
 same problem here.. i upon some googling found out that this can arise due to faulty or broken or modified .iso files.. the UCK needs fresh untouched original Ubuntu .iso files.. i checked my files and am very sure that they are fine.. but i still get this problem.. also after running the uck-gui command once.. and closing the terminal after it fails...results in me not being able to open the terminal again.. it shows starting the terminal but nothing happens.. then i am forced to restart the computer..somebody also said that this issue was fixed in 2.0.9 version so i wanted to get teh latest one and found out that i had 2.0.12..

---

### Post by satyanash on 2010-07-13
i also went here [http://sourceforge.net/projects/uck/files/](http://sourceforge.net/projects/uck/files/)
 and downloaded v2.2.1 .deb file and installed but it still gives me the same problem

---

