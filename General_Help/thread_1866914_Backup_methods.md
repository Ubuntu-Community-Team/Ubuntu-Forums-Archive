---
title: "Backup methods"
date: 2011-10-22
forum: General Help
---

### Post by NautiusMaximus on 2011-10-22
I've dabbled with Ubuntu a few times in the last few years, but I'm now making a serious attempt to kick the Windows habit and get an Ubuntu system set up that I can use for all my home computing needs. If that goes well, I may attempt to do likewise at work, but that's a whole nother story.

Anyway, before I do very much else with my system, I want to be sure I have automatic backup procedures in place (I'll be backing things up nightly to a network attached storage drive, and making occasional additional backups to DVDs manually).

I dare say I could set up a simple script using rsync and set it up as a cron job to do the automatic part, and perhaps that's the best way, but I was wondering if there are more user-friendly backup utilities that anyone could recommend?

I'm using Ubuntu 11.04 for now. May well upgrade to 11.10 before long.

---

### Post by ajgreeny on 2011-10-22
Keep with your idea of a script and rsync;  it is simple and effective.

---

### Post by ballantony on 2011-10-22
For must have docs, I've found Dropbox and ENCFS to encrypt the stuff I keep on there invaluable

---

### Post by Alwimo on 2011-10-22
Ubuntu 11.10 comes with a backup utility called Deja Dup installed. You can set these to automatically synchronise with Ubuntu One if you sign into that. Very easy.

---

### Post by galois1 on 2011-10-22
Take a look at Unison. It is an easy tool to synchronize two discs.

---

### Post by haqking on 2011-10-22
When i install a system, i take an immediate clone using clonezilla of the base build that can be restored in a few minutes.

I then add my common apps, drivers etc and basic configuration as well as updates, when i am satisfied everything works ok i take another clone of that as a more complete build.

Then i cron a rsync for personal files and evolution backup and thats it.

I have seperate partitions for / /home /boot /usr /tmp

Simple and quick to restore.

But it is personal preference and also depends on your system, but there are so many options.

You can also cron a tarball backup also which is common.

---

### Post by NautiusMaximus on 2011-10-22
Thanks for the quick responses!

OK, I think rsync sounds like the way to go, but my next question is how I refer to the external drives. It's incredibly easy to see the drives through the GUI: if I look at the file system, I have a "network" option to click on, and when I click on it, they're just there and I can open them and do as I will with them.

That seems to mount them when I do that; do I need to make sure the files are mounted before the rsync file will work?

If so, what's the best way of doing that? Can it be done in the same script I use for the rsync command, or is it better done via fstab? Any idea what syntax I'd need?

Sorry if these are really basic questions, still feeling my way with Ubuntu!

Thanks
NM

---

### Post by CharlesA on 2011-10-22
Easy - you'd mount them somewhere (I mount my backup drives to /backup) and then rsync to them.

You can have the script do that for you (mine does).

---

### Post by masgeeks on 2011-10-22
I use a few different backup methods, depending, but for a no-brainer automatic backup, Simple Backup works great, always has for me.  Search for it in synaptic or software center, sbackup and sbackup-gtk.

I do a nightly backup to a USB drive.  It has been flawless for years across many ubuntu versions.  I do check my backups on a regular basis and they have always been perfect.  Yo need to run it in admin mode, though, so you can schedule days/times for your backups to run...

Its simple yet flexible...  :)

---

### Post by haqking on 2011-10-22
> **masgeeks said:**
> I use a few different backup methods, depending, but for a no-brainer automatic backup, Simple Backup works great, always has for me.  Search for it in synaptic or software center, sbackup and sbackup-gtk.

I do a nightly backup to a USB drive.  It has been flawless for years across many ubuntu versions.  I do check my backups on a regular basis and they have always been perfect.  Yo need to run it in admin mode, though, so you can schedule days/times for your backups to run...

Its simple yet flexible...  :)

sbackup is ok, but has alot of bugs listed on launchpad, but it is all personal choice, if it works for ya then why change ;-)

---

### Post by NautiusMaximus on 2011-10-23
OK, I'm struggling here to mount the network drive via the terminal.

I can easily mount it via the GUI, but what syntax should I use?

I assume it's some kind of variant of

```
sudo mount [options] //[ip address of drive]/sharename /mountpoint
```

