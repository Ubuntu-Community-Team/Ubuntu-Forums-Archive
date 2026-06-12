---
title: "Automatic Partition Copy for Backups"
date: 2012-09-11
forum: General Help
---

### Post by Valkhorn on 2012-09-11
I'm not sure if this is the right forum or not but to me it seems like it should be in general help.

I'm a LAMP developer, and so far I haven't found a good way of doing backups on LAMP servers without simply booting into a gparted CD and copying a partition to a new drive or using Clonezilla. This means doing backups of my servers are a little more work than I want them to be because it requires that I log out of the server and reboot it to do a backup. 

I can't simply backup the /home directory or even the /var directory because there are other files in /etc and other places that are needed for custom configuration of the server. It's far easier (and quicker) to just clone a hard drive than to re-install apache and mysql and restore a few gigs of a mysql database.

Plus, I know with minimal additional configuration and two commands I can get a cloned hard drive to boot with absolutely no problem off of almost any hardware I throw at it. 

I can see the virtue of just backing up /home if it's a basic desktop environment, but with a AMP server (that also has python, java, and a few other goodies for development) I haven't yet come across any software that could (with root control) log out of the machine, do a direct partition copy, modify the /etc/fstab file with the new hard drive UUID, and do this on a consistent basis (every week perhaps).

I thought about just writing a shell script that could be crontabed or something, but before I do that is there any app or utility that can do this?

---

### Post by Valkhorn on 2012-09-20
I never got any reply to this - but I think what I'll have to do is to just boot into GParted every week or so and do a backup manually.

No program I've found so far will just do a raw hard disk copy. The copies are always seemingly limited to specific folders - and I'd have to copy things with sudo privs anyway and while I'm not logged into Ubuntu.

---

### Post by Tobeus on 2012-09-20
Have you checked out rsync yet?  I'm not sure if it is exactly what you are looking for, but upon initial inspection it appears to allow for live partition backup.  I also have a dev web server I'm looking at setting up a backup solution for similar to what you are going after, and this looked promising so I thought I would share it.

[https://wiki.archlinux.org/index.php/Full_System_Backup_with_rsync](https://wiki.archlinux.org/index.php/Full_System_Backup_with_rsync)

That's the article I came across where it talked a little about the partition backup, but I'm only beginning to look into it.  If you find anything, let us know.  I'm basically in the same boat.

Cheers!

-Tobeus

---

