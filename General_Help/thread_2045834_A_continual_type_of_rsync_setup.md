---
title: "A continual type of rsync setup?"
date: 2012-08-22
forum: General Help
---

### Post by Roasted on 2012-08-22
A random thought just popped into my head and I became curious how I would do this. Let's say I have a Linux box that does video surveillance. In top of that I have a second box on the lan for backups but have no external Internet connection to upload the data elsewhere. Is there a way to do a continual rsync style copying of data that runs around the clock so both boxes always have the latest feeds even if the cameras themselves are only hooked into one of the boxes?

---

### Post by sepo on 2012-08-22
Why don't create a share on the backup-box and config the camera-box to create there the images? 
This way you'll always have both machines sync'ed.

Then you can backup the share as you prefer.

---

### Post by drmrgd on 2012-08-22
If I understand you, it looks like you want to have an automated and frequent rsync command run based on time and not file presence (i.e. it runs at given intervals and not just when new files are detected).  If that's the case, I would recommend Rsnapshot ([http://rsnapshot.org/](http://rsnapshot.org/)).  I believe the smallest interval it can do by default is hourly, although as it's basically an rsync wrapper, I'd bet you could probably hack it to do more frequent syncs if you wanted.  You can also choose to version your backups with it so that it will keep (for example) 24 individual backups for a full day before starting to overwrite the oldest one.  

Not sure this is what you're looking for, but maybe worth a look.

---

### Post by LewisTM on 2012-08-22
You could try lsyncd
> lsyncd
daemon to synchronize local directories using rsync
 
Lsyncd (Live syncing mirror daemon) uses rsync to synchronize local
directories with a remote machine running rsyncd. Lsyncd watches
multiple directories trees through inotify. The first step after
adding the watches is to rsync all directories with the remote host,
and then sync single file by collecting the inotify events. So lsyncd
is a light-weight live mirror solution that should be easy to install
and use while blending
well with your system.
Cheers!

---

### Post by Roasted on 2012-08-22
> **sepo said:**
> Why don't create a share on the backup-box and config the camera-box to create there the images? 
This way you'll always have both machines sync'ed.

Then you can backup the share as you prefer.

I'm not sure I understand what you mean. It was just a thought that popped into my head. For example, say you're a shopkeeper and you have a Linux box running with video surveillance feeds saving to it. Okay fine. But you don't have an external connection to upload the feeds off site for identification purposes. Instead, you decide to put a 2nd box on site and within the LAN have a continual backup exist so that way if Mr. Robber decides to jack the first DVR he finds and runs, you at least have a secondary box.

Question is how do you keep the feeds perfectly synced between the two? After all, if a robber comes in and swipes the first DVR he sees, you've got a matter of 3-5 minutes worth of his presence being in the store... therefore an hourly rsync would make no difference.

I'm curious in an "rsync style" way to make sure the data on box A is the same as box B. Think of it like a RAID 1 mirror, except in different boxes. And sure, time lapses will exist, but I'd rather have a 30 second difference between synced boxes versus relying on hourly sync's which would make little/no difference in this particular scenario.

---

### Post by LewisTM on 2012-08-22
> **Roasted said:**
> I'm curious in an "rsync style" way to make sure the data on box A is the same as box B. Think of it like a RAID 1 mirror, except in different boxes. And sure, time lapses will exist, but I'd rather have a 30 second difference between synced boxes versus relying on hourly sync's which would make little/no difference in this particular scenario.
That is exactly what lsyncd does. It watches a directory and sends new or modified files to the target (backup) location on-the-fly. It does wait a few more seconds in case there are queued events but you should's have a blind spot of more than a few seconds, of course depending on the transfer speed and size of your pictures.

---

### Post by drmrgd on 2012-08-22
> **LewisTM said:**
> That is exactly what lsyncd does. It watches a directory and sends new or modified files to the target (backup) location on-the-fly. It does wait a few more seconds in case there are queued events but you should's have a blind spot of more than a few seconds, of course depending on the transfer speed and size of your pictures.

