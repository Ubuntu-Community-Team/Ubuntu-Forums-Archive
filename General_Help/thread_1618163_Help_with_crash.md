---
title: "Help with crash"
date: 2010-11-10
forum: General Help
---

### Post by supradave on 2010-11-10
My lucid server is crashing nearly daily and three times yesterday (with more drive activity).  Unfortunately there are no console messages and nothing in messages or syslog.  What I believe is the problem is that the hard drive is failing though data integrity appears fine.  What I think the problem is is that the drives buffer is getting data and then when it tries to write it out is when it dies, i.e. the platters or heads freeze.  Before I spend a few bucks on a drive, does that make sense or should I look elsewhere?

The drive is an Hitachi Deskstar that's 5 years or so old.

The drive is vertical and reading a review on newegg said that that could cause a problem.  Looks like a new drive is in the works.

---

### Post by Ashrael on 2010-11-10
HI!

Hitachi deskstar also known as Hitachi Deathstar....
Try to read the S.M.A.R.T. data from the drive....

[http://www.howtoforge.com/checking-hard-disk-sanity-with-smartmontools-debian-ubuntu](http://www.howtoforge.com/checking-hard-disk-sanity-with-smartmontools-debian-ubuntu)

From the moment that I lost ALL my data from the Deathstars, I swapped brands to SAMSUNG, and NEVER lost anything again.... SAMSUNG FOREVER! Or at least until they develop a really bad harddrive first... :)

HTH!

---

### Post by dino99 on 2010-11-10
its strange there is no error logged to help you .

try first to clean the system as much as you can:
- check hdd free space
- run clean/autoclean/autoremove or better install bleachbit to make room

- run a fsck on next reboot
sudo shutdown now -R

- check that you only use genuine ubuntu repo (no exotic or untrusted ppa) then:

update, install -f

at last check that blkid and fstab have the same uuids

---

