---
title: "Help with mounting fat32 partitions"
date: 2006-05-29
forum: General Help
---

### Post by SaxmanTy on 2006-05-29
Hello,
I'm a newbie and I'm haveing trouble mounting my fat32 partitions from my second hard drive.  I set everything up fine in  the /ect/fstab file.  I have the two partitions showing up exactly where i want them to be when my system boots no problem.
The problem is, I don't have permission to write to SOME of the files and folders.  "SOME" being the key issue and what is cofusing me.  Some folders work perfect, I can read write, exe, everything.  But some others have the lock, and i can only work with them as root.  I tired mounting the partitions by using the "defualt" option, "rw,exec,user,sync" options, and then "iocharset=utf8,umask=000" option. (By the way, all of these options I understand except for iocharset, and umask, help on that would be cool too)  Each set of options had my permmision set different ways for different files and folders, but none of them give full permission for all users for all the files and folders.  What can I do to fix this?  Or is this something I need to fix in windows? Or am I shooting form the hip?  Thanks for you help!

---

### Post by Nonno Bassotto on 2006-05-29
I can't say anything about this, except that I'm having this problem too, and I've not been able to solve it so far. One of the advices I got (but it didn't work for me ](*,) ) was to mount you fat32 partition outside /mnt and /media, say in /Windows.
Let me know if this works for you.

---

### Post by SaxmanTy on 2006-05-29
Nope, thatdoesn't work, because I've never attmempted to mount them there in the first place!  And if you want to really cook the noodle, the place where I HAVE been trying to mount them is my /home/username directory!  That's where I should have permission to do whatever I want right!! I'll join you till someone can help us... ](*,)

---

### Post by randell6564 on 2006-05-29
I have 120GB drive partitoned with HDA1 being widows and HDA2 being ubuntu.

I also have a 20GB slave (Fat32) for storage.  this is what my fstab looks like:

[B]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1 /windows ntfs nls=utf8,umask=0222 0 0
/dev/hdb1 fat32 vfat iocharset=utf8,umask=000 0 0
[/B]

I have no trouble reading/writing to HDB1.  

I read somewhere that with ubuntu, you cannot write to your windows partiton.

Hope this helps!

---

### Post by RRS on 2006-05-29
Follow the instructions [here]("http://easylinux.info/wiki/Ubuntu#Windows") and you should have no problems.

Even though ownership may be shown as Root in properties you should still be able to read/write Fat32 files and read NTFS. You can also copy from NTFS to Fat and then write to them there but not vice-versa.

Edit; typo, and also in reference to randell6564, writing to windows(ntfs) is not currently supported in Linux but their are a couple experimental methods being used with some success but the emphasis is on experimental.

After following the instructions in my link your fstab's should appear similar to randell6564s' guy's. 

Let us know if it works for you.

---

