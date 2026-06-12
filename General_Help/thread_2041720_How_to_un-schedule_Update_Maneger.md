---
title: "How to un-schedule Update Maneger?"
date: 2012-08-13
forum: General Help
---

### Post by trade4target on 2012-08-13
I have Ubuntu 10.04 LTS (Lucid Lynx) installed on my desktop.

Very often just after the startup, the Update Manager is launched automatically and it is annoyed because I want it to appear only when I launch it manually.

Could anybody advise me what should I do to remove the Update Manager from the launching schedule?

P.S. I have looked into man pages on cron, crontab, anacron and anacrontab but have not found any specific line in system-wide crontab or anacrontab files that should be removed.
       Moreover, the system reports that crontab files does not exist for root and the user.

Thank you.
trade4target

---

### Post by Tobeus on 2012-08-13
If you open Update Manager look in the lower corner for Settings.

Click this button and choose the Updates tab.  You can then customize your settings at the lower part of this screen, and can even turn "Automatically check for updates" to Never, just make sure you run it every once in a while so you are not vulnerable to security vulnerabilities.

On high-use systems, I like to check updates daily, automatically install security updates, and other updates to display every two weeks.  I'm not sure how to disable the update manager from popping up if there are currently updates in the queue though, other than installing the updates and disabling for future use.

Good luck!

-Tobeus

---

### Post by 2F4U on 2012-08-13
Did you look into the automatically started applications for the desktop (if I remember right it is called Startup Applications)?

---

### Post by asmoore82 on 2012-08-13
You can open "System -> Preferences -> Startup Applications" and uncheck Update Notifier completely.

But it sounds like you might prefer this instead: This is how to restore the old behavior where you see updates are available in the notification area but the update window doesn't jump up in your face:

```
gconf-editor
```

and in the left pane, browse down to /apps/update-notifier.
Then in the right pane, uncheck auto_launch (should be the 1st one).

---

