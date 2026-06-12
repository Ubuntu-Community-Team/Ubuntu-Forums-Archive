---
title: "Trouble with mounting NTFS drives"
date: 2006-06-19
forum: General Help
---

### Post by Grimmeehh on 2006-06-19
Firsty, hi, im a brand new unbuntu user- but dont click back just yet!

Ive installed unbuntu and i like it, using it right now. However im having issues with trying to access my NTFS hard drives with my data on. I dont want write access, just basic read access.

I can view the drives from Disk manager, and it shows how much space they have on them etc, however i do not have permission to view them. So i read up on the wiki, help pages and such, and loaded up the fstab, and made attempts to mount them properly to a /media folder and  set permissions. however the drives are not in the /etc/fstab, i cannot unmount them from the default and i cannot even create a folder in /media due to lack of permission or whatever.

theyre currently (apparantly automatically) mounted to /tmp/disks-conf-sdb1 (or /tmp/disks-conf-hda1 etc etc) it seems (from the disk manager) with locations of /dev/sdb1 etc. using the disk manager to attempt to mount them to a location such as /hdd1 is confusing and does not appear to work anyway.

whats going on ?

thanks, from a hopefully new linux user :)

---

### Post by aysiu on 2006-06-19
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows) should help you.

Just let us know if you run into weird errors or parts that confuse you.

---

### Post by Grimmeehh on 2006-06-19
Thanks, thats the page i was using before.

My problem comes when i try to edit the /etc/fstab file. I load it up, but all i get is:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sdb3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

None of which are my NTFS drives. my drives are listed in the fdisk -l command however, albeit they are separate physical drives so under a different heading.

do i need to add lines to this? im not at all sure how i would go about that though. 
*edit- i cant seem to even edit that file, i do not have permission...

Thanks for the help

---

### Post by aysiu on 2006-06-19
Yes, go ahead and add the lines. Basically, the idea is that they need to be there correctly.

If they're there incorrectly, they need to be corrected.
If they're not there at all, they need to be added.

You'd add something like ```
/dev/hda1 /windows1 ntfs nls=utf8,umask=0222 0 0
``` You also have to actually create the folder /windows1, too ```
sudo mkdir /windows1
```

---

### Post by Grimmeehh on 2006-06-19
Thanks, but as i just edited in to my last post (apparantly not fast enough) I get a permission denied when i attempt to edit /etc/fstab using nano. Do i need to set permissions to the /etc folder also? and er, how :/ the "permissions" page on the wiki is very confusing to a newbie like me.

sorry bout the hassle :)

[ Error writing /etc/fstab: Permission denied ]

---

### Post by aysiu on 2006-06-19
The instructions I linked to give you the command to edit the /etc/fstab with administrator privileges: ```
kdesu kwrite /etc/fstab
``` for KDE or ```
gksudo gedit /etc/fstab
``` for Gnome.

---

### Post by Grimmeehh on 2006-06-19
Excellent, thanks, I have now mounted my drives :)

Though i cannot see

kdesu kwrite /etc/fstab
 or 

gksudo gedit /etc/fstab

 anywhere on that page, it worked :) . your help is much appreciated. gonna fiddle about a bit more i think til i come unstuck.

---

### Post by sisooktom on 2006-06-19
[QUOTE=Grimmeehh]Excellent, thanks, I have now mounted my drives :)

Though i cannot see

kdesu kwrite /etc/fstab
 or 

gksudo gedit /etc/fstab

 anywhere on that page, it worked :) . your help is much appreciated. gonna fiddle about a bit more i think til i come unstuck.[/QUOTE]

Sounds like you're just not used to having to deal with *nix permissions.  Generally, your normal user account does not have permission to write to any files that aren't in your home directory.  This includes most of the files your system needs to run.  In order to edit those files you have to elevate your permissions using "sudo" (kdesu and gksudo are just graphical equivalents of sudo).  Doing this gives you the ability to run commands as the "root" user (superuser or system admin).  This is a good system as it helps to prevent you accidentally breaking your system by inadvertantly messing up key files.  I'd encourage you to read up on the permissions system used in UNIX type OSs.  It will really help you out.

---

### Post by Grimmeehh on 2006-06-19
This is true, but then ive never used linux before :)
thanks for the info though.

I did just run myself into another problem, after getting things i wanted going (music, msn, irc, basics like that) i decided it was time to install nvidia graphics drivers.. possibly not such a bright idea!

I followed the wiki as close as i could: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

unfortunately when i came to reboot the X server by CTRL-ALT-BSPACE, the x server will no longer boot up and i get an error (the splash screen did not show). i made sure i had all the packages, the restricted modules, nvidia-glx, then "sudo nvidia-glx-config enable" seemed to go through fine..

closed everything up and reloaded it and it doesnt work :S balls.

Anyway, it said it made a backup, how can i restore this through the command prompt i end up with? or any suggestions on where i went wrong :)

i assume the file was /etc/X11/xorg.conf the one thats now incorrect, infact i shouldve remembered where it backed up too.. hrm. it sucks being a newbie again !

Incidentally its a GeForce 6800.

-Col (from windows.. should i have made a new post? .. mhm)

*edit* infact i shouldve tried troubleshooting it a bit first before coming straight here. i just had to boot to windows and i naturally thought i should ask. problem is i cant read the wiki and use linux at the same time now :@ and im kinda worried bout completely knackering something :)

---

### Post by WhoDaBear on 2006-06-22
Thanks anyway - fixed.

---

