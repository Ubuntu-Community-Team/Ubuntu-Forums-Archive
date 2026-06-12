---
title: "Any good GUI-based backup software?"
date: 2010-08-30
forum: General Help
---

### Post by ownaginatious on 2010-08-30
So my dad had me build this file server at his studio.

His old server was a Mac running OS X with some backup software called 'Retrospect'.

He has two backup drives - two identical 2-terabyte external drives. Each week he brings in one, plugs it into the server and at a scheduled time it would start the backup. The following week he'd bring in the other drive and backup to that - swapping each week. If the drive was missing at the time of backup, Restrospect would display a message saying it needs the drive to do the backup.

Personally I don't really like the fact that he's relying on himself or someone else to plug in the drives and do the backups, but he's paranoid that a disaster could occur in which the computer gets destroyed (maybe a comet hitting his studio... lol).

Anyway, what I'm wondering is - is there some sort of backup software out there for Linux with a GUI that can just show current backup progress (if one is occurring) and allow you to configure how the backups can occur?

I can make the window pop-up automatically using cron I guess, after which it can be closed by someone in the studio.

I'm guessing maybe a front end for rsync would be good, but I haven't seen any that do anything besides letting you configure rsync.

Any help would be greatly appreciated.

Thanks!

P.S. I guess I could check if the drive is there by doing a grep on blkid for whatever the backup drive's UUID is to check if it's there. Good idea? lol

---

### Post by inameiname on 2010-08-30
The frontend for rsync is grsync, and works just fine for me. Although, personally, I use Remastersys for my backing up needs. 

sudo apt-get install grsync

Also, here is a recent poll on the best Linux backup software. Maybe you'll find it useful.:

[http://www.webupd8.org/2010/05/best-linux-backup-tool-software.html](http://www.webupd8.org/2010/05/best-linux-backup-tool-software.html)

---

