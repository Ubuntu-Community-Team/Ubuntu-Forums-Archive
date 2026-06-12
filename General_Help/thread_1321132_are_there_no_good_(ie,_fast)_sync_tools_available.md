---
title: "are there no good (ie, fast) sync tools available?"
date: 2009-11-09
forum: General Help
---

### Post by jt_04 on 2009-11-09
I've tried rsync but it is only a copying tool, not a true 2-way sync.  Unison is exactly what I want, but extremely slow (takes 12 hours to sync my media over my home network).  

what I want is something like SyncToy for windows (gasp!).  i know, but synctoy is very fast and efficient.  it leaves a small file in each directory so it doesn't have to transfer an entire dir to compare changes.  

is there a sync app for linux that is FAST between remote systems??

---

### Post by jt_04 on 2009-11-13
in case anyone cares:

apparently the answer to my issue lay in the way I was using unison.  I had mounted my remote system as a samba share and had set up unison as if they were two local directories.  by setting up unison to ssh to the remote system, the sync time dropped tremendously and now is very fast.  unison is still the way to go.

---

### Post by Giblet5 on 2009-11-13
No, rsync is a full sync program that can perform any type of synchronization, local, remote, full master/slave, master/master, slave/master, or slave/slave.

Don't buy the Unison hype about rsync being "unidirectional". It isn't unless you use it that way. Unison is pushing Unison AND NOTHING ELSE WILL POSSIBLY WORK!!! ;)

That said, unison is better than rsync for some purposes, for others, Stonebranch's file management tools are far superior.

For Windows, Unix, and Linux, I use rsync because it's always there and it will do anything you need done.

---

### Post by jt_04 on 2009-11-14
could you give me an example of how to run rsync bidirectionally between master/master?

---

### Post by The Cog on 2009-11-14
This is the script I use. I added a launcher for this script to my menu.
It syncs with my home server by updating in both directions. 

If there is a route to 192.168.1.0 in the routing table then it knows it's at home and calls the internal address. Otherwise it tries to connect to my public address.

It works whether I'm on my local LAN at home or out and about.

It tunnels through SSH which I have set up for passwordless keys, but could just as easily sync over OpenVPN using rsyncs own protocol (just remove the "--rsh=ssh"). 

As an example of usage, I have a calendar.ics file in ~/Sync which I have told Sunbird to use on all my PCs. And an encrypted spreadsheet with all my other passwords in it.
```
#!/bin/sh
LOCALDIR=$HOME/Sync/
REMOTEDIR=$HOME/Sync/
if /sbin/route -n | /bin/grep -q '^192.168.1.0 ' 
then 
    SERVER=192.168.1.103
else
    SERVER=my.public.address.here
fi
echo Syncing with $SERVER
echo Sending...
rsync --rsh=ssh -aizuKL $LOCALDIR $SERVER:$REMOTEDIR
echo Fetching...
rsync --rsh=ssh -aizuKL $SERVER:$REMOTEDIR $LOCALDIR

```

---

### Post by jt_04 on 2009-11-14
thanks for the script...that's pretty much what i've tried in the past (just running sync a second time in the opposite direction).  my question is how that method handles deleted files.  

for instance, if a file exists on both servers, but then i delete it from server2, and then run

rsync -havu server1 server2
rsync -havu server2 server1

rsync will re-copy the file from server1 to server2 instead of deleting it off server1.  by the time the second command runs the file exists in both locations again and it doesn't know anything is wrong.  

is this right?  this is what i've seen in my local tests, and I haven't found a way around it, besides using unison.

---

### Post by The Cog on 2009-11-14
You're right. That script will recreate files that have been deleted. To reproduce the deletion of a file would require keeping a separate record of what used to be there in order to know something has gone. rsync doesn't do that.

---

### Post by fisheater on 2009-11-14
> **jt_04 said:**
> in case anyone cares:

apparently the answer to my issue lay in the way I was using unison.  I had mounted my remote system as a samba share and had set up unison as if they were two local directories.  by setting up unison to ssh to the remote system, the sync time dropped tremendously and now is very fast.  unison is still the way to go.

