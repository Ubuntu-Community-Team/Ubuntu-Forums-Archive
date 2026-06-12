---
title: "rsynch server tutorial"
date: 2012-01-06
forum: General Help
---

### Post by conradin on 2012-01-06
Hi all,
I am using Ubuntu 10.4.3 LTS, and I want to set up an rsynch server on my desktop that will periodically synch my laptops to itself, and the other laptops. I've never done it before, and I'm looking for a simple tutorial that can get me up and running fast.

---

### Post by papibe on 2012-01-06
Although you can set up the rsync daemon to implement that, I think using rsync over ssh would work just fine (I think it's easier to configure, too).

For unattended scripts I would recommend setting up ssh '[Public Keys]("http://principialabs.com/beginning-ssh-on-ubuntu/")' (so you can connect with no passwords).

For the backup schedule you can use [crontab]("https://help.ubuntu.com/community/CronHowto").

Does that help?
Regards.

---

### Post by x C0MMAND0 x on 2012-01-06
You can make a script like this:

```

#!/bin/bash
rsync -avt --delete /target /destination

```

Save it as "backup.sh" or whatever you want.

Make the script executable (chmod +x /path/to/file/backup.sh) and either manually run it (./backup.sh or right-click>execute) or you can set it up to run automatically via crontab.  Let me know if you need help setting up a crontab job.

```
man crontab
```

---

### Post by conradin on 2012-01-06
Thanks for the post backs.
I think I am confused. Is rsync just a way to push data on to a shared folder like a samba share?

---

### Post by papibe on 2012-01-06
It is much more than that.

It can sync directories remotely over a LAN or even the Internet. There are two protocols you can use:
[LIST]
[*]Setting an special service (rsync daemon), or
[*]Using rsync over ssh (which is encrypted).
[/LIST]
I personally use rsync over ssh to share family pics and videos with my brother who is out of the country.

I found this is a basic [tutorial]("https://calomel.org/rsync_tips.html") on how to do remote backups using rsync over ssh.

I hope it is a bit more clear now.
Regards.

---

### Post by killermist on 2012-01-06
This is the script I crafted, and tweaked to do my backups (as incremental dated backups, using hardlinking between them to save on prevented duplication, each dated backup capable of being copied out and then used without any special effort).


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
# assumes that $BASEDIR/last was left pointing to $BASEDIR/2011-10-28

#setup
ssh $SYNCSERVER mkdir -p $WORKDIR
# ex. $BASEDIR/2011-10-29
# may work without pre-creation, but why tempt fate?
ssh $SYNCSERVER rm -fv $NOWDIR
# ex. $BASEDIR/now
ssh $SYNCSERVER ln -s $WORKDIR $NOWDIR
# ex. $BASEDIR/2011-10-29 -> $BASEDIR/now

# act
rsync -aHP $SYNCWHAT $SYNCSERVER:$NOWDIR --link-dest=$YESTERDIR

# cleanup
ssh $SYNCSERVER rm -fv $YESTERDIR
# ex. $BASEDIR/last
ssh $SYNCSERVER ln -s $WORKDIR $YESTERDIR
# ex. $BASEDIR/2011-10-29 -> $BASEDIR/last
# so that tomorrow (2011-10-30), 'today sync' will be 'yesterday sync'

```

---