but the ones I've tried so far don't work.

Any ideas?

---

### Post by NautiusMaximus on 2011-10-23
Ah, OK, I've figured it out. Turns out I needed to install smbfs.

Odd that I could mount the drives easily via the GUI, though.

---

### Post by Alan5127 on 2011-10-25
> **NautiusMaximus said:**
> Ah, OK, I've figured it out. Turns out I needed to install smbfs.
 
Odd that I could mount the drives easily via the GUI, though.
 
Hi,
 
I am following a similar track. Can I just check that this is correct?
 
We can mount a drive via the GUI without installing anything extra, but to do it via the command line, we have to install SMBFS?
 
Obviously it works - it just seems unlikely to be necessary, but I am definitely no expert!
 
Thanks,
 
Alan.

---

### Post by Jacobonbuntu on 2011-10-27
if you want to make backups to a network storage, you might want it to automount on startup, as explained here in a pretty good way:
[http://www.mattvanstone.com/2007/11/automatically-mounting-windows-smb-shares-in-ubuntu-v3/](http://www.mattvanstone.com/2007/11/automatically-mounting-windows-smb-shares-in-ubuntu-v3/)

---

### Post by Alan5127 on 2011-10-27
Hi Jacob,
 
> **Jacobonbuntu said:**
> if you want to make backups to a network storage, you might want it to automount on startup, as explained here in a pretty good way:
[http://www.mattvanstone.com/2007/11/automatically-mounting-windows-smb-shares-in-ubuntu-v3/](http://www.mattvanstone.com/2007/11/automatically-mounting-windows-smb-shares-in-ubuntu-v3/)
 
Thanks for that.
 
Alan.

---

### Post by Jacobonbuntu on 2011-10-27
you're welcome!

---

### Post by killermist on 2011-10-29
I've been working on an automated backup procedure to backup (via cron) from several machines to a central storage machine running SSH and Rsync.

May not be exactly what you're looking for, but I decided ease of modification was key, so most of what needs tweaking should be easy enough, I hope.

Was wanting to take advantage of rsync's smart incremental backup system, and that took some effort to sort through, but I think it works quite well.

> 
$ du -hsc */*
126G	grace@grace/2011-10-27
626M	grace@grace/2011-10-28
676M	grace@grace/2011-10-29

64G	killermist@grace/2011-10-28
3.2M	killermist@grace/2011-10-29

2.0K	killermist@killermist/2011-10-28
2.0K	killermist@killermist/2011-10-29

191G	total
 (spaced out for a little clarity)

```

#!/bin/bash

# expects that password-less SSH key based authentication has already
# been configured on the client and server sides of the operation
# otherwise expect to enter user's SSH password/passphrase several times
# for commands passed to the server
# Date examples imply that "today's" backup is being done 2011-10-29

# config
## host name of ssh/rsync server
SYNCSERVER=torrents
## what to sync
SYNCWHAT=/home/`whoami`  #'my' home directory
## where to sync it, as the server filestructure would recognize it
BASEDIR=/mnt/torrent-pool/home-backups/`whoami`@`hostname`
## can be changed to taste if backups need to happen more often than daily, or whatever
NOW=`date +%F`
# end of config

WORKDIR=$BASEDIR/$NOW
NOWDIR=$BASEDIR/now
YESTERDIR=$BASEDIR/last
# assumes that /backup-path/last was left pointing to /backup-path/2011-10-28

#setup
ssh $SYNCSERVER mkdir -p $WORKDIR
# ex. /backup-path/2011-10-29
# may work without pre-creation, but why tempt fate?
ssh $SYNCSERVER rm -fv $NOWDIR
# ex. /backup-path/now
ssh $SYNCSERVER ln -s $WORKDIR $NOWDIR
# ex. /backup-path/2011-10-29 -> /backup-path/now

# act
rsync -aHP $SYNCWHAT $SYNCSERVER:$NOWDIR --link-dest=$YESTERDIR

# cleanup
ssh $SYNCSERVER rm -fv $YESTERDIR
# ex. /backup-path/last
ssh $SYNCSERVER ln -s $WORKDIR $YESTERDIR
# ex. /backup-path/2011-10-29 -> /backup-path/last
# so that tomorrow (2011-10-30), 'today sync' will be 'yesterday sync'
```

---

