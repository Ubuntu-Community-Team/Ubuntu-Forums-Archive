---
title: "Troubleshooting low disk space"
date: 2009-10-08
forum: General Help
---

### Post by NinjaNumberNine on 2009-10-08
I have a relatively new** [COLOR=Black][COLOR=RoyalBlue]*e*[/COLOR]machine[/COLOR]** desktop PC, with a GB and a half of ram and a 35GB hard drive. I run Kubuntu Jaunty on it 2 months and this morning it pops up a "FreeSpaceWidget" thingy that says I'm running low on disk space, so I look in the Home folder but there is only 5GB of MythTV recordings and I don't need them so I delete them. That said, my problem is solved temporarily, but I wondered if there was some kind of utility that would let me troubleshoot **where** all the "stuff" is. 
 I.E. (not internet explorer lol) is there something that could show me in order from large to small the top ten "biggest" folders on the computer? 
 
  Thanks in advance,


NinjaNumberNine

---

### Post by NinjaNumberNine on 2009-10-08
bump

---

### Post by drs305 on 2009-10-08
Here's a guide I wrote about finding 'lost' disk space. It's based on Ubuntu but there are commands to sort things out as well.
[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

For example, this command searches for folders 1GB or larger:
```

sudo du / -h --max-depth=1 | grep '[0-9]G\>'

```

---

### Post by NinjaNumberNine on 2009-10-08
Thanks, I'm checking it out... :)

---

### Post by mechro on 2009-10-08
There should be a utility already available (it may be different in Kubuntu)

Applications/Accessories/Disk Usage Analyzer though I don't know whether it will give you the info you require.

---

### Post by NinjaNumberNine on 2009-10-08
Hmm... seems that four files are taking up 20 GB- that's a little weird... seems like there's some kind of backup utility that creates an entire system backup and does not replace it when it makes a new one...
Here's the files, I deleted them, (maybe I shouldnt have?!)
```
/var/archives/Victory-home.20091006.master.tar.gz
/var/archives/Victory-home.20091004.master.tar.gz
/var/archives/Victory-home.20091005.master.tar.gz
/var/archives/Victory-home.20091008.master.tar.gz

```

By the way that was an excellent and comprehensive guide you wrote. I'm glad people have the patience to write them!

Thanks again!

---

### Post by drs305 on 2009-10-08
Glad you found what was taking up the space.

If you have a known backup program set up to run it is possible your backup partition is not being mounted before the backup begins. In that case, the backup will be created on the system partition. Sbackup is often the 'culprit'.

You could look at the time the files were created to see if they are all similar - indicating a backup triggered by an app or cron job.

If you delete them as root, make sure you use SHIFT-DEL or they will end up in root's trash bin and continue to take up space.


*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

---

### Post by NinjaNumberNine on 2009-10-08
> **drs305 said:**
> Glad you found what was taking up the space.

If you have a known backup program set up to run it is possible your backup partition is not being mounted before the backup begins. In that case, the backup will be created on the system partition. Sbackup is often the 'culprit'.

You could look at the time the files were created to see if they are all similar - indicating a backup triggered by an app or cron job.

If you delete them as root, make sure you use SHIFT-DEL or they will end up in root's trash bin and continue to take up space.


*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*
Thanks, I don't use SBackup that I know of, but now that I know where the problem is, I can take a different approach. Also I had always wondered how you mark a thread as solved, thanks for the tip.

---

