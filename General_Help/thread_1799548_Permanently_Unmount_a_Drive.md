---
title: "Permanently Unmount a Drive"
date: 2011-07-07
forum: General Help
---

### Post by TheNEScollector on 2011-07-07
Hey! I'm brand new to the world of Linux. I'm running both Ubuntu 11.04 and Windows XP Home Edition. I have my hard drive partitioned with 90 GB for Windows and 60 GB for Ubuntu. Here's the problem: When I booted up Ubuntu for the first time, the Windows file system appeared as a second HDD. My dad told me that I need to make it so that drive doesn't appear or be read only or else he will be uninstalling Ubuntu because of the risk that some program will write to the Windows file system. I personally am not worried about that happening, but he clearly is. Remember, I'm brand new to Linux so please make things simple for me to under stand! Thank you so much!

---

### Post by Theredbaron1834 on 2011-07-07
Type in a command line "gksu gedit"
Open /ect/fstab (you can try opening it via command line, but I have trouble with that))
delete the line that has your windows partition, I would guess SDA1

And leave the things that look like this:
proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID=f3be5834-6fe2-43f9-a69f-d984860a63ca /               ext4    errors=remount-ro 0       1
/dev/sda3 none            swap    sw              0       0

At least, that is mine. If you don't know what one, just post it and someone here could help.

---

### Post by TheNEScollector on 2011-07-07
And that will still make Windows able to boot on start up? As long as I still have the option to run Windows, then I am more than happy. But I just want to be sure before I delete anything.

Edit: I don't have a folder called ect. But I have etc. Is that what you meant?

---

### Post by Theredbaron1834 on 2011-07-07
O, yeah. Fstab is used as linux is loading to tell it what to mount. Doesn't mess with windows at all.

Or, now that I think about it, you could change it so that the windows partition mounts, but is read only. So nothing can write too it, but I would ask your dad if that is alright first. Again, one of those doesn't really matter, can't hurt anything really things, but ask first, best not to get him angry.

O, I didn't see you post, sorry. 
It is /ect/fstab. The / is your root directory. When you press open in gedit, click the Places called "Filesystem" That takes you to the root dir, then ect is right there.

O, god, and I just got what your ment. Yeah, etc. /le sigh. Didn't get enough sleep last night. :)

---

### Post by TheNEScollector on 2011-07-07
So I opened up Fstab and I got this:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=4445d3fe-2ac2-4527-9c1a-4c24d3115cbd /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=fd72a8aa-d16c-41ab-91ab-03c188c7162d none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

I can't tell which one is Windows :(

---

### Post by rbc on 2011-07-07
As Theredbaron1834 pointed out, the fstab file specifies which partitions are mounted (made accessible) at startup, and how they are mounted. Installing Ubuntu shoudn’t have made an entry for Windows in that file. So unless you did something extra, there shouldn’t be one there to delete. I agree with redbaron assessment, the easiest thing to do would be to have that partition mount read-only. Have a read here, and post back with questions:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by Theredbaron1834 on 2011-07-07
Well, um, none as far as I can tell. Proc is Proc, so not that.First real one is your buntu drive, second one is your swap partition, and third I believe is a floppy drive. Have to wait for some other help, sorry, Not sure.

Um, Open up Gparted and tell me what drive windows is on, something like SDA1 SDC3, ect.

---

### Post by TheNEScollector on 2011-07-07
Sorry, not to sound like a total n00b here, but what is Gparted? :confused:

---

### Post by WorMzy on 2011-07-07
```
Windows file system appeared as a second HDD
```

Yeah, it will do that. It isn't mounted though. It just appears there so that, if the need arises, you can mount it with a single click. Unless you manually mount it (e.g. by clicking on it) there is no chance of an application accidentally writing to it. (Not that there's any chance of that happening in the first place anyway).

---

### Post by Theredbaron1834 on 2011-07-07
gParted is a graphic frontend to parted, a partition editor. Since you are new, it might not be installed, not sure if they have in installed in a new ubuntu. It is my favourite partition editor/formatter. But, just incase, can you try restarting, seeing if it really automounts?

O, yeah, Wormzy is right, open up nautilus up first, and see if there is an eject icon next to your windows drive. If not, it isn't mounted.

---

### Post by TheNEScollector on 2011-07-07
Figured it out!!! Yay! Thanks you guys! I will be coming back soon to bug you all with more questions :)  Thanks again!

---

### Post by Theredbaron1834 on 2011-07-07
:) Have fun.
O, and nice name. :)

---

