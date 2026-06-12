---
title: "Disk space warnings"
date: 2010-09-02
forum: General Help
---

### Post by kford on 2010-09-02
I'm a little puzzled as to why I'm getting a warning about running out of disk space.  It seems others have similar issues but with little resolve.  I'm hoping the horde can help.

I received a warning about how I have little disk space remaining.  I got the message when writing files to my /home directory.


The output of df -h is:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             7.4G  5.9G  1.1G  85% /
none                  984M  288K  983M   1% /dev
none                  988M  280K  988M   1% /dev/shm
none                  988M   76K  988M   1% /var/run
none                  988M     0  988M   0% /var/lock
none                  988M     0  988M   0% /lib/init/rw
none                  7.4G  5.9G  1.1G  85% /var/lib/ureadahead/debugfs
/dev/sda5              63G  5.7G   54G  10% /home
```


You'll see I have distinct partitions for / and for /home.  Root is at 85% capacity. /home is using 10%.  

BUT, Ubuntu's Disk Usage Analyzer reports that my root (/) directory is basically at 100% usage, consuming 10.8 GB or so.  My /home directory, which the Disk Usage Analyzer appears to see as a subdirectory, is using 5.5 GB of space (50%).  In bold at the top of the Disk Usage Anaylzer, it reads "Total Filesystem capacity: 69.7 GB (used 11.7 GB; available 57.9 GB)."  The warning I received seems to be based on the information seen in the Disk Usage Analyzer.

For the record, I've cleaned out aptitude and I've emptied all the trash directories I could.

I really don't want a programming glitch to decide that I've run out of disk space and effectively lock me out.

Why the difference?  Which can I trust?  And, why would I get this message?

---

### Post by viralmeme on 2010-09-02
[What's /var/lib/ureadahead/debugfs ?]("http://ubuntuforums.org/showthread.php?t=1350785")

---

### Post by kford on 2010-09-02
Thanks for the link viralmeme.

I'm still puzzled, but there was a link to a bug report that touches on this issue ([https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/499773](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/499773)) and the last poster (Comment 13) has it right: why is the priority low for an error that could result in users being told their hard drive is full and therefore unusable?

All that being said, the ureadahead line in the df -h output doesn't, on the surface, seem to be a contributing factor here.  Adding the used space on /dev/sda1 and the ureadahead together, I'd be well over 100% disk usage.  It's quite possible that, with all the crap I have installed, I am using 5.9 GB (85%) of root.

---

