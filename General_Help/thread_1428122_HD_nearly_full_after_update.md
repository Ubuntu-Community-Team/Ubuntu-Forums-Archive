---
title: "HD nearly full after update?"
date: 2010-03-12
forum: General Help
---

### Post by Giradman on 2010-03-12
I have Ubuntu 8.04 on an IBM laptop w/ 18 GB HD & 512 MB RAM - the HD in the past was just half full; today (after not using the laptop for several weeks), I needed 64 or so updates which seemed to progress fine; however on re-booting and checking the disc analyzer, the HD is now 97% FULL!

I was wondering if perhaps the updates installed did not clean up previous software leading to many files being left on the HD - I've never ran into this situation before, and would like some advice as to my first steps in figuring out this problem.

Thanks!  Dave

---

### Post by philinux on 2010-03-12
What does this command show.

```
df -h
```

You can read this too.
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)

---

### Post by Giradman on 2010-03-12
Thanks for your response - I took a screenshot of the output from the command suggested, but cannot use Firefox on the laptop - assume related to the HD being nearly full?  Now on my Dell VISTA!

But, the top line states:

/dev/sda1     Size 18 GB Used 18 GB Avail 0 Uses% 100% / mounted on

The remaining entries for Size are 248 MB

Also, when I scan the Filesystem, the root label, i.e. / states 100% usage (complete red bar) w/ 67.9% in the 'media' bar; clicking on that down button indicates 100% disk usage, but all of the bars below that one show minimal if any usage?

Let me take a look at your link - thanks again!  Dave

---

### Post by philinux on 2010-03-12
Well just to quickly see if we can get you some space try this.

```
sudo apt-get autoremove

and

sudo apt-get autoclean
```

Check your trash and then roots trash with gksu nautilus.

---

### Post by Giradman on 2010-03-12
OK - I did the two commands suggested; and looked at the root thrash (just a desktop folder listed) and emptied the regular trash bin.

Reran Disk Usage Analyzer which now reads 96.6% full, so a minimal decrease - thanks again.  Dave

---

### Post by Giradman on 2010-03-12
Just curious - since 67+% of the apparent disc usage was listed under the disk/media folder, I took a look in that area - there are about 2 dozen folders w/ dates - I assume these relate to the updates that have been done in 2009 & 2010 - looking at the folder for today (after I did some 64 updates), there is an item labeled files.tgz (assume like a zip file from the updates) - this measures 1.1 GB in size; there are TAR archives of similar size in some of the other folders - I suspect that much of my disk space is in this area?

Are these important to keep? And if not, how should each be removed?  Any other suggestions would be appreciated - thanks.

---

### Post by drs305 on 2010-03-12
Take a look at the following thread. It details how to investigate and solve several of the most common "disk full" problems (root trash, backups to the wrong partition, log files gone wild, etc):

[http://ubuntuforums.org/showthread.php?t=1122670]("http://ubuntuforums.org/showthread.php?t=1122670")

And when trying to detemine / "disk full" problems, it's best to unmount all other partitions, which may be hiding the problem underneath an existing mount point. My initial guess is that a backup was made to / instead of to a partition that wasn't mounted at the time of the backup.

---

### Post by philinux on 2010-03-12
> **Giradman said:**
> Just curious - since 67+% of the apparent disc usage was listed under the disk/media folder, I took a look in that area - there are about 2 dozen folders w/ dates - I assume these relate to the updates that have been done in 2009 & 2010 - looking at the folder for today (after I did some 64 updates), there is an item labeled files.tgz (assume like a zip file from the updates) - this measures 1.1 GB in size; there are TAR archives of similar size in some of the other folders - I suspect that much of my disk space is in this area?

Are these important to keep? And if not, how should each be removed?  Any other suggestions would be appreciated - thanks.

Could be backups you or the system created.

---

### Post by Giradman on 2010-03-12
> **Giradman said:**
> Just curious - since 67+% of the apparent disc usage was listed under the disk/media folder, I took a look in that area - there are about 2 dozen folders w/ dates - I assume these relate to the updates that have been done in 2009 & 2010 - looking at the folder for today (after I did some 64 updates), there is an item labeled files.tgz (assume like a zip file from the updates) - this measures 1.1 GB in size; there are TAR archives of similar size in some of the other folders - I suspect that much of my disk space is in this area?

Are these important to keep? And if not, how should each be removed?  Any other suggestions would be appreciated - thanks.

These appear to be backup file folders - not sure why so many appeared?  I went ahead and removed all of the ones from 2009 and ran the disc analyzer which stated that I was now at 60% capacity; however, on re-booting the machine, I was back to the issue from my OP, i.e. full disc capacity indicated! :x

Now I looked at both links given previously - not sure I completely understand all of the terminology (I'm not much of a BASH user - probably should be!).  The command that seem to give me some information was that looking for files > 1GB - all of these were in the TAR archives mentioned before in the quoted earlier post.

Not sure 'where' to go from here - I've backed up my home folder onto an external drive - I have only one partition on this hard drive and nothing else is mounted at the moment.  If this problem is not resolved, I don't think that I can update to the next Ubuntu version (next month?) since I seem to have no disc space left to use!  Well, I await any other further suggestions - thanks again.  Dave

---

### Post by Giradman on 2010-03-12
OK - well tonight I've been re-reading the previous links and attempting the BASH commands suggested - now, I'm getting an X-authorization issue in trying to run these commands @ root!

Assume that my previous 'handy work' likely caused a new issue, so I'm further compromised on this computer.

In addition, when I try to 'close down' the computer by using the icon in the right upper corner, I am not getting the usual menu options; i.e. the desktop bars @ the top & bottom disappear, the desktop icons remain, but nothing else happens - I have to use the OFF button of the laptop - not sure if this may have cause one of the other issues.

Think that I may be 'hosed' w/ this installation unless someone has any bright ideas - suggestions please?  And in case (since I've saved my important 'home' files), what is the best way to wipe this HD and do a re-installation of the newest version of Ubuntu?  Thanks all - Dave

---

### Post by Giradman on 2010-03-12
Well, I think that the problem is resolved for the moment! :)

After another reboot, the available HD space had increased, so I decided to do an 'easy' migration from 8.04 to 8.10 - took a number of hours of downloading and re-installation, and a couple of re-boots to get my wireless internet connection working!

But, the 18 GB HD is now just half filled and the previous problems have disappeared - I'll work w/ this version for a while and hope that all stays well?

This is an 'old' laptop but the one I take 'on the road' so like the compactness and the safety of the Linux OS in hotels, etc.

Again, thanks for the advice - learned a lot from those links.

I'll put this thread as 'solved' for the moment at least - Dave

---

