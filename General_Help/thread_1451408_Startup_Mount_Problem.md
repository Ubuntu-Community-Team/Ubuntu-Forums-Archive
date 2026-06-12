---
title: "Startup Mount Problem"
date: 2010-04-10
forum: General Help
---

### Post by kwanylongy on 2010-04-10
Dear all,

    I have Portable Ubuntu Remix version TRES installed on Windows Vista Home Basic. It used to work fine until once my laptop shut down because of low battery.

    Since then, when I start my portable ubuntu, DOS stops at this point(see "DOS Error Mesage" below):

    After doing my research, I learned that I could solve the problem with this by:
    1) Pressing "Esc" to start the recovery shell
    2) Type in the cmd "mount -o remount /" (and press enter)
    3) Ctrl+D

    Then boot would resumed and Ubuntu would be successfully booted up.

    But I have to do this every time I start Ubuntu, and I wonder how I could solve this problem.

    Below are my DOS Error Message and my /etc/fstab.



DOS Error Message (DOS stops at this point at startup)
===============================================================================================
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
mountall: mount  [888] terminated with status 1
mountall: Filesystem could not be mounted:
fsck from util-linux-ng 2.16
WARNING: bad format on line 19 of /etc/fstab
ata_id[1158]: unable to open '/dev/.tmp-block-22:0'

/dev/cobd0: clean, 146957/242880 files, 796881/969920 blocks
One or more of the mounts listed in /etc/fstab cannot yet be mounted:
(ESC for recovery shell)
/: waiting for /dev/cobd0
/tmp: waiting for (null)
: waiting for -e
===============================================================================================

Content of /etc/fstab
===============================================================================================
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           	proc    	defaults        	   0   0
# Colinux block device mount points

# <file system> <mount point>   <type>  <options>		  <dump>  <pass>
/dev/cobd0	/		ext3	relatime,errors=remount-ro 0      1
#/dev/cobdX 	/path           ext3   	relatime,errors=remount-ro 0      0
# Windows mount points

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
cofs0		/usr/local/pubuntu 	cofs		user,dmask=0777,fmask=0666 0   0
#cofsX		/path/mount/point 	cofs		user,dmask=0777,fmask=0666 0   0
-e 
#Entry for cdrom
/dev/cdrom           /media/cdrom              udf,iso9660		user,noauto,exec,utf8
===============================================================================================
P.S. Line 19 in /etc/fstab (referred in DOS Error Message) is the line with "-e"


Thanks a million for your help!

Carlos

---

### Post by b0b138 on 2010-04-10
delete line 19

---

### Post by kwanylongy on 2010-04-10
> **b0b138 said:**
> delete line 19

How do I delete line 19?

I tried "sudo gedit /etc/fstab" and deleted line 19 using gedit, saved and restarted.
But then line 19 reappears in /etc/fstab after restart. :confused:

Thanks for your quick reply!


Carlos

---

### Post by jamesisin on 2010-04-11
I don't imagine this is causing the trouble, but you should not use sudo for graphical applications:

```
gksudo gedit...
```

---

### Post by Skidbladnir on 2010-04-11
GEdit isn't a problem, but you should use gksudo in GNOME or XFCE or kdesu in KDE, to avoid problems with your something-ice files that get CHOWNed because it's loading the user's profile, and not root's.

---

### Post by kwanylongy on 2010-04-11
> **jamesisin said:**
> I don't imagine this is causing the trouble, but you should not use sudo for graphical applications:

```
gksudo gedit...
```

I tried "gksudo gedit /etc/fstab", but couldn't succeed. These errors were returned.

Terminal: Error copying '/home/pubuntu/.Xauthority' to '/tmp/libgksu-gAHOzB': Permission denied
Cygwin/X X: Failed to run gedit '/etc/fstab' as user root.Unable to copy the user's Xauthorization file.


As pointed the problem may have been root authority on GUI applications, so I tried editing using nano.
I did "sudo nano /etc/fstab", and deleted the "-e" line (line 19), and saved (with WriteOut in nano)

Then I restarted, and the "-e" line still remains..........

any thoughts?


Thank you so much for your help!
The Ubuntu community is really a nice and friendly place! 


Carlos

---

### Post by jamesisin on 2010-04-11
Are you editing your Ubuntu files from your Windows environment?

---

