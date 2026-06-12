---
title: "installation problem with DVDRW"
date: 2006-02-04
forum: General Help
---

### Post by razzy911 on 2006-02-04
Hey I have a nec dvdrw and it boots fine but then it cant find drivers for it(it cant recognize it) .. it tells me i can load drivers from floppy,I tryed but it doesnt even attempt to read from it , it just says retry
Everything works with windows..
However, I noticed i can execute a shell...if someone could help me with that, it would be good, coz i have the iso installation file on my harddrive..
Thanks

---

### Post by dcstar on 2006-02-04
[QUOTE=razzy911]Hey I have a nec dvdrw and it boots fine but then it cant find drivers for it(it cant recognize it) .. it tells me i can load drivers from floppy,I tryed but it doesnt even attempt to read from it , it just says retry
.....
Thanks[/QUOTE]
**Exactly** what does it it say and when does it say it?

And you may get more help posting the question here:

[http://ubuntuforums.org/forumdisplay.php?f=94](http://ubuntuforums.org/forumdisplay.php?f=94)

---

### Post by handy on 2006-02-04
[QUOTE=razzy911]Hey I have a nec dvdrw and it boots fine but then it cant find drivers for it(it cant recognize it) .. it tells me i can load drivers from floppy,I tryed but it doesnt even attempt to read from it , it just says retry
Everything works with windows..
However, I noticed i can execute a shell...if someone could help me with that, it would be good, coz i have the iso installation file on my harddrive..
Thanks[/QUOTE]

It sounds like your drive is not mounted.

Have a look in the online help which is installed on your computer.

*Choose:*  **Ubuntu 5.10 Starter Guide**

*Then:*  **Hardware** or **Hardware Chapter**

That should get you started, the next question that you will be asking your self is  what's fstab?

The manual will help there too! :p

---

### Post by drmcclure on 2006-02-04
I am also trying to get a dvd drive running after installing it.  Right now, I think Ubuntu has the settings for the old drives.  Where is the 5.10 starter guide?

---

### Post by dcstar on 2006-02-04
[QUOTE=drmcclure]I am also trying to get a dvd drive running after installing it.  Right now, I think Ubuntu has the settings for the old drives.  Where is the 5.10 starter guide?[/QUOTE]
What do you mean "running"?

If you mean getting it to write, you must install the various bits of software, if you mean it's not on your list of drives, do:

System-Administration-Disks and see if it is listed, then you may have to edit your /etc/fstab file to add it in.

---

### Post by drmcclure on 2006-02-04
You are right.  It is not on my list of drives.  How do you add it in to the fstab file?  I know how to use the gesit feature.  Thanks!

---

### Post by handy on 2006-02-04
[QUOTE=drmcclure]I am also trying to get a dvd drive running after installing it.  Right now, I think Ubuntu has the settings for the old drives.  Where is the 5.10 starter guide?[/QUOTE]

There is a small red & white life bouy icon in the title bar of the Ubuntu (Gnome) desktop, also available through ***Menu:***  **Sysem / Help** (Same icon).  After that it is more obvious. :-D

If you search the forum, & or the various wiki's you will findout how to edit the /etc/fstab

---

### Post by dcstar on 2006-02-05
[QUOTE=drmcclure]You are right.  It is not on my list of drives.  How do you add it in to the fstab file?  I know how to use the gesit feature.  Thanks![/QUOTE]
sudo gedit /etc/fstab

My file has the following lines for a CD/DVD, copy and edit this to suit your settings (if you like):

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  	<options>       			<dump>  <pass>
proc            /proc           proc    	defaults        			0       0
/dev/hda4       /               ext3    	defaults,noatime,errors=remount-ro	0       1
/dev/hda5       none            swap    	sw					0       0
[B]/dev/hdd        /media/cdrom0   udf,iso9660	ro,user,noauto,noatime			0       0
/dev/hdc        /media/cdrom1   udf,iso9660	ro,user,noauto,noatime			0       0[/B]
/dev/fd0        /media/floppy0  auto    	rw,users,noatime,noauto			0       0
/dev/hda1       /c		vfat    	umask=000,noatime,auto			0       0
/dev/hda3       /Img            ext3    	defaults,noatime,errors=remount-ro	0       1
/dev/pktcdvd/0	/media/cdvdrw	udf		noauto,noatime,rw,users			0	0
```

---

### Post by drmcclure on 2006-02-05
Here's what I have in my fstab file and my DVDRW is still not mounting.  Any more suggestions?!

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660	ro,user,noauto,noatime			0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
#/dev/pktcdvd/0	/media/cdvdrw	udf		noauto,noatime,rw,users			0	0


Thanks

---

### Post by dcstar on 2006-02-06
[QUOTE=drmcclure]Here's what I have in my fstab file and my DVDRW is still not mounting.  Any more suggestions?!

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660	ro,user,noauto,noatime			0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
#/dev/pktcdvd/0	/media/cdvdrw	udf		noauto,noatime,rw,users			0	0

Thanks[/QUOTE]
You have to specify what /dev/hd? your drive actually is, and you must make sure the mount point directory exists (/media/cdrom?), if it doesn't exist you must create it.

hda is the first IDE channel Master device Ubuntu detects, hdb is the first Slave on that channel, hdc is the second IDE channel Master device, hdd the second Slave device.

Check to see what these actually are on your system, and make any necessary modifications to the fstab file.

---

### Post by drmcclure on 2006-02-06
[QUOTE=dcstar]You have to specify what /dev/hd? your drive actually is, and you must make sure the mount point directory exists (/media/cdrom?), if it doesn't exist you must create it.

hda is the first IDE channel Master device Ubuntu detects, hdb is the first Slave on that channel, hdc is the second IDE channel Master device, hdd the second Slave device.

Check to see what these actually are on your system, and make any necessary modifications to the fstab file.[/QUOTE]

What command do I use to find out what my devices actually are on my system?  Thanks

---

### Post by annsachd on 2006-02-06
dmesg | less

---

### Post by drmcclure on 2006-02-06
[QUOTE=annsachd]dmesg | less[/QUOTE]

OK. I tried this command but I just see hdc in the list.  I can hook up my DVD/RW first  and get it to work.  Then when I plug the CDROM in on top I can only use it.  Do you have any ideas on how to clear up my mess?!  Thanks

---

### Post by dcstar on 2006-02-06
[QUOTE=drmcclure]OK. I tried this command but I just see hdc in the list.  I can hook up my DVD/RW first  and get it to work.  Then when I plug the CDROM in on top I can only use it.  Do you have any ideas on how to clear up my mess?!  Thanks[/QUOTE]
Do you have the Master/Slave jumpers set correctly on **both** drives?

---

### Post by drmcclure on 2006-02-06
[QUOTE=dcstar]Do you have the Master/Slave jumpers set correctly on **both** drives?[/QUOTE]

I'm not quite sure what you mean by set correctly.

---

### Post by drmcclure on 2006-02-07
[QUOTE=drmcclure]I'm not quite sure what you mean by set correctly.[/QUOTE]

OK.  I found some good websites (cnet.com and helpwithpcs.com)  on how to set up the drives jumper.  Thanks!

---

