---
title: "create a new user with home on existing LUKS partition"
date: 2010-05-15
forum: General Help
---

### Post by DizzyCoder on 2010-05-15
Couple of things:
[LIST=1]
[*]I have a LUKS partition on an external drive where I keep my private data ( / is on SSD, 36GB, not big enough)
[*]just upgraded from 9.1 to 10.04
[*]my users/groups dialog doesn't let me create new users
[/LIST]
NOTE: since 9.x my users/groups has been botched.  I have to create my users from terminal, don't know why.. error when creating is "the configuration could not be saved | invalid data was found" (and I can't find anything on that error)

But that's not my problem.  I want to have multiple user accounts instead of sharing one login user, and have each users' data show up in their home folder.

From what I gather, I have a few roadblocks.
[LIST]
[*]/media/Secure must be mounted on login so that user settings can be parsed
[*]permissions must be proper in the users' home folder (my problems below)
[*]I can't for the life of me chown folders in /media/Secure (WTF?! does that have something to do with the mounting or LUKS?!?)
[/LIST]

So, I have to use terminal to create my user
```
sudo useradd dude
```
and then I log in as dude and move his home folder
```
sudo usermod -d /media/Secure/Dude
sudo rsync -aS /home/dude/. /media/Secure/Dude/.
```

Why don't I just move the /home partition?  b/c if I take that external drive with me away on business, my wife can't login as the regular user (who's home is mounted at /home and not at /media/Secure) 

When I log in as Dude I get an error that ICEauthority file could not be update... I tried chmod'ing it to 644 and made sure owner was set to Dude

then I get the error: There is a problem with the configuration server. (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)

if some one could point me in the direction of how this should be done then I can find my answers... I'm so lost at this point.

---

### Post by DizzyCoder on 2010-05-16
Welllll... I couldn't find a way around my roadblocks and the user editor thing was a little troublesome, so I followed this execellent post to reinstall and saved all my settings / reinstalled my programs (that dpkg --set-selections trick is wicked awesome)

[http://ubuntuforums.org/showthread.php?t=1034910](http://ubuntuforums.org/showthread.php?t=1034910)

To set up things the way I want, I've set up my EXT drive as encrypted /home and now I'm going to manually change the main logon users' /home to be /localhome/user in case I remove that drive containing /home

Then to have the drive auto unlock at login.  ;)

---

