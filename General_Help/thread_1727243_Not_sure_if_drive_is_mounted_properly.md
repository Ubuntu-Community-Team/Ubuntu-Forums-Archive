---
title: "Not sure if drive is mounted properly"
date: 2011-04-12
forum: General Help
---

### Post by izombie666 on 2011-04-12
I have two drives in my computer.  My C drive handles the operating system and some files.  My D drive is storage for files suchs as music movies and pictures.  I cannot create a shortcut for the D drive. If I want to burn some music for example, I cannot access D drive via Brasero, I have to copy the file to C drive.  I am not sure if there is some I need to do in mount manager.  Any Ideas?

Thanks

---

### Post by Mark Phelps on 2011-04-12
Linux doesn't use drive letters, so "C" and "D" don't mean anything useful here.

To access the data drive, you should go to the Places menu and see entries there.  It won't say anything like "D drive"; instead, it will have different names.  But, when you click the entry, Ubuntu will auto-mount it and open a Nautilus file manager window to it.

You should be able to use that to drag-and-drop your files there.

---

### Post by mikewhatever on 2011-04-12
Why can't you access it via Brasero? In other words, what happens when you try to? Are there any error messages?

---

### Post by izombie666 on 2011-04-12
In "places, this drive is listed as "DATA". When using software like Brasero, DATA does not show up as a source for files.  Also The system will not keep the desk top shortcut.  The next time the computer is started I will get a message that says Link "DATA" is broken.

---

### Post by mikewhatever on 2011-04-12
+1 for drag and drop.

---

### Post by QLee on 2011-04-12
[QUOTE=izombie666]In "places, this drive is listed as "DATA". When using software like Brasero, DATA does not show up as a source for files.  Also The system will not keep the desk top shortcut.  The next time the computer is started I will get a message that says Link "DATA" is broken.[/QUOTE]
In "Places" it isn't mounted until you click on it.

It sounds like what you might want is to have the "DATA" partition (D drive in Windows) automatically mounted when the system boots. That can be accomplished by including a line for the partition in fstab (file system table). With the partition mounted at boot a link to it will survive reboots and programs will be able to find it in the filesystem at the location you specified in fstab. Here are some useful links.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by izombie666 on 2011-04-12
Hey QLee!!!!  Thank You!!!  You helped me fix this nagging issue!!!!!!!   My second drive is opening fine and the system and software is seeing it!!  

"+1 for drag and drop"....What the......?

---

