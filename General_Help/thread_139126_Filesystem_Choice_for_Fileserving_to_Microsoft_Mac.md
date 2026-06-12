---
title: "Filesystem Choice for Fileserving to Microsoft Machines"
date: 2006-03-03
forum: General Help
---

### Post by fairyliquidizer on 2006-03-03
Hi!

I'm new to using Linux for file serving/backup but want to setup Ubuntu as a server for a couple of apps (music stuff) with the files stored on a partition on the Ubuntu box that XP can drop files in.  I also want to do some backups to Ubuntu.

What filesystem is best given that I want this data to be stored for many years to come but be accessible from an XP box?

Should I use VFAT and SAMBA?  or just ReiserFS and SAMBA ?  Please point me in the right direction.

Cheers,
Fairy

---

### Post by AndyCooll on 2006-03-03
Assuming that by saying "Ubuntu server" you mean a separate Ubuntu box, then Ext3 or Reiser with Samba will be fine.

:cool:

---

### Post by fairyliquidizer on 2006-03-03
Cool.  So Ext3 or Reiser seams like a good choice.  Any preferences?  Bear in mind I want something that I'll be able to access even if my distro gets updated/changed.

Yes I've got one box that's a small form factor box that I've just installed Ubuntu on (after being away for a while from Linux) and my desktop client (XP) and my Squeezebox.

I intend to run:

Slimserver
Music Magic Mixer (Predixis)
BOINC

and use the PC as a SAN.

In terms of backing up XP files on my Ubuntu box and moving odd documents to the Ubuntu server what is the best method?  Are SAMBA shares vulnerable to XP viruses?  (Not that I have ever lost anything to a virus)

In addition is VNC the best way to access an Ubuntu box from XP for admin etc?  The Ubuntu box will not have a keyboard or mouse connected.

Thanks,
Fairy

---

### Post by BoneKracker on 2006-03-03
ext3 is your safest choice.

You may gain some performance with reiserfs, with some potential stability loss.  (If you don't have clean power or crash your rig occasionally, you may want to stick with ext3.)  If you do choose reiserfs, you may get an incremental risk/performance tradeoff by using mount option "notail" (and perhaps "noatime").

If you are using disk-striping (RAID-0, etc.), you might get better performance from using the XFS filesystem.

There is documentation online about the various filesystem alternatives.

---

### Post by AndyCooll on 2006-03-03
No you won't have any XP related vulnerability problems because the files are on a Linux box (and all the security factors this brings). Of course, if one of those files has a virus on it and is then opened on the XP machine that's a different issue. It would affect the XP machine not the Linux box.

And yes, you can use VNC for admin will work fine. Using FreeNX would be even better IMO.

:cool:

---

