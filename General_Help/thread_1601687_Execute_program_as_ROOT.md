---
title: "Execute program as ROOT"
date: 2010-10-20
forum: General Help
---

### Post by anereton on 2010-10-20
Hi,

I have a program ARES commander edition, from Graebert, and i having problems in save the drawing files, in certain folder (/media/Balthazar/Projects/[project name]) the file is in one partition, but this is the only program that presents that issue, so there a solution for that?

- Giving root previleges to oly this software? (how can i do that?)

- Twaeking the folder to give permission to this package to save normaly? (how)

- Cry, and suffer consequences, for being newbe in linux?

P.S: Balthazar is from Evangelion, my computer name is MAGI :)

If have a solution, can i create a launcher wiht that? 

rsrs

Thanks so much for helping me.

---

### Post by mikegarri on 2010-10-20
I'm not quite sure, but I'm pretty interested in this too [particularly the launcher aspect].  I tried making a launcher with the command "sudo [program]", but I believe it's waiting for a password in the background without giving me a prompt for it.  Does anyone else have an answer?

---

### Post by Vectorferret on 2010-10-20
gksudo in the launcher. But that is generally a bad idea (you don't want to run anything not absolutely necessary as root).

The easiest way to give permission to use those files is: use Alt-F2 to open a run program window and type "gksudo nautilus" in it. This will give you a root file manager. Navigate to the folder, right click on it and choose properties. From there you can use the permissions tab to change the permissions (and owner). 
If the folder is on a FAT or NTFS partition, you can't change permissions so you will have to mount the whole partition with those permissions by editing fstab. (Ask about that if needed.)

---

### Post by coabiguy on 2010-10-20
Well ... as you know, sudo asks for a password only on the first execution.
if you perform a man sudo, it tells you about the ASKPASS option.
I experimented with this and tried to create a simple "echo $PASSWORD" command file but kept getting "exec format error".

I searched for help on this but did not find anything useful.
I would be very interested in how to do this without invoking a graphical, enter password screen.

ANYWAY ... if you can live with invoking a graphical password screen, then try this.

  	 	 	 	p { margin-bottom: 0.08in; }  export SUDO_ASKPASS='/usr/bin/ssh-askpass'
 sudo -A ls -l /
 The first time you execute the sudo command it will open a graphical window that requests the password.

---

### Post by WorMzy on 2010-10-20
What is Balthazar, and how is it mounted?

If it is an NTFS partition, and you've created an entry for it in fstab to have it automatically mount, then add the following arguments to it's comma-separated mount options list (the fourth column):

```
uid=1000,gid=1000,umask=002
```

Replace uid and gid values with the uid and gid you want to use. (I've used the default user's UID and GID; if you're not the default user, then you can find out your UID and GID by opening a terminal and running "echo $UID" or "echo $GID" respectively.)

The umask value sets the file permissions to 775. (-rwxrwxr-x)

---