### Post by kwanylongy on 2010-04-11
> **jamesisin said:**
> Are you editing your Ubuntu files from your Windows environment?

No, I edited under Ubuntu, using the terminal.

Carlos

---

### Post by jamesisin on 2010-04-11
Ah, I see that this portable version makes heavy use of Cygwin.  I'll offer advice if I am able, but for now I watch to see if anyone with more familiarity can help.

---

### Post by kwanylongy on 2010-04-11
> **jamesisin said:**
> Ah, I see that this portable version makes heavy use of Cygwin.  I'll offer advice if I am able, but for now I watch to see if anyone with more familiarity can help.

Cheers, thank you so much, you have been great! 

Carlos

---

### Post by jamesisin on 2010-04-11
I suppose you could try commenting out the line in question (place a # at the beginning of that line) to see if it is replaced or if an additional line is added.  That would tell you if the file was being recovered to its former state or whether some smart application is added that missing line back into the file.

---

### Post by kwanylongy on 2010-04-11
> **jamesisin said:**
> I suppose you could try commenting out the line in question (place a # at the beginning of that line) to see if it is replaced or if an additional line is added.  That would tell you if the file was being recovered to its former state or whether some smart application is added that missing line back into the file.

Tried commenting with "sudo gedit...." initially.

now retried using "sudo nano", "#-e" still becomes back to "-e"


Carlos

---

### Post by jamesisin on 2010-04-11
This suggests that something is replacing your fstab file with some archived copy.  Try adding some useless comment line (like # will this line remain?) to retest this theory.

(Using nano or vi is great because then you don't have to fret over graphical issues.  You may want to create a post to ask about gksudo on that system.)

---

### Post by kwanylongy on 2010-04-12
> **jamesisin said:**
> This suggests that something is replacing your fstab file with some archived copy.  Try adding some useless comment line (like # will this line remain?) to retest this theory.

(Using nano or vi is great because then you don't have to fret over graphical issues.  You may want to create a post to ask about gksudo on that system.)


Did that (with nano of coz), but fstab still became what it was before editing after restarting.

1 important thing I did not clarify. I did the previous editing AFTER Ubuntu was booted up (I got ubuntu booted up by "mount -o remount /" then "Ctrl+D", as mentioned in my original post.

I guess I could have edited fstab at the colinux console to avoid uncertainty and I tried just that, but this error was returned.

Nano: "Error writing /etc/fstab: Read-only file system"

I tried "chmod a+rw /etc/fstab", but the follow error was returned

chmod: changing permissions of `/etc/fstab': Read-only file system


Any thoughts?


Many Many Thanks!!!

Carlos

---

### Post by jamesisin on 2010-04-12
This is moving into somewhat uncertain territory for me, but there is a command called chroot which allows one to navigate and access foreign systems.  I think that is what you want to use to access the installed fstab from the recovery console or live CD or anything that is not specifically the installed OS.

Here is a good starting point for your investigations:

[http://ubuntuforums.org/showpost.php?p=8995103&postcount=37](http://ubuntuforums.org/showpost.php?p=8995103&postcount=37)

---

### Post by AbieSwanepoel on 2010-06-13
The extra '-e' is generated by the /etc/init.d/postmount_pubuntu.sh script on startup. It seems the problem is (yet again) due to incompatibilities between dash and bash. Dash uses a built-in 'echo' command that does not recognize the '-e' option (used on line 52 of the script mentioned above).

To solve the problem, change the first line of the /etc/init.d/postmount_pubuntu.sh script to read:

#! /bin/bash

---

### Post by kwanylongy on 2010-06-27
Did that: modified the first line of '/etc/init.d/postmount_pubuntu.sh' from '#! /bin/sh' to '#! /bin/bash' via cmd 'sudo nano /etc/init.d/postmount_pubuntu.sh'.

I made sure changes were saved and restarted pubuntu, sadly the problem still persisted.

Thank you very much for your generous help!


Carlos

> **AbieSwanepoel said:**
> The extra '-e' is generated by the /etc/init.d/postmount_pubuntu.sh script on startup. It seems the problem is (yet again) due to incompatibilities between dash and bash. Dash uses a built-in 'echo' command that does not recognize the '-e' option (used on line 52 of the script mentioned above).

To solve the problem, change the first line of the /etc/init.d/postmount_pubuntu.sh script to read:

#! /bin/bash

---

