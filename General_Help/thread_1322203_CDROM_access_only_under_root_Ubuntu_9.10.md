---
title: "CDROM access only under root? Ubuntu 9.10"
date: 2009-11-10
forum: General Help
---

### Post by SirWeazel on 2009-11-10
NOTE: This problem fixed itself a couple hours later after a couple reboots and complete shutdowns. Not sure what changed. (could it be the order in which it loads drivers or something?) Anyways, i'm curious if anyone else has had this issue? Should i file a bug report?

For some reason with no changes that i can tell, when ever i put a cd into the drive it is not seen or accessible under either of the 2 user accounts i have created.  The drive mounts itself as root i think.  If i use gksu nautilus i can browser the contents of the drive and unmount and eject the drive. Otherwise, the drive is unusable under normal account.

Something is messed up with permission maybe?  What should the drive ownership be set to and other stuff?  When view permissions it is currently set to:

Owner: 400 - user #400
folder access: (create and delete files)

Group: 401
folder access: (none)

Others: "blank"
folder access: (none)

And when i go to manage user acounts/manage groups. The group "users" doesn't have any of the user accounts selected?

---

### Post by pennygov on 2009-11-11
I am having a similar problem on both my kubuntu 9.10 computers. (Toshiba=an upgrade from Jaunty; and Acer=clean install) It is inconsistent - sometimes the cds mount with user (well, me) as the owner and I can execute; then sometimes they mount with root as the owner and I can read them, but not execute. 

I've tried mounting them in a terminal as user, and it still will be "owned" by root and I can read it but not execute. 

Lines from fstab & mtab:
fstab - "/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0"
mtab - "/dev/sr0 /media/cdrom0 iso9660 ro,nosuid,nodev,utf8,user=pennyg 0 0"

dev scd0 and sr0 are the same device. The mtab line says I am the user, but it won't let me use it! (and yes, I realize that fstab says how it SHOULD be mounted and mtab says how it IS mounted)

Now, to further complicate things, I just put in a cd and mounted it as user and it is owned by "unknown"(501) and the group is "dialout". I can execute. The same cd showed the same earlier. I'm wondering if the problem is with the cds?????

Anyone else out there know what this is about? Does fstab have any validity any more or is there another way to control how devices are mounted?

---

### Post by Sin@Sin-Sacrifice on 2009-11-11
Might be that the "Browse Media When Inserted" option is unchecked in the nautilus preferences. Open any folder and click Edit>Preferences and then the Media tab. At the bottom you should see it. Don't know why it would go away now why it would start working again. Sorry if that doesn't do it for you.

---

### Post by SirWeazel on 2009-11-12
Penny, that sounds exactly like the problem i was having. It fixed itself!!??(as i noted in top of my post) and hasn't reoccured yet/unable to duplicate problem.

I have my computer setup for multiple users (myself and my wife) and we are both logged in, and the cd is inserted, sometimes it mounts uder the other users name. But i havn't had the mounting as root problem again.  And i hope it doesn't occur again :)

Sin sin, as of now i have the "browse media" checked. I don't know if that could have been the problem or not. But i didn't know to look their at the time of the problem.  If it happens again, then i will check that to see if it is related.

Sorry i couldn't be any help.  But i'm glad i'm not the only one with this problem. I hope you get it fixed Pennygov, and i'll be looking forward to hearing how incase it happens again.

---

### Post by SirWeazel on 2009-11-25
I've also been able to duplicate the problem.  This problem happens when i put a "windows" based cd in (an application cd designed for windows).  So if want to copy a cd i have to run gksu brasero and image the file, then burn the file from my local user account.  Example: i have a UBCD4WIN disk i made along time ago and whenever i put it into the drive it mounts as root.  Or if i put a windows XP disc in the drive it mounts as root. Which i think is going to be a problem when i attempt to install xp on a virtualbox.  I hope someone can help.

---

### Post by jmervyn on 2009-11-27
I've found the same error, trying to browse an e-book CD that I stupidly left in the drive during the upgrade process.

It may or may not have something to do with mounting the drive under particular formats - when I eject the CD and put either a DVD or a different CD in, no problems.  Trying to execute this command:
sudo mount /dev/cdrom /media/cdrom -t vfat

yields an error claiming wrong fs type yadda yadda or some other error.  So maybe there's a problem with the recognition of some file system types?

EDIT - probably related to this error:
[http://ubuntuforums.org/showthread.php?t=1329949](http://ubuntuforums.org/showthread.php?t=1329949)

---

### Post by jmervyn on 2009-11-27
Well, I managed to resolve the initial problem but I'm too much of a n00b to know if/how the change is permanent.

**sudo mount -o rw /media/cdrom0** can mount the drive, but I strongly suspect that the problem lies in my /etc/fstab file.  The relevant entry is:

/dev/scd0     /media/cdrom0   udf,iso9660   user, **noauto**,exec,utf8  0  0

EDIT - and that's it.  Dump the noauto entry and it works.

---

### Post by cwlowcay on 2009-12-19
I think it is related to this bug: [https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/10550](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/10550).  Basically, some lousy authoring program is setting incorrect permissions on UDF DVDs, which Linux tries to honour.  Apparently it only affects some disks.  The solution is to mount in iso9660 instead of udf, by changing the cdrom line of your fstab file.

Type:
```

gksu gedit /etc/fstab
``` at a terminal to open up the fstab file.

Find the line with mount point /media/cdrom0 and change "udf,iso9660" to "iso9660,udf"

Save the file and reinsert the disk.

---

