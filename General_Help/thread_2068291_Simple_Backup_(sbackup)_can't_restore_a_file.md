---
title: "Simple Backup (sbackup) can't restore a file"
date: 2012-10-08
forum: General Help
---

### Post by sberla54 on 2012-10-08
Hello everybody,
i've got this strange problem with Simple Backup 0.11.4 (sbackup) and is making me worrying a little bit.

I'm trying to restore a file from a 3 months old full backup but i can't: i can find the file in the backup image of that month, i can choose "Restore as", the process begins and it ends with a success message.
Anyway, it doesn't restore nothing.

In the files listing of the backup image i see that the file is in status "Unchanged". Is it this the cause of the fail? What does that mean? That it is unchanged from an old backup so it isn't included in this one, even if is a full backup?
I've manually deleted a lot of old full backups...

I can see there are a lot of files in status "Unchanged", even my Thunderbird folder, that obviously changes almost everyday...

I'm afraid i can't trust Simple Backup anymore, but it always worked well before, the 2 times i needed it.

Thank you

---

### Post by sberla54 on 2012-10-16
Nobody has any advices about that?

Maybe even a better backup program...
I was considering Crash Plan: [http://lifehacker.com/5787572/set-up-an-automated-bulletproof-file-back-up-solution](http://lifehacker.com/5787572/set-up-an-automated-bulletproof-file-back-up-solution)

---

### Post by sberla54 on 2012-10-17
Update: i think i've understood the problem.

The file i was trying to restore was a .ogg file and in the default profile configuration, Simple Backup doesn't backup mp3, ogg, mkv, avi etc.

This is the reason because it was on state "unchanged".

Everything else is on state "included".

So, i've changed the profile configuration.
And i gave up restoring that file, that hasn't been backupped.

Thank you anyway.
If you still have some advice regarding backup software, i will appreciate them.

---

