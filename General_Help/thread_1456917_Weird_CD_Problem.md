---
title: "Weird CD Problem"
date: 2010-04-17
forum: General Help
---

### Post by tmms on 2010-04-17
Hallo,



Have a weird problem with Ubuntu not recognizing 
audio CDs.

Tried to search forums for "audio CD problem", 
"audio CD not recognized", and similar, 
found numerous references to similar problems, 
but, unfortunately, no solutions helpful to my situation.

So, the problem is as follows:


Computer: Dell Optiplex GX240
CD Drive: Samsung CD-ROM SN-124
OS: Ubuntu 9.10 Karmic Koala
GNOME Version: 2.28.1


After inserting an audio CD into the CD drive, 
the icon "CD Drive" changes to "CD Drive: Audio disc", 
but, after approx 60 seconds a message appears:

Unable to mount Audio Disc
Drive /dev/sr0 does not contain audio files

or, when Rhythmbox Music Player happened to be running:

Unable to mount Audio Disc
DBus error org.freedesktop.DBus.Error.NoReply: 
Message did not receive a reply (timeout by message bus)

After that, the icon returns to plain "CD Drive", 
like there is nothing in the bay, 
and Rhythmbox shows no disc.

Tried to install other players, namely KsCD, Mplayer, and VLC.
KsCD reports "No disc"
Mplayer Media Player reports "No media opened"
VLC shows no disc.

What's more, after going thru the above mentioned problems, 
CD drive ceases to recognize data CDs, as well.
(For reference, before inserting an audio CD 
CD drive reads data CDs properly.)

After a reboot, the situation repeats.

Let's me add, that it seems not to be a hardware problem, 
as the same computer with the same CD drive works like a charm 
when running Windows XP: reads both the very same audio CDs, 
as well as the data CDs without any problems.

Audio subsystem works OK, as I am able to play MP3s
from the HDD.

Any ideas how to play audio CDs ?





For reference: /etc/fstab content below:


# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=66f0cf2d-e542-4acf-9f44-035005187737 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b65fb477-c6ad-4e88-af0c-32d8ef5ccc6b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by tmms on 2010-04-18
Sorry, if it was posted in a wrong forum   :-(
 
But I understood that "Dell" forum deals with current Dells only...
 
And "Hardware" seems not to be appropiate...

---

### Post by pj_kare on 2010-04-19
Just letting you know I'd been here, I know how frustrating it can be when you don't get a reply,
I exhausted every search phrase I could come up with in Google trying to find an answer for you, but I wasn't very successful.
Seems as though you are not the first to have had this problem as I found this: [http://newyork.ubuntuforums.org/showthread.php?p=7287286](http://newyork.ubuntuforums.org/showthread.php?p=7287286) 
Just wish I could have been of some help, Good luck! Hope you get it sorted.:(

---

### Post by tmms on 2010-04-20
Questions to moderators: 

Can you move this post to "Multimedia & Video" section ?

Or, should I send there a new post ?

---

### Post by tmms on 2010-04-20
Thanks, pj_kare, for your compassion !

---

