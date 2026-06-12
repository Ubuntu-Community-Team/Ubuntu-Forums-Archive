---
title: "df reports 89% usage du says different"
date: 2009-10-18
forum: General Help
---

### Post by bobwdn on 2009-10-18
I have been using a 8.04LTS server for my /home storage via nfs. It has an older P2-350 motherboard and a hardware RAID card (MegaRAID i4) with two 200Gb HD's striped for almost 400 Gb's of storage space. A "df" command report that there is 89% usage.
```
blob@4stripe:/$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            384040176 323779912  40752136  89% /
varrun                  127772        68    127704   1% /var/run
varlock                 127772         0    127772   0% /var/lock
udev                    127772        32    127740   1% /dev
devshm                  127772         0    127772   0% /dev/shm
```
A "du" command reports just under 167Gb used.
```
blob@4stripe:/$ du -cm /*
166212	total

```
This should leave me with just about 50% space available. But it does not. Just recently I had to clear some space to drop my "df" from 98% used to get to 89%. Which command is correct? Have I really out grown my server space? What am I not understanding?:confused:

---

### Post by falconindy on 2009-10-18
df and du measure different quantities. Take a look at this:

[http://linuxshellaccount.blogspot.com/2008/12/why-du-and-df-display-different-values.html](http://linuxshellaccount.blogspot.com/2008/12/why-du-and-df-display-different-values.html)

---

