---
title: "Simple Backup (Sbackup) -- Improved and Worse?"
date: 2010-11-22
forum: General Help
---

### Post by Curbuntu on 2010-11-22
Ubuntu did some sort of upgrade last week, which seemed to partially break, yet partially improve, Sbackup.

First, what "broke"?

[LIST=1]
[*]The profile I had previously created for my sbackup routine was completely ignored.  (Everything seems to have moved to different folders.)
[*]Not knowing what my profile was, Sbackup went ahead and launched itself anyhow -- without asking.
[*]The "Schedule" tab is completely grayed out, so I can't adjust the backup frequency, nor do I know what Sbackup is assuming as the frequency default.
[*]Trying to test the e-mail notification freezes Sbackup, requiring a kill.
[*]This morning, Sbackup *seems *to be successfully creating a *.ful backup from this system (after several failed attempts yesterday, all marked as *.corrupt on the remote server's drive).  BUT about two hours after the backup started, a message-notification balloon popped up to announce the following:
[/LIST]
[CENTER]**"SIMPLE BACKUP SUITE**
Attempt of starting another instance of 
Simple Backup while this one is already running" [sic]
[/CENTER]

I didn't launch this attempt, nor is there a profile other than the modified "default" profile.  So why would SBackup try to launch itself *again *know that it is already running?

What seems to be improved?

[LIST=1]
[*]Sbackup now uses the notification area *and *it displays an icon in the top panel.  That's a nice touch.
[*]Setting up a backup to a remote ssh server now no longer requires equal parts hair-tearing and voodoo sacrifices to be set up properly.  (Previously, it would repeatedly refuse SSH connections, even though the SSH username, password, and target were carefully verified, and this even though a "manual" CLI SSH connection could be performed easily.)  Now it works the first time.
[*]The new e-mail notification is a nice touch (or it would be if it didn't freeze the application -- see above).
[/LIST]

FWIW, I've encountered the above problems in both 10.04.1 32- and 64-bit.

---

