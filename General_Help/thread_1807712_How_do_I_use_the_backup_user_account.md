---
title: "How do I use the backup user account?"
date: 2011-07-19
forum: General Help
---

### Post by mickey13 on 2011-07-19
So I was creating a backup user on my Ubuntu machine, and realized that there was already one there.  I wanted to have a user account that only had permission to scp data archives to my backup directory.  Is there already a mechanism in place via this backup user to do just that?  Or does this account have other uses and should be left alone?

---

### Post by btindie on 2011-07-19
The backup user account under Ubuntu is a system account and it doesn't have a password.

It's home directory is in /var/backups which is where /etc/cron.daily/standard, triggered via cron, places it's backups though that is run as root.

It's probably better to create your own account and not touch the system ones as they may be reconfigured when new software is installed.

---

