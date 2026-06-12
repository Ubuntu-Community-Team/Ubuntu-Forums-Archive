---
title: "BU script filled / partition log in not possible"
date: 2010-08-14
forum: General Help
---

### Post by jamesisin on 2010-08-14
I ran the following B/U script:

```
# redirect from script --> sends all STDERR to log file
# run in cron [0 4 * * 1 /home/[scriptpath] >/dev/null 2>&1] Mondays at 4 AM

budate="date +%Y%m%d"
exec 2> /home/[username]/Desktop/$budate # use dated folder on desktop



## backup Tunage


if ! mountpoint -q /media/TunageBU
then
   mount -t [filesystem] -U [UUID] /media/TunageBU
fi

# Note rsync -a copies permissions but will not copy owner:group if not run as root

rsync -ailS --delete --progress /media/Tunage/iTuna /media/TunageBU

umount /media/TunageBU


## backup Tonage


if ! mountpoint -q /media/TonageBU
then
   mount -t [filesystem] -U [UUID] /media/TonageBU
fi

# Note rsync -a copies permissions but will not copy owner:group if not run as root

rsync -ailS --delete --progress /media/TonageBU/Zoom /media/TonageBU
rsync -ailS --delete --progress /media/TonageBU/BB /media/TonageBU

umount /media/TonageBU
```

As you can see, / should not be written to at all.  However, at some point I received a drive-full error and rebooted the machine.  I am now unable to log in through Gnome ("The configuration defaults for GNOME Power Manager have not been installed").

I am able to ssh into the machine (as root if necessary), but can't find the fat to delete it.  I looked in /var/backups (empty) and in /tmp and /var/tmp (also devoid of anything interesting).

A little help?

(Is there a problem with my script?  Why did / fill itself up?  How do I correct the matter at hand?  How do I get my script to backup without filling / (none of the backups are for or to the / partition)?)

Thanks.

---

### Post by jamesisin on 2010-08-14
Also, I found a folder called /home/username/T which is loaded with files in folders according to extension (wave, zip, pgn, &c).  What is this doing here?  Is it something new or perhaps related to this issue?

---

### Post by jamesisin on 2010-08-14
I successfully moved /home/username/T onto a different partition, but df -hk still shows my / as 100% (which is unlikely).

I really need to get back on this machine.  Can anyone help out?

---

### Post by fast_ian on 2010-08-14
You did check /var/logs right? [Actually, /var/*]

Can you mount it? Get a shell? [I'm assuming yes, at least via SSH?]

Then, I guess, "man find" ;)  Something like "find / -size gt10000 -print" [That's not right, but it'll give you a heads up on any big files, anywhere under "/" once you get the syntax......]

However, who is "username/T"?.... Sounds like you've got no idea what (s)he is and/or what all that stuff you just moved actually is?..... I dunno 'bout that :-)

Cheers,
Ian

---

### Post by jamesisin on 2010-08-14
> **fast_ian said:**
> You did check /var/logs right? [Actually, /var/*]

Can you mount it? Get a shell? [I'm assuming yes, at least via SSH?]

Then, I guess, "man find" ;)  Something like "find / -size gt10000 -print" [That's not right, but it'll give you a heads up on any big files, anywhere under "/" once you get the syntax......]

However, who is "username/T"?.... Sounds like you've got no idea what (s)he is and/or what all that stuff you just moved actually is?..... I dunno 'bout that :-)

I didn't see anything of interest in the logs.  It's possible I overlooked something, of course, but I don't know what I might look for in specific.  For example, rsync is not mentioned.  I went through other parts of /var by date (looking for activity today) and didn't see anything exciting either.

The folder called T, it turns out, was related to a recovery operation I performed months ago.  It was about 2.5 GB and it is now sitting on a different drive out of the way.  However, even after moving those 2.5 GB df still shows / and /var/lib/unreadahead/debugfs at 100% (there is nothing in degubfs, by the way).

(As a general rule, I sanitize usernames and machinenames.)

---

### Post by jamesisin on 2010-08-14
Ok, I've figured some of this out.

This section:

```
if ! mountpoint -q /media/TunageBU
then
   mount -t [filesystem] -U [UUID] /media/TunageBU
fi
```

is supposed to check to see if /TunageBU is mounted and if it is not to then mount it.  This seems to have failed and thus rsync went ahead and created a *folder* at /media for the sync operation.

Can anyone help with this scripting question?

---

### Post by jamesisin on 2010-08-14
There was an error in my script (in the mount commands).  I have corrected that error and my script ought to function as expected.  We shall see.

Thanks, Ian, for helping out.  I appreciate it.

---

### Post by jamesisin on 2010-08-15
For those interested, I have written a blog post on this matter.

[Backup Script: A Love Story]("http://www.soundunreason.com/InkWell/?p=2313")

---

