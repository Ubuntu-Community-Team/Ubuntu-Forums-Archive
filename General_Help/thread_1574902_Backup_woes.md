---
title: "Backup woes"
date: 2010-09-14
forum: General Help
---

### Post by akav on 2010-09-14
I was on Mac OS X for several years before moving to Ubuntu. Time Machine was great -- a truly plug-and-play, set it and forget it backup solution. I never had to use it for a full recovery, though the selective file restoration came in handy several times.

My local files are now much more critical than they ever were under Mac OS X, as I have a lot of source code that I depend on. But despite that, I still don't have a backup routine in place under Ubuntu. Tools just seem sorely lacking. No, I don't need or expect an exact duplicate of Time Machine's functionality. Just a solid backup GUI would be swell -- ideally something that can make a complete, bootable backup. But even that seems to be a pretty gaping hole in Linux.

Back In Time promised to fill that hole. I've used it however, and I'm not impressed. First mistake is the default settings: it defaults to literally backing up nothing, and excluding .* (as if all of my config files don't matter). OK, so I add the root directory (/) to the include folders for backup. That should take care of everything, right? No, actually that backs up nothing, for some unexplained reason. Backing up my user Documents directory seems to work, but for some reason it doesn't traverse through all directories (as one would expect) from /. And yes, I did run as root.

Furthermore, it seems that Back In Time neither produces incremental backups, nor does it produce full backups that one may restore from. So it seems pretty lacking as a fully featured backup solution, even if one overcomes these hangups.

So does anyone have a good, regular backup routine in place? Mind sharing what it is?

I know there is another thread on this forum regarding backup, but it's over 100 pages at this point, and seems to be geared toward command line backup. I'm comfortable enough in the command line -- I use it all the time for the stuff it's best at. But must we use it just to do backups?

---

### Post by e79 on 2010-09-14
Just some thoughts :

LuckyBackup :

[http://luckybackup.sourceforge.net/](http://luckybackup.sourceforge.net/)

If you want a more solid solution, Bacula should do it :

[http://www.bacula.org/en/?page=home](http://www.bacula.org/en/?page=home)

And for complete bootable backups as in snapshots of some kind, you can try clonezilla or Ghost4Linux (G4L) but those has to be use while the PC is offline if I recall :

[http://sourceforge.net/projects/g4l/](http://sourceforge.net/projects/g4l/)

[http://clonezilla.org/](http://clonezilla.org/)


Hope this helps.

---

### Post by akav on 2010-09-16
> **e79 said:**
> Just some thoughts :

LuckyBackup :

[http://luckybackup.sourceforge.net/](http://luckybackup.sourceforge.net/)

If you want a more solid solution, Bacula should do it :

[http://www.bacula.org/en/?page=home](http://www.bacula.org/en/?page=home)

And for complete bootable backups as in snapshots of some kind, you can try clonezilla or Ghost4Linux (G4L) but those has to be use while the PC is offline if I recall :

[http://sourceforge.net/projects/g4l/](http://sourceforge.net/projects/g4l/)

[http://clonezilla.org/](http://clonezilla.org/)


Hope this helps.

Have you used any of these yourself?
None of them look like particularly attractive or approachable solutions...

Luckybackup is KDE software.

Bacula doesn't sound very approachable or suitable for desktop use:

> Bacula is a set of Open Source, enterprise ready, computer programs that permit you (or the system administrator) to manage backup, recovery, and verification of computer data across a network of computers of different kinds.

And the imaging software just isn't what I'm looking for; it's not ideal for regular backups.

---

### Post by anglican on 2010-09-16
I use "mondoarchive" which is in the repos and can make full or incremental backups. I found it easy to use and schedule (via cron). I've had to do complete (bare metal) restores a couple of times after hard disk failures and they went without hitch.

H

---

### Post by 101011010010 on 2010-09-16
Hello. 
I've been using "remastersys" for quite a while now and never had any problems. I prefer it to some other backup applications because it allows you to make a live cd/dvd of your system. I've used "Mondo" as well and found it to be very good also.

[http://www.geekconnection.org/remastersys/ubuntu.html](http://www.geekconnection.org/remastersys/ubuntu.html)

I hope you find something that works for you.
[B][COLOR=#0000ee]
[/COLOR][/B]

---

### Post by e79 on 2010-09-16
> **akav said:**
> Have you used any of these yourself?
None of them look like particularly attractive or approachable solutions...
 
Luckybackup is KDE software.
 
Bacula doesn't sound very approachable or suitable for desktop use:
 
 
 
And the imaging software just isn't what I'm looking for; it's not ideal for regular backups.
 
I tried luckybackup in my Gnome environment and it suited my needs at that time. I tried CloneZilla as well to snapshot some of my comps and it worked pretty well for this type of job. i'm sorry but I can't help you further as I did not test anything else. Hope you can find something that suits your needs.
 
Regards

---

### Post by CharlesA on 2010-09-16
Check up on this: [http://www.mikerubel.org/computers/rsync_snapshots/](http://www.mikerubel.org/computers/rsync_snapshots/)

---

### Post by akav on 2010-09-16
> **anglican said:**
> I use "mondoarchive" which is in the repos and can make full or incremental backups. I found it easy to use and schedule (via cron). I've had to do complete (bare metal) restores a couple of times after hard disk failures and they went without hitch.

H

I'll check into this, looking at the docs it doesn't look *too* bad.
Still no GUI, but meh, it's a one-time setup.

---

### Post by akav on 2010-09-16
> **CharlesA said:**
> Check up on this: [http://www.mikerubel.org/computers/rsync_snapshots/](http://www.mikerubel.org/computers/rsync_snapshots/)

See, this is the sort of thing I was talking about -- it's a helpful guide, as far as it goes. But wow... there must be 100 variables to consider in that guide. That's *100 chances to get things wrong*, for something as elementary as file backup. I can probably piece it all together, given a few hours. But really, I groan at the thought of putting all that effort in, and worrying that I didn't set this or that option correctly. And Joe Q Averager down the street wouldn't stand a chance.

This just seems to be a big hole in Linux desktop-oriented software now, and as a result I suspect that consistent backups are done pretty rarely among Linux users.

---

### Post by CharlesA on 2010-09-16
I do daily backups with rsync. :)

If you want the script, I can post it.

---

### Post by Baked- on 2010-09-16
Seconding rsync.   Im using it at work to backup 400GB of files 2x/day and it seems to work flawlessly.  here is a guide you may be interested in

[http://blog.interlinked.org/tutorials/rsync_time_machine.html](http://blog.interlinked.org/tutorials/rsync_time_machine.html)

Also I use clonezilla its pretty easy to use and serves its purpose well (disk-image type backups)

---

### Post by Ghost_Mazal on 2010-09-17
I also have a daily rsync run and once a week I image with Clonezilla. Nothing more than that is needed.

---

### Post by akav on 2010-09-19
> **Baked- said:**
> Seconding rsync.   Im using it at work to backup 400GB of files 2x/day and it seems to work flawlessly.  here is a guide you may be interested in

[http://blog.interlinked.org/tutorials/rsync_time_machine.html](http://blog.interlinked.org/tutorials/rsync_time_machine.html)

Also I use clonezilla its pretty easy to use and serves its purpose well (disk-image type backups)

This guide makes Rsync a little easier to understand, at least -- by limiting itself to the important options for backup, rather than covering every last available flag.

But I decided to give Deja Dup a shot, and it seems to fare much better than Back in Time for a GUI tool. Its approach is almost too simple, but it seems to get the job done (with incremental backup and scheduling) with a minimum of configuration.

It backs up the files to a bunch of .tar.gz archives, which makes the files inaccessible for cherry picking, or for restoration through any other tool. Still, it'll do for the primary purpose of protecting against catastrophic data loss.

---

