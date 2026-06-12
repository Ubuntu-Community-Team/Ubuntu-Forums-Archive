---
title: "samba - seeing my hda drive"
date: 2005-03-04
forum: General Help
---

### Post by geovino on 2005-03-04
I've just installed Ubuntu and when going to Disks, I don't see my hda and hdb drives to access files. How do I set that up?

Thank You,
Dave

---

### Post by alastair on 2005-03-04
Not sure I can help - but I don't really know what you mean. "Disks"?

Please explain what you are doing and what you want to happen.

---

### Post by geovino on 2005-03-04
When you click on desktop on the tool bar you can select Disks; it  shows the hardrives that you have. I have two, hda and hdb. I want to open the files in hda (WinXp) so I can open my documents and music files. The BeatrIX linux live CD and the Mepis live cd let you see the hard drives. In Ubuntu they have that feature turned off. This access to HD should be normal.

Thanks,
Dave

---

### Post by p!=f on 2005-03-04
Do you mean you can't see Windows partitions mounted?
Post your /etc/fstab here.
Did you read [http://www.ubuntuguide.org/#windows?](http://www.ubuntuguide.org/#windows?)

---

### Post by geovino on 2005-03-04
yes! exactly. can't  you tell me how? Please make it easy. the instructions to mentioned are not very good. Thank you.  

Dave

---

### Post by crane on 2005-03-05
I added the 2 following lines to my fstab file.

/dev/hda1       /windows/system    ntfs    umask=0222      0       0
/dev/hda2       /windows/games    ntfs    umask=0222      0       0


/dev/hda1= is the disk itself
/windows/system is a file I created as a mount point.

This way my to windows partitions are mounted when ever I boot up/
You can change the /windows/system and or the /windows/games files to what ever you like. Just be sure to create the files. As far as adding it to the disks menu, I don't have a clue. (never tried it) You can however create a shortcut on your desk top or bar to access the file. 
Just creat launcher, and under command enter something like: nautilus /usr/local/games  or whatever you named your file.

Goos luck!!

---

### Post by geovino on 2005-03-05
I added the 2 following lines to my fstab file.

where is the fstab file? what do you mean? 

I've have tried three different ways of accessing the hda drive and none of them have worked. 

the hda drive should have been there by default

thanks

---

### Post by geovino on 2005-03-05
Crane ,
Please explain how you do this.

I may go back to Mandrake. I've heard it's very good.

---

### Post by eazy on 2005-03-06
hey.i am new in linux and have the same problem,when i try to mount my cd rom or hdd-s.
with cd rom i get  
message like these:Unable to mount the selected volume. The volume is probably in a format that cannot be mounted.mount: wrong fs type, bad option, bad superblock on /dev/hdb,or too many mounted file systems. how can i fix it?
my /etc/fstab looks like:# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc6       /               ext3    grpquota,errors=remount-ro 0       1
/dev/hdc5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

and how can i mount other hdd i have ide1 C=hda1 ntfs  windows xp
and ide2 E=hdc7 fat32 my files?
thanks if anybody can help me =D>

---

### Post by geovino on 2005-03-06
this is too much trouble for something that should be there to begin with... I'm trying out Mandrake!

---

### Post by p!=f on 2005-03-06
[QUOTE=geovino]this is too much trouble for something that should be there to begin with... I'm trying out Mandrake![/QUOTE]
Should be for you, not for me. ;) Question of taste. 
If you leave Ubuntu just because you are not able to read carefully 100% working step by step instructions, I have nothing to comment.

Good luck with Mandrake. Sad you're leaving but it happens, I'm sure you will have great times with RPM based distro. ;)

---

