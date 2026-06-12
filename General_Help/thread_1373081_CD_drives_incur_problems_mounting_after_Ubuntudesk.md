---
title: "CD drives incur problems mounting after Ubuntudesktop to Xubuntudesktop &quot;upgrade&quot;"
date: 2010-01-05
forum: General Help
---

### Post by Brendo613 on 2010-01-05
Hi all.  I have a 1200mhz AMD tower which has used Ubuntu since June of '07.  I am on what I think is now the 3rd install (for various reasons), which was performed only a few months ago with a fresh copy of Ubuntu 9.10.  I don't remember doing the upgrade process from 9.04 to 9.10, so I'm fairly certain it was a fresh 9.10 install.  A week or two ago, I found that the system runs a bit smoother with the XFCE desktop environment installed, but it's not a whole lot better than Gnome.  Either way, I can choose which to load at the login screen.

My problem is with mounting CDs - with media, or blank.  There are two drives: a CD R & RW burner (primary) and a DVD reader.  Here's where each desktop environment is giving me different results.  

[CENTER]G N O M E[/CENTER]
In Gnome, a blank disc inserted to the burner drive does not mount and is if the drive is empty.  Browsing in "Places -> Computer," the CD drive option disappears when there's something in it.  The DVD drive can read an audio disc, as can the CD burner drive.

[center]X F C E[/center]
In XFCE, a blank CD inserted into the burner drive brings up a popup menu, offering an option for Brasero to burn an audio CD.  Strangely, the blank CD isn't mounted - I can't open it up in a file manager window.  

I'm not in XFCE right now, and don't remember if the audio CD loaded right in either tray while running XFCE, but it's the lack of burn-ability that has me troubled.  The system used to run fine with either drive, and I don't recall any burning issues; certainly, I don't recall any non-mounting issues.  I am inclined to think the problem lies with the ubuntudesktop -> xubuntudesktop installation, but why would both desktop environments now fail to do what Gnome used to be able to?  I think I'm missing something.  Thanks for reading, and hope it's something simple.  It would be a pain to have to reinstall - especially if I have to now pick one "permanent" desktop environment

---

### Post by Tigersmind on 2010-01-05
I have a problem very much like this. What I found out over a period of time was the drive was going bad. Later the drive started to not even open, mechanically failing.

Linux seemed more sensitive to this than Windows for quite a while, but it is doing it all the time now.

---

### Post by Brendo613 on 2010-01-05
I suppose that's a possibility, but it just seems too coincidental that two mechanical failures present themselves at the same time as a recent Synaptic package addition had been performed.  As a further note, an external USB hard drive is mounted and fully browse-able.  I really don't know what is at fault here.  Maybe I should try manually mounting a blank disc?  I tried following some tutorials on this, but I'm unsure from where and to where to pick.  

Here is an output of my /etc/fstab ; maybe this can help someone get a better clue (spacing is off though, not sure how to make it appear right):

[INDENT][FONT="Courier New"]proc            /proc           proc    defaults        0       0
UUID=6cdfce7f-64ea-49f0-aa8e-8caf4a32f10a /               ext4    errors=remount-ro 0       1
UUID=55ad9027-b1d6-4fa0-9618-93d20205e7eb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0[/FONT][/INDENT]

---

### Post by Brendo613 on 2010-01-10
bump.  I don't just wanna do a fresh install to fix a likely config problem :-\  Still no clue on what to test out.

---

### Post by Brendo613 on 2010-01-13
I know I don't have much to offer, seeing as I'm seeking someone's help.  Oh, the drama of it all!  The fresh install temptation looms ...

This is bump.

---