Hi, can I ask how you mounted your remote system in samba? I have been trying to get my NAS on my home network mounted so I could use rsync/gsync/backintime (or anything) to do backup. Im new to Linux, and its been a bit puzzling.

I used dmizers workaround ([http://www.ubuntuforums.org/showthread.php?t=288534](http://www.ubuntuforums.org/showthread.php?t=288534)) with limited success ([http://ubuntuforums.org/showthread.php?t=1217797](http://ubuntuforums.org/showthread.php?t=1217797)). Likely due to my ability to understand what I need to be doing.

This is my setup:
Cable internet
- wireless router
o laptop 1 - wireless (wireless router assigns IP)
o laptop 2 - wireless (wireless router assigns IP)
o Desktop via LAN cable (wireless router assigns IP)
o Printserver via LAN (wireless router assigns IP)
o NAS via LAN (static IP, option set in NAS setup)

Thanks!

FE

---

### Post by jt_04 on 2009-11-15
i can tell you what I did and maybe that will help you.  I followed [this guide here]("http://ubuntuforums.org/showthread.php?t=202605") to set up a samba server on my main ubuntu computer, which is then accessed by my laptop (windows) or htpc (ubuntu) over my local network behind my router.   

One big thing that you might want to check is if you have a firewall blocking ports 137, 138, 139 445 on the samba server.  type "sudo ufw status" to check.  if ufw isn't enabled, enable it via sudo ufw enable and open the ports with:

```
sudo ufw allow proto udp from 192.168.1.0/24 to any port 137
sudo ufw allow proto udp from 192.168.1.0/24 to any port 138
sudo ufw allow proto tcp from 192.168.1.0/24 to any port 139
sudo ufw allow proto tcp from 192.168.1.0/24 to any port 445
```

then I mount the share on my htpc with this line in my fstab:

```
sudo mount -t cifs //192.168.1.100/MyFiles /mnt/shared/ -o credentials=/home/user/.credentials
```

does that help?  i'm not sure what to tell you about that thread you are referencing, it looks specific for utf8 encoding and i'm not even sure that that is.

---

### Post by leorolla on 2009-11-25
The Cog,

But that is exactly what Unison does, right?

Is there any better tool to do that job?

I would like to know about it...

---

### Post by Pablo Alonso on 2010-04-10
> **jt_04 said:**
> in case anyone cares:

apparently the answer to my issue lay in the way I was using unison.  I had mounted my remote system as a samba share and had set up unison as if they were two local directories.  by setting up unison to ssh to the remote system, the sync time dropped tremendously and now is very fast.  unison is still the way to go.

Hi to all !

I'm having today the same issue as commented by Jt_04

I was previously using to win2003 boxes to sync folders with microsoft DFS and it worked incredibly fast.

Now I have migrated the first box to ubuntu karmic 9.10 to start getting free from M$ bond.

I'm interested in the solution you have found, I'm a little bit desperate.
I'm comming from a win2003 DFS replication and find unison slow to death!
DFS works keeping a hidden directory with the database to follow changes. I'm using unison right now as you also mentioned mounting the win2003 share into ubuntu box and sync as if they were two local dirs.

my setup:
side1  ->  server ubuntu 9.10
side2  ->  server win2003 (by now, i will convert to ubuntu in near future but y have to still wait more)
link bandwidth 256kbps ~(16KB/s)
Folder Size to Sync ~(1GB)

previously win2003 replicated changes instantly when any side modified, unison lasts more than six hours to do the comparison!!! it's impossible to offer this as a solution!....

I need something else.

Please if someone knows how to implement unison in any other way that makes it faster or how to use any other replication tool that do this job well I'll be life thankful!

Regards
Pablo Alonso

---

### Post by Cue2 on 2010-11-08
> **The Cog said:**
> You're right. That script will recreate files that have been deleted. To reproduce the deletion of a file would require keeping a separate record of what used to be there in order to know something has gone. rsync doesn't do that.


I know this is an old thread but this is still quite high in a google search for file sync. The --delete option can help with deletes can it not? you can either cascade the deletes by including it in both directions or make it so it is only deleted if deleted on the "master" directory by doing it only one way.

---

