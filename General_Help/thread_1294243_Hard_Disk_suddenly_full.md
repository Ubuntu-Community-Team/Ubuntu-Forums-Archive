---
title: "Hard Disk suddenly full"
date: 2009-10-18
forum: General Help
---

### Post by ^_Pepe_^ on 2009-10-18
Hi all.

Suddenly, Ubuntu said that my main partition is full. How? Full? All my media and information is out of there.

I've checked out this threat [http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573), with all my credits to the author (great), but I couln't find any full trash, any log or so.

Disk analyzer says a curious thing:


My /media/DOWNLOAD mount, that is a NAS disk, is reserved only for backups. It, currently has about 55GB of information that is the amount I miss in my /dev/sda5/ mount which is my / folder. But I can see 55GB in my NAS disk, either from other computers, and from the administration tool of the NAS. So, information is inside the HDD of the NAS, but seems to spend my boot partition space too.

:confused:

Any idea? Any help?

Thanks in advance.
Pepe

---

### Post by MartinEve on 2009-10-18
Is it possible that you have, at some stage, not mounted the NAS and put data onto the hard disk that is now being hidden by the mounted NAS?

I would suggest: Unmount the NAS. Have a look inside the mount point and make sure it is empty. If there are files inside, then, at some point, the mount failed and the data was written locally.

Also, if you know some of the file names that should only be on the NAS but you suspect might also be local, you can, after the same unmount from above, use "find name 'filename_pattern*'"

Hope that helps...

---

### Post by Paqman on 2009-10-18
> **MartinEve said:**
> 
I would suggest: Unmount the NAS. Have a look inside the mount point and make sure it is empty. If there are files inside, then, at some point, the mount failed and the data was written locally.


+1

I used to get that occasionally from backups, the trick is to modify your script so that it check that the share is mounted before running.

---

### Post by theozzlives on 2009-10-18
Do you have a seperate /home partition? My / has 4.8 GB free whereas my /home has 208.6 GB free. If my / gets filled up, it'll say I'm out  of space even though I still have over 200 GB free. If that's the case, it's as simple as resizing your partitions.

---

### Post by ^_Pepe_^ on 2009-10-18
Solved!

You were right!

There were some .ful backup files inside my "/" partition in /media/DOWNLOAD, but out of the NAS.

SHIFT+DELETE did the dirty work! 

Ah! I had to restart to see my free space again. Weird!

Thank you so much!!

^_Pepe_^

---

