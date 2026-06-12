---
title: "how to make folders display as in windows?"
date: 2010-09-13
forum: General Help
---

### Post by dirtyburger on 2010-09-13
hi everyone!

new ubuntu user here, and i feel 100% comfortable with it now other then command line :P

i love it, feels better then windows, and im in awe at how fast it boots

i have 2 gripes only, that im hoping can be fixed!

is there anyway to make ntfs hidden fils hidden again?

i have a storage partition that i use on windows, and now ubuntu, the problem is theres all sorts o wierd ****

like "system voume information, RECYCLEBIN-O1" and wierd crap like that

its usually hidden in windows, but visable and clickable in ubuntu

is there some way to hide these fils and folders? i think windows needs them, but they look so bad and ruin my folder organization :(

and also, is there some way to have my stoarge partition always mounted? each time i restart i lose my music library in rhythembox, and have to redirect it to my music folder on my stoarge drive.

thanks! i love ubuntu other than these 2 littl quirks, any help is appreciated! :p

---

### Post by Jesus_Valdez on 2010-09-13
I use something called "pysdm" (I installed it via Synaptic) to configure the automount of my windows partition. Maybe there's a better option, but this work perfect to me as it comes with an easy GUI.

As you may know the hidden files and folders in Ubuntu have a "." as a prefix before their name, so why don't just try rename those folders and see if nothing brakes in windows.

---

### Post by dirtyburger on 2010-09-13
> **Jesus_Valdez said:**
> I use something called "pysdm" (I installed it via Synaptic) to configure the automount of my windows partition. Maybe there's a better option, but this work perfect to me as it comes with a easy GUI.

As you may know the hidden files and folders in Ubuntu have a "." as a prefix before their name, so why don't just try rename those folders and see if nothing brakes in windows.

thx for the advice, unfortuntly i nearly lost my system to that program lmao

i clicked some wierd crap in it, and restarted no boot menu just

no bootable sata

lucky went into boot options and picked the harddrive and fixed it

now i uninstalld it and its auto mounting all 3 of my partitions :P

anyway to get rid of this, i just want one partition mounted, my storage partions, not my windows 7 and my windows 7 reserved

thx

---

### Post by dirtyburger on 2010-09-13
help please

---

### Post by WorMzy on 2010-09-13
To hide those folders, you can create a new file in the same directory as them named ".hidden"

Inside this file put the names of the folders you don't want to see, one per line. When you next refresh the window, those files will be hidden. Press Ctrl+H to show hidden files. The .hidden file will also be hidden, so you may need to press Ctrl+H to make it visible to be able to edit it.

As for automounting a partition, you just need to create an entry for it in fstab. Read this: [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by MooPi on 2010-09-13
You can edit your /etc/fstab file to mount or not the partition on boot.

---

### Post by dirtyburger on 2010-09-14
> **WorMzy said:**
> To hide those folders, you can create a new file in the same directory as them named ".hidden"

Inside this file put the names of the folders you don't want to see, one per line. When you next refresh the window, those files will be hidden. Press Ctrl+H to show hidden files. The .hidden file will also be hidden, so you may need to press Ctrl+H to make it visible to be able to edit it.

As for automounting a partition, you just need to create an entry for it in fstab. Read this: [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

i messed up my system so bad with that tool i downloaded earliar in thi thread, i dont think automated mounting is worth it!!!

its not that big o a deal to click storage whenever i wanna listen to music so ill jut deal with it

im interested in this .hidden idea, i know that "." in front of the folder or file name makes it hidden in ubuntu, but how exactly to i add the names of the folders into a empty folder?

**wont dragging system volume information and $RECYCLE.bin make the drive unusable in windows??!!!**

thanks!

---

### Post by Jesus_Valdez on 2010-09-14
It says to create a empty file, not an empty folder, you can create it with gedit.

---

### Post by dirtyburger on 2010-09-14
wow thanks!!!!

now ubuntu is perfect for me!

and maybe in the future whne im more confient with command lines i can auto mount my storage partioton, but really going to places > storage takes all o .5 o a second pretty much a non issue

all my problems are solved thanks so much everyone!

i just love that you get so much support here, for free as well as everything for free!!!!!

---

