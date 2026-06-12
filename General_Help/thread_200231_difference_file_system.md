---
title: "difference file system"
date: 2006-06-19
forum: General Help
---

### Post by syadnom on 2006-06-19
after much searching i cannot find the information im looking for.  btw, the answer here may help a post for edgy eft reccommends.

im looking for a differencing filesystem.  id like to be able to install ubuntu dapper and then start with that base install and mount a differencing filesystem over the top.  by this i mean the data in the original / partition would be read from but changes and additions would be written to a new filesystem mounted over the top.  those changes would then be read instead of the original.  the idea here is to have a single 'bulk' of the install and have upgrades/test upgrades written to the difference file...

i guess a theoretical mount script is the only other way for me to describe it


mount -t differencing -o base=/dev/hda3 /dev/hda5 /

and yes, i mean for / to include all other filesystems so my /home on /dev/sda1 would have changes written to /dev/hda5/home ... and /boot would instead of writing to /dev/hda1 write to /dev/hda5/boot

replace /dev/hda5 with -o loop /test_systems/diff_01_edgyeft
 etc etc etc.

any ideas, feasability??

i other search term i used was "transparent filesystem(s), file system(s)" with no luck

---

### Post by RAOF on 2006-06-19
I'd check out unionfs.  From the unionfs-utils package description:
[quote=aptitude]
Description: stackable unification file system - management tools
 The unionfs driver provides a unification file system for the Linux kernel. It
 allows to virtually merge the contents of several directories and/or stack them,
 so that apparent file changes in the unionfs end in file changes in only one of
 the source directories. 
 
 This package contains utilities needed to configure unionfs containers
 on-the-fly.
[/quote]

---