### Post by turbojugend_gr on 2006-05-29
Well first of all, I strongly recommend to both of you to mount your fat32 partition as /winux or /windows or something like that. As for your problem it is propably caused cause some Windoz Appz are changing the permissions to your folders. Most commonly I believe them to be anti-virus apps and others of that family.
I can think of 3 approaches, ---1st try to set those apps not to do so (if you are admin in your XP system that should not be tricky - though I can't define anything specific...) ---2nd try to make less use of windoz (that should be a really good approach) ---3rd try to write down a shell script for changing those permissions and run it at start up) the last should be difficult but not beyond your abilities. Shell scripts are routines of terminal commands that are  executed by just starting the script.

Be sure before doing anything to check this: change the permissions at your needs, restart to XP and back to ubuntu to see if permissions are changed... if not that shouldn't be the case...

Another idea is to change all those permissions through WINDOWS and allow anyone to read,write,execute and REMEMBER to allow those permission to be set for all the SUBLFOLDERS and FILES inside them (you should get asked for that). Then try again to see if your permissions stay as you wish them to...

Notify me with your progress.

---

### Post by aysiu on 2006-05-29
Post your /etc/fstab file, and we'll help you out.

---

### Post by Nonno Bassotto on 2006-05-29
RRS, I've already done that, in fact I can r/w my fat32 partition. But, alas, some directories at random make an exception.
turbojugend_gr, fat32 filesystem does not allow to set permissions; in fact you have to mount the whole partition with the same permissions scheme. :( . In windows permissions don't even exist afaik, so I don't believe windows apps affect them.
Aysiu, here is my /etc/fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       /home           ext3    defaults        0       2
/dev/hda1       /media/Windows  vfat    iocharset=utf8,umask=000 0 0
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```
I may mention I had the same issue with Breezy. I have made a fresh install of Dapper and the problem is still here :(

---

### Post by aysiu on 2006-05-29
Try this: ```
sudo umount /dev/hda1
sudo mkdir /windows
sudo cp /etc/fstab /etc/fstab_backup
gksudo gedit /etc/fstab
``` Replace this line ```
/dev/hda1       /media/Windows  vfat    iocharset=utf8,umask=000 0 0
``` with this line ```
/dev/hda1       /windows  vfat    iocharset=utf8,umask=000 0 0
``` Save and exit Gedit. ```
sudo mount -a
``` See if that makes a difference.

---

### Post by SaxmanTy on 2006-05-29
Well I tried moving my mounting point to /Windows.  But no dice.  After that I went into windows, and checked.  And yes some of the files and folders were set to be read only.  Even ones that I was having trouble with.  I corrected that, and was sure to include all of the subfiles and folders.   I thought this would fix it, but when I rebooted back into Linux, I found that nothing has changed.  I can read everything, but I can not write to certain folders, where as others I can.
But anyway, here is my fstab file.
```
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,sync  0       0
usbfs         	/proc/bus/usb usbfs   devgid=14,devmode=0660 	0 	0 
/dev/hdb1	/home/saxmanty/Documents	vfat	iocharset=utf8,umask=0000	0	0
/dev/hdb2	/home/saxmanty/Multimedia	vfat	iocharset=utf8,umask=0000	0	0
```

---

### Post by aysiu on 2006-05-29
SaxmanTy, my message was targeted at Nonno Bassotto, not you.

For you... I don't know. It's a mystery. I've seen a lot of these FAT32 issues, and they've always come down to one of the following:

1. The partition is mounted in /media or /mnt
2. The partition is specified to mount at two separate mount points within the /etc/fstab
3. The partition was never remounted after changes to the /etc/fstab

If you're pretty sure it's not one of those three... I have no idea what it could be. Can we assume you've already tried these? ```
sudo umount /dev/hdb1
sudo umount /dev/hdb2
sudo mount -a
```

---

### Post by SaxmanTy on 2006-05-30
Ok everyone here's the problem.
It its TOTALLY a windows thing.  So I hope for anyone else whos runs into this, they see the solotion here.  
Because windows likes to customize folder like "My Documents, Fonts, ect" and give them bell and whistles, it needs to make them read only!  BUT don't forget this is windows were talking about!  You can not change that!   So for me, with all of the folders in question,  had them color coated for easy access when I was using windows.  And well I guess  the second I did that, windows made the folders read only, and permanatly!  So when I tried to load the partitions in Linux, I can't wirte to them becasue windows said so! 

Well here's micorsoft's solution:
 [http://support.microsoft.com/?id=326549]("http://support.microsoft.com/?id=326549")

and this thead explained it to me a little better:
[http://www.ozzu.com/ftopic61196.html]("http://www.ozzu.com/ftopic61196.html")

So as you can see, to  make it even more stupid, Explorer will STILL claim that the files are Read only, even after you changed it at the command prompt!!  GOD am I so happy that I switched to Linux!  Anyway, once I did all this mess and booted back into Linux, everything was just how I want it.  I can read and wirte to each of the folders no problem, and they are mounted to where I need them to be!  Time for a beer!! 
Cheers
:evil:

---

### Post by Sutekh on 2006-05-30
I have seen this issue before in another thread.

[http://www.ubuntuforums.org/showthread.php?t=140809](http://www.ubuntuforums.org/showthread.php?t=140809)

An un-obvious solution indeed.  Good on you for working it out.

---

### Post by Nonno Bassotto on 2006-05-30
turbojugend_gr, sorry, it seems you were right. I didn't know that windows could set this kind of attributes on files.
I'm going to try the solution proposed, but it is quite annoying having to do this for each folder (there are quite a lot). I hope this won't screw up personal settings made in windows.
Does anybody know if there is a way to tell mount simply to ignore windows permissions? This would be the quickiest way.
Otherwise one could profit from the fact that fat32 allows permissions to set it the linux way. That is, set everything as ro in windows, except for "Documents and Settings/Username", in order to create something similar to standard permissions in Linux. It seems Windows should ignore this settings, anyhow, isn't it?
Thank you all for your help.

---

### Post by turbojugend_gr on 2006-05-30
It's ok, I am used to such view differences. That's why I love Linux, users get to know exactly what they are talking about after some chat...
I hope you got all your problems solved. DON'T miss the first parts of my POST, it has it's reason to be there, try it out...

---

