---
title: "Full System Backup (which folders?)"
date: 2011-05-09
forum: General Help
---

### Post by q-sens on 2011-05-09
Hello,

I've started using [COLOR="DarkOrange"]Ubuntu 11.04 Natty[/COLOR] a few days ago and as i want to learn, i'm messing a bit with things and sometimes break my system... xD

I've installed and tried many backup application and finally picked sbackup to set 1 backup per day.

At the moment the backup is including the following:
[COLOR="SeaGreen"]/var
/home
/usr/local
/etc[/COLOR]

Exluding:
[COLOR="DarkRed"]/media
/var/run
/var/cache
/var/spool
/var/tmp[/COLOR]

Do you think that is enough to restore the system if for example i have issues with audio, video or anything else.. or even a severely broken system?

[COLOR="DarkOrange"]A) Which folders should be added and excluded?[/COLOR]
As i have a lot of free space, i would like to backup as much as possible.

I first tried with the whole root / but restoring failed and just froze the system... :(
(Deja Dup)

[COLOR="DarkOrange"]B) Do you know any application that would take full backups and full restore of the  root / ?[/COLOR]

Thank you by advance!

---

### Post by nothingspecial on 2011-05-09
I would backup everything except /proc /lost+found /sys /mnt /tmp and /media

The reason /media is excluded is that it where your external drives are auto mounted.

If you want to include stuff on external drives include media, but exclude where your backup is going.

---

### Post by CVGH on 2011-05-09
All fine and good backing that stuff up, but how do you put it back into a new install?

I used simplebackupsuite and did /etc/home and /var.

Putting /etc and /var back broke many applications.....

So I'm only doing /home and reinstalling the programs from scratch....

---

### Post by q-sens on 2011-05-09
@nothingspecial
Thanks for your advice. I'll add everything but the folders you listed in your post. Do you use a script or an application for your backups?

@CVGH
My intention is not to reinstall the system but simply to restore it to a previous state. For example if i break something i can simply restore my system to the previous day state.

---

### Post by dragonfly41 on 2011-05-09
This link I bookmarked since it provides helpful information on backup strategy.

[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

---

### Post by fabricator4 on 2011-05-09
> **q-sens said:**
> 
Exluding:
[COLOR="DarkRed"]
...
/var/cache
[/COLOR]

I have a different approach, which includes backing up /home and /var/cache/apt/archives.

The latter is where all the downloaded .deb files are kept - all of the updates and all of the installed software.  When I install a new system (or re-install an old one) I put the debs back before running updates or installing software.  If the .debs are there, the system uses them again instead of downloading all over again.  This saves _heaps_ of download time and bandwidth.  I also share debs between three systems all running 10.04.  Heaps of time saved X3.

Chris

---

### Post by q-sens on 2011-05-09
@dragonfly41
Thanks for the link!
I'll have a close look.

@fabricator4
Thanks for your advice.
I removed /var/cache/ from the excluded folders.

---

### Post by nothingspecial on 2011-05-09
> **q-sens said:**
> @nothingspecial
Thanks for your advice. I'll add everything but the folders you listed in your post. Do you use a script or an application for your backups?


```
#!/bin/bash

before="$(date +%s)"; sudo tar --same-owner -cpvzf /media/Backup/10.04_Backup_09-28-10.tgz --exclude=/proc --exclude=/lost+found --exclude=/sys --exclude=/mnt --exclude=/tmp --exclude=/media /; after="$(date +%s)"; echo "Elapsed time: $(expr $after - $before) seconds."; echo -e "\a"

exit 0
```

source [http://openubuntu.com/index.php/topic,671.0.html](http://openubuntu.com/index.php/topic,671.0.html)

---

### Post by q-sens on 2011-05-12
> **nothingspecial said:**
> ```
#!/bin/bash

before="$(date +%s)"; sudo tar --same-owner -cpvzf /media/Backup/10.04_Backup_09-28-10.tgz --exclude=/proc --exclude=/lost+found --exclude=/sys --exclude=/mnt --exclude=/tmp --exclude=/media /; after="$(date +%s)"; echo "Elapsed time: $(expr $after - $before) seconds."; echo -e "\a"

exit 0
```

source [http://openubuntu.com/index.php/topic,671.0.html](http://openubuntu.com/index.php/topic,671.0.html)

Nothingspecial, thank you again.

To make it simple, i can backup the whole system root and just exclude the following:
[COLOR="DarkRed"]/proc
/lost+found
/sys
/mnt
/tmp
/media[/COLOR]

Now about restoring, is it possible to restore from my Ubuntu session?
Do i need to unmount the partition hosting my system before to restore?
Does the backup method upper would restore my system exactly as it was at the time of the backup?

I kept looking for a simple method but couldn't find any...
Using Sbackup or Deja dup is cool but what if i can't even log into my session, or what if the system fails loading...
Partimage seems not to be available for amd64... sounded like a good solution for me.

Thanks!

---

