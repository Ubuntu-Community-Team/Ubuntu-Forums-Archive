---
title: "push remote linked backup"
date: 2010-04-09
forum: General Help
---

### Post by sdacs_01s on 2010-04-09
Hi all,

I've been looking at various ways to backup several clients (laptops/desktops) to a linux-based NAS device (QNAP TS219 - ARM cpu) which runs an rsync/ssh server (on my home network).  I've looked at almost every program out there and I'd like to hear your thoughts on things below.

[COLOR="Blue"]Here is precisely what I need: [/COLOR]

* Push-style snapshot-style hard-linked backup - using 
rsync over ssh. 
* A widely used program that I can trust, otherwise it should be simple enough that I can manually inspect the code and learn what it's doing.

[COLOR="Blue"]Here is a narrowed down list of ways I've found to do this and my conclusions:[/COLOR]

1) rdiff-backup
This requires server-side software, thankfully the NAS device comes with ipkg and rdiff-backup was in the repo.
However, I don't like the concept of only storing reverse diffs for old backups, a small corruption is fatal. I want complete backup images (linked of course).   ie snapshot 
**Thus rdiff-backup is out...**

2) RlBackup
[http://www.math.ualberta.ca/imaging/rlbackup/](http://www.math.ualberta.ca/imaging/rlbackup/)
This looks promising, however it requires server side software which involves compiling rsync from source on the NAS device.  Not easy to do.   Also the program doesn't seem popular, and code is too complex (for me).  I will have a hard time understanding it and thus cannot trust it fully.
**Thus RLBackup is out...**

3) Raw and simple rsync wrapper/script
I've found many scripts that do this sort of thing on google and many of which are mentioned in Mike Rubel's article:
[http://www.mikerubel.org/computers/rsync_snapshots/#Contrib](http://www.mikerubel.org/computers/rsync_snapshots/#Contrib)
Most are quick example scripts and not of "package quality".   

I'm trying to find the most complete and popular script out there, preferably python or bashscript since I know a bit about those languages (unlike perl which will be a nightmare).

Brett Alton's script looks pretty interesting:
[http://ubuntuforums.org/showthread.php?t=639979](http://ubuntuforums.org/showthread.php?t=639979)
Currently I'm leaning towards Brett's script because from what I can tell, it will do what I need... and it looks short enough that I can understand it - given some time :)
It also seems he's iterated over it a few times and improved things.

[COLOR="Blue"]My question:[/COLOR]
Given my observations/conclusions above, what backup script/program would you recommend for me ?    

Any input would be much appreciated.

---

### Post by sdacs_01s on 2010-04-09
Is there a more specific sub-forum I can post this in ?   I realized it's a somewhat advanced topic but I couldn't find any place I can post "backup" related questions in.

---