Thanks for pointing that out Lewis!  That looks to be quite a useful tool that I intend on playing with myself.  I had no idea that existed already, and I'm sure that is exactly what Roasted it looking for!

---

### Post by TheFu on 2012-08-22
Why not use block device replication like DRBD [https://www.ibm.com/developerworks/linux/library/l-drbd/index.html?ca=dgr-lnxw97LX-DRBD](https://www.ibm.com/developerworks/linux/library/l-drbd/index.html?ca=dgr-lnxw97LX-DRBD) ? This would be immediate replication.  GlusterFS is another option.

Or just setup RAID1 using multiple iSCSI devices.

Rsync is fantastic, but not really for High Availability, HA.  For backups, there are better tools than rsync too, but if you need a mirror for files every hour or day or week, then rsync is the right tool for the job. HA should be solved in a different way.  You really want a disk cluster.

---

### Post by Roasted on 2012-08-22
> **LewisTM said:**
> That is exactly what lsyncd does. It watches a directory and sends new or modified files to the target (backup) location on-the-fly. It does wait a few more seconds in case there are queued events but you should's have a blind spot of more than a few seconds, of course depending on the transfer speed and size of your pictures.

Awesome. Thanks for that. This looks very promising. How exactly is it used though? Would I just be writing a simple bash script to call on lsyncd? Or is it a more in depth setup process?

---

### Post by LewisTM on 2012-08-22
There is an in-depth [manual]("https://github.com/axkibe/lsyncd/wiki/Manual-to-Lsyncd-2.0.x") and the man page is also informative. Unless you have very specific needs you generally don't need to edit a config file, just run at startup
```
lsyncd -rsync sourcedir targetir
```
You say the other machine is on the LAN. Is it accessible by passwordless SSH or through a network share? That might affect the command syntax.

---

### Post by Roasted on 2012-08-23
> **LewisTM said:**
> There is an in-depth [manual]("https://github.com/axkibe/lsyncd/wiki/Manual-to-Lsyncd-2.0.x") and the man page is also informative. Unless you have very specific needs you generally don't need to edit a config file, just run at startup
```
lsyncd -rsync sourcedir targetir
```
You say the other machine is on the LAN. Is it accessible by passwordless SSH or through a network share? That might affect the command syntax.

Yeah - I always use ssh keys. I assume a correct "example" in finished form would be:

lsyncd -rsync /media/server1 administrator@192.168.1.10:/media/server2

eh? :guitar:

EDIT - looks to be that way... assuming SSH would work the same as local dirs, which I suspect it would. I ran this command:


jason@Area51:~$ lsyncd -rsync /home/jason/test/source /home/jason/test/destination

and it seems to have worked fine. I put 80MB worth of video clips into "source" and watched the destination folder. There's about a 15 second lapse, but it DOES work. Can't argue with that. :D Thanks guys!

---

### Post by LewisTM on 2012-08-23
Not quite:
```
lsyncd -rsyncssh /media/server1 administrator@192.168.1.10 /media/server2
```
Good luck!

---

### Post by Roasted on 2012-08-23
> **LewisTM said:**
> Not quite:
```
lsyncd -rsyncssh /media/server1 administrator@192.168.1.10 /media/server2
```
Good luck!

How is that accurate syntax?

When I rsync my data to my server on my LAN I use:

```
rsync -az --delete /home/jason/Pictures /home/jason/Documents /home/jason/Desktop /home/jason/"Ubuntu One" /home/jason/Dropbox /home/jason/kdenlive jason@192.168.1.150:/media/NAS/jason/DesktopUbuntu
```

In particular, taking note of:

```
jason@192.168.1.150:/media/NAS/jason/DesktopUbuntu
```

Works great here... *shrug*

---

