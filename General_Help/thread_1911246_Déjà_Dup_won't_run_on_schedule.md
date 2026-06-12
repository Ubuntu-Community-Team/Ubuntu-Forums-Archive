---
title: "Déjà Dup won't run on schedule"
date: 2012-01-18
forum: General Help
---

### Post by Fraoch on 2012-01-18
Hello:

I'm using Déjà Dup to backup.

The GUI is very simple and kind of hard to screw up but perhaps I have.  I have automatic backups scheduled (weekly) but the program does not run automatically on schedule.  I always have to trigger a manual backup.

Déjà Dup Monitor is active in my Startup Applications - I believe it was put there when I installed Déjà Dup and I haven't altered it, besides confirming it is checked and should run.

[I posed this question to the developers of Déjà Dup]("https://answers.launchpad.net/deja-dup/+question/179913") and didn't get much of a response:

[quote=Javier Domingo]In theory, each time it is scheduled to work, if you have made it to remember the password of the backup place, etc, it wil start making the backup[/quote]

So it should work...but doesn't.  The backup location does not require a password and "others" have permission to create and delete files, so if Déjà Dup runs as a user other than me, it should be able to write to the drive.

Is there anything else I should check?

Thank you.

---

### Post by bluexrider on 2012-01-18
in your "startup applications" make sure "deja dup" is checked. that starts the scheduled daemon.

---

### Post by Fraoch on 2012-01-18
Thanks for the response!

> **bluexrider said:**
> in your "startup applications" make sure "deja dup" is checked. that starts the scheduled daemon.

Hmm, I put "Déjà Dup" in my Startup Applications and pointed it to /usr/bin/deja-dup and unclicked the "Déjà Dup Monitor" that Déjà Dup added when it was installed.

I then restarted.  I don't think anything happened, there's been no disk activity and "Déjà Dup Backup Preferences" shows the next backup as Today.  Also "ps aux" shows no Déjà Dup process or daemon actually running.

It runs backups at 2:00 AM or something, so here's to hoping that it does this tonight (if it wants to back up "Today") but I'm not sure the daemon is actually running.

Is there a better command than "ps aux" to determine this?

Thanks.

---

### Post by bluexrider on 2012-01-18
You could use 'top'

---

