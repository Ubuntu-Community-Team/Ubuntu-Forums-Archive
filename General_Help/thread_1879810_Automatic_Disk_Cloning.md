---
title: "Automatic Disk Cloning"
date: 2011-11-12
forum: General Help
---

### Post by Valkhorn on 2011-11-12
I've been trying to find a nice GUI program for Ubuntu that would let me do the following:

 * Clone my entire hard drive (bit by bit) onto another of any size as long as the space is there daily or weekly
 * Send this copy to either my fileserver (samba share), an external hard drive, a hot swappable hard drive, or any or all of the above
 * Be able to schedule this whenever I want
 * Be able to easily replace a hard drive with a clone if my primary hard drive goes bad

The reason for this is that I work from home on a LAMP server that I'd like to be able to duplicate and boot off of remotely with a laptop from some other drive. In other words, I'd like to copy my main hard drive frequently to some other, and take that hard drive with me with a laptop so I could boot off of it whenever I needed to - or even put that hard drive into a laptop and it just works.

It would take less time to copy my existing drive to another rather than reconfigure my LAMP environment and move all of my data/files over, and that way I can sync everything up. 

I've looked at bacula - but I can't seem to get it installed. I've also looked at Deja Dup and it's too simple, and I can't seem to get Grsync to open a samba share on the network.

Any thoughts?

I'm using Ubuntu 10.04. Thanks!

---

### Post by enkay009 on 2011-11-12
Some old school scripting might do the trick and setting up cron job.

At the heart of this would be disk dump (dd). You can use this dump your hard drive to a file. And then use it to restore it. BE VERY CAREFUL WITH THIS. A typo could screw up your hard drive.

To dump
```
dd if=/dev/sdx of=my_dumped_hard_drive
```

To restore:
```
dd if=my_dumped_hard_drive of=/dev/sdx
```

*However...* it would be simpiler if you just backed up your apache config, you mysql config, backup your database into a series of SQLs (redirect it to a file), and backup your web sites. Tar those up and then send them to your samba share. It would:

a) consume less disk space/bandwidth
b) avoid issues with machine specific configuration (drivers, network settings, resolution, etc.) and would allow you get to work quickly
c) allow you to get familiar with what's actually part of LAMP
d) be more or less OS/platform agnostic

Just my 2 cents...

---

### Post by sanderd17 on 2011-11-12
GUI method and automated don't go well together.

You can use clonezilla, as a GUI frontend to dd, or you can use plain dd (as explained above), or you can use rsync (it doesn't do clones, but it checks file diffs and only uploads the diffs to save bandwidth).

If you want to automate it, you will probably need to use some kind of cron.

I just wrote a little script with rsync for myself, so that's my personal favourite.

Please google a little, the arch wiki can also be of great help.

[https://wiki.archlinux.org/index.php/Backup_Programs](https://wiki.archlinux.org/index.php/Backup_Programs)

---

### Post by Valkhorn on 2011-11-12
> **enkay009 said:**
> Some old school scripting might do the trick and setting up cron job.

At the heart of this would be disk dump (dd). You can use this dump your hard drive to a file. And then use it to restore it. BE VERY CAREFUL WITH THIS. A typo could screw up your hard drive.

To dump
```
dd if=/dev/sdx of=my_dumped_hard_drive
```

To restore:
```
dd if=my_dumped_hard_drive of=/dev/sdx
```

*However...* it would be simpiler if you just backed up your apache config, you mysql config, backup your database into a series of SQLs (redirect it to a file), and backup your web sites. Tar those up and then send them to your samba share. It would:

a) consume less disk space/bandwidth
b) avoid issues with machine specific configuration (drivers, network settings, resolution, etc.) and would allow you get to work quickly
c) allow you to get familiar with what's actually part of LAMP
d) be more or less OS/platform agnostic

Just my 2 cents...

Apache config and mysql config won't work since a lot of my development documents and mysql restores that I test with are elsewhere. Plus I have a lot of external PEAR libraries, test frameworks, and other tools that I would need in the event of a hard drive crash. So, that wouldn't cut it. I have plenty of space free on other drives though and a full backup wouldn't take that much to begin with. 

I can setup another LAMP server if I need to, but if I don't need to, then why do that? I can setup a LAMP server, but it's not exactly a short process with all the stuff I need and use on a day to day basis. At one point I had a cheap laptop that I used as a duplicate environment, but it was a major pain synchronizing those things up all the time.

The idea is to be able to take my work with me if I have to go out of town for some reason by just picking up the hard drive, walking out of the door, and booting off of it later.

Also, most of the stuff I do for my main job is not OS Agnostic because it needs to modify the dev environment quite a bit, and relies on external programs that aren't PHP. Again, I see no reason to setup an entirely new LAMP server or restore a database and config files every time I want to take a laptop out of the house to do some work.



> **sanderd17 said:**
> GUI method and automated don't go well together.

You can use clonezilla, as a GUI frontend to dd, or you can use plain dd (as explained above), or you can use rsync (it doesn't do clones, but it checks file diffs and only uploads the diffs to save bandwidth).

If you want to automate it, you will probably need to use some kind of cron.

I just wrote a little script with rsync for myself, so that's my personal favourite.

Please google a little, the arch wiki can also be of great help.

[https://wiki.archlinux.org/index.php/Backup_Programs](https://wiki.archlinux.org/index.php/Backup_Programs)

I'll try clonezilla - I hadn't heard of that. 

I mentioned already rsynch isn't allowing me to do remote backups through the GUI - so I think that's a dead end. I don't need to worry about bandwidth either because I've got plenty of network bandwidth to do this. I have moved up to a few terabytes of data through my LAN without any noticeable slowdown or drawbacks.

I have googled quite a bit, and wouldn't have posted this if I hadn't. My original post said I found some programs, tried them, and didn't find them to be useful. That would imply that I had googled.

---

