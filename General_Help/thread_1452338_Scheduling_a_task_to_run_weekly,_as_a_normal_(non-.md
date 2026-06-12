---
title: "Scheduling a task to run weekly, as a normal (non-root) user"
date: 2010-04-11
forum: General Help
---

### Post by runesvend on 2010-04-11
Hi

I'm trying to get my backup script to run every week, but as a normal user, and not as root as it is done when the script is placed in */etc/cron.weekly*.
Anacron fits my needs in the sense that it doesn't require my computer to always be on, as opposed to cron, and will just run my script when it can, but at the most each week.
Cron fits my needs in the sense that I can run the script as the user I am logged in as. The particular script backs up my home directory with rdiff-backup, and it is very convenient that I am the owner of that backup, since when root performs the backup, I am unable to browse my own backup files and must use "sudo" to do this.

Is there a way to let me use the feature of anacron that allows my computer to not always be on, but still get a weekly execution, and also run the script as a normal (non-root) user?

Thank you!

---

### Post by runesvend on 2010-04-11
A refined Google search yielded the following solution:
[http://ubuntuforums.org/showthread.php?t=353824](http://ubuntuforums.org/showthread.php?t=353824) (last post)

I have set it up, and will report back the results in a couple of weeks, to see if it does as intended.

---

### Post by runesvend on 2010-06-24
It works like a charm!

---

