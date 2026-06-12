---
title: "How to Sync Two Computers via External Drive?"
date: 2011-07-29
forum: General Help
---

### Post by Kissell on 2011-07-29
So, I have a large amount of data on a Ubuntu server, and I needed a cheap way to back up that data, so I configured RAID on another computer and copied the files to it.  Great...  data is backed up...  then I would periodically update it.

Later I decided to move the new computer to another location to be the local server there.  I still want to use it for backups, now as an offsite backup, but there is not a fast enough internet connection to copy changes online from the main site.  They are connected via a VPN, so they can see each others files, but they just can't use that link to copy changes, the files are often too big.  And since the new one is always a backup copy, changes only need to go one way.  

Is there a program you can recommend which will run on Ubuntu, look at both paths, decide what has added/changed/deleted, and then store that information along with the new files onto a USB drive, then allow me move that USB drive to the other site and run that program on the other computer to import those changes?

Currently I am using "cp" with the mtime and noclobber switches, it copies everything new and modified within X number of days to a USB drive (X being the days since I last ran a backup), then imports those new files without overwrite to the other server.  The problem is that it isn't propagating deletes, and if I increase X to make sure I don't miss anything, it takes a lot longer to do the incremental backup (which I am waiting on).  And I have to manually run some CLI commands and think about what value to change X to...  it would be nice to just have a program which would do it on a schedule without me having to think, like backup the changes to a USB drive every night, then anytime I take it to the remote site, import those changes.  I was about to crontab this, but decided that without propogating deletes, this wasn't a good enough solution.

---

