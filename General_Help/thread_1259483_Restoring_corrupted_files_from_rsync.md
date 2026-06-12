---
title: "Restoring corrupted files from rsync"
date: 2009-09-06
forum: General Help
---

### Post by darth_indy on 2009-09-06
I've been using rsync ("rsync -ar --progress --delete /home/darthindy /media/disk/Backups" in case it matters) to back up my laptop on a mostly-regular basis (Though, I must admit, I've missed the last couple weeks), and recently I had an issue that corrupted my /home partition. While a fsck was able to put the home partition back into full working order, I know a lot of files were corrupted and are missing bits and pieces. One in particular was an .iso, for example, where the md5sum did not match what I was given. The backup copy had the correct md5sum.

My question is, what would be the best way to use rsync (or some other program, if it works better) to restore corrupted files, without deleting/messing with files that I've added to my computer since last backup, or overwriting files that I've manually edited?

I know the last part would be the hardest, and perhaps impossible, since I don't think rsync would be able to tell whether the changes in a file were made on purpose or whether it's because blocks were erased during a fsck. If that's not possible, that's OK - there are only a couple of folders where I'm worried about losing new work. But if that's the case, how do I exclude folders from being restored? For example, if I have homework stored in /home/darthindy/Schoowork - could I specify to rsync to restore all but the "Schoolwork" folder?

Any help is appreciated in advance.

---

### Post by winotree on 2009-09-06
I'm by no means an expert on this (just began using *rsync* this summer) but **--exclude=nameoffile **works for me when backing-up or restoring my /home/user file.  Here's a link to probably more info than you need at one time: [http://www.manpagez.com/man/1/rsync/](http://www.manpagez.com/man/1/rsync/) which I hope helps you...  ;)

---

