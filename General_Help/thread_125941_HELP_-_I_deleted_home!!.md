---
title: "HELP - I deleted /home!!"
date: 2006-02-05
forum: General Help
---

### Post by andrewsawyer on 2006-02-05
Ok, not such a good thing.  But I'd really appreciate if someone could help me out.  My dad has installed Ubuntu on his computer (he's in the UK and I'm in Australia).  He set up two partitions, one for /home and one for /root however didn't specify at install time to mount the home partition, and so the /home folder got set up in the main partition, leaving the much larger one empty.

I ssh'd into his computer to help him set up some stuff - open all the repos, update, install Skype etc etc, and also copy the /home directory over to the new partition.

Well, I copied it over, however ended up with it in /home/home/(username) rather than just /home/(username).  I tried to correct this, but somehow managed to delete it - don't ask!

I still have the /home structure on the main partition, but there is nothing on it (it was a clean install, so I figure it will be easier to just create new user accounts).  I really do need to get this sorted though!

I have tried ```
useradd -gusers -s/bin/shell -pwhatever -d/home/user01 -m user01
```

However he still can't log into gnome.  He is getting an error about his .dmcc file.  For what it's worth, the new /home partition is mounted as vfat (so he can swap and change between windows and linux).

It is mounted in fstab as:

```
/dev/hdb3       /home  vfat    iocharset=utf8,umask=000   0       0
```

As it is, there is a /home/user01 directory however it is empty.  He can't log in - well he could probably get to the xterm, but that would be it, and I obviously feel real bad for messing it up!

Please help me!

---

### Post by stoffe on 2006-02-05
There should be plenty of utilities for this on the net, try a google for "undelete fat32" and similar searches. It might be that all you will find is windows programs though, but there was a windows installation too, yes?

---

### Post by mdmarmer on 2006-02-05
At this point not much to lose by re-installing.  If home is lost, most things are lost anyway.  Difficult to try to recover the data across the pond

Mike

---

### Post by andrewsawyer on 2006-02-05
Hiya,

Windows is installed yes - however on a different drive.  I'd really rather not reinstall, as we had just set up the wacom tablet which had taken a good while.  There was nothing in the /home directory - just the .dmcc and those type of files.  Is it not possible to recreated them by making a new user profile?

---

### Post by jkka on 2006-02-05
[QUOTE=andrewsawyer] There was nothing in the /home directory - just the .dmcc and those type of files.  Is it not possible to recreated them by making a new user profile?[/QUOTE]

Yes, you can actually empty the whole /home/user -directory. Just make sure the user has full rights to the folder. All needed files will be recreated.

---

