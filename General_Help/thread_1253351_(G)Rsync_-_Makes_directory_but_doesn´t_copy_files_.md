---
title: "(G)Rsync - Makes directory but doesn´t copy files AARGH!!!"
date: 2009-08-30
forum: General Help
---

### Post by Megamanic on 2009-08-30
Ok, this is what I´m trying to do.

I have a USB Hard Drive Formatted NTFS with about 170GB of data on it which I want to move onto my shiny new WD World Book II Raid 1 NAS.

I used ¨dmizer¨´s excellent HowTo and I have successfully mounted the NAS.  The HDD automounts fine.

So, I´e been copying stuff for days at around 3MB/s which is around 25% of the max throughput of my 100Mbit router but I´ll live with that for now - I have bigger issues.

RSyncing a partially copied directory it only seems to have created directories not files.  For example...

Using GRSync (because I´m a newbie & thought it would be easier) I set it up to copy from:

/media/disk/music/ (The directory on the USB drive containing my MP3s)

to:

media/MyWorldBook2/Media/Music/

Basic options:

Preserve Time, Preserve Permissions, Preserve Owner, ignore existing, verbose, show progress.

Advanced options:

contains a residual ¨--exclude=.gvfs¨ left over from my /home -> backup run (which also appears to have done the same thing copying only the directories not the contents)


HELP!!!!  What am I doing wrong?

Ok, I finally had a chance to debug this.

Basically the problem is Preserve Time & Preserve Permissions.  It looks like I don't have rights to do that on the NAS - I can create, delete edit & move files but I can't change the time or permissions - go figure.  Removing these options & it runs like a dream.

Anyway, I was naively hoping that I could make an exact replica of /home/Megamanic/ but it looks like I'm just going to have to settle for copying all the files ;)

I'd suggest that anyone copying what I'm doing doesn't just "--exclude=" instead use --exclude-from and a filename which you can then add lines of stuff you don't want to mirror like .gvfs & .thumbnails etc.

---

### Post by Megamanic on 2009-08-30
Bump - also just confirming I haven´t been a total clot & put ¨--existing¨

Does anyone have any ideas?

---

### Post by PGScooter on 2009-08-30
hmmmm I would suggest trying to do it with the command line. You might get better feedback/warnings/errors. Remember, you can put two v's such as "rsync -avv folder1 folder2" to get more verbose.

I would also get rid of the preserve stuff. I do not think that NTFS stores the owner and permissions and such. That might be the problem.

---

### Post by Megamanic on 2009-08-30
> **PGScooter said:**
> hmmmm I would suggest trying to do it with the command line. You might get better feedback/warnings/errors. Remember, you can put two v's such as "rsync -avv folder1 folder2" to get more verbose.

I would also get rid of the preserve stuff. I do not think that NTFS stores the owner and permissions and such. That might be the problem.

Thanks - I was trying to use GRSync to ¨build¨ the command line visually - as I said I´m a newbie :) then I was going to CRON the job from /home to /backup & have the best home backup system I´ve ever had.

---

### Post by PGScooter on 2009-08-30
> **Megamanic said:**
> Thanks - I was trying to use GRSync to ¨build¨ the command line visually - as I said I´m a newbie :) then I was going to CRON the job from /home to /backup & have the best home backup system I´ve ever had.

definitely understandable :). Sorry I can't help more.

---

