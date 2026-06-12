---
title: "Changing UID breaks GUI functions - suggestions?"
date: 2011-11-16
forum: General Help
---

### Post by Jalaska13 on 2011-11-16
I'm dual-booting on a MBP, and I've changed my uid to 501 to be cross-compatible with my Mac OS and filesystem (so I can access my user's files on the mac partition).

Problem is, a few things are broken.

When I restarted, the login menu no longer listed my username (no surprise there).  When I logged in, though, my Name (full user's name) at the top right bar was replaced by:
[Invalid UTF-8]

Also, when I go to the user accounts pane for system settings, all of my account fields are blank (ie, it doesn't seem to recognize that my user account is there).

Are there any configs that I can edit so that the system now looks for user 501 and not user 1000?  Maybe something else I can do to fix this (other than changing my uid back)?

Thanks!

---

### Post by Slim Odds on 2011-11-16
> **Jalaska13 said:**
> I'm dual-booting on a MBP, and I've changed my uid to 501 to be cross-compatible with my Mac OS and filesystem (so I can access my user's files on the mac partition).

Problem is, a few things are broken.

When I restarted, the login menu no longer listed my username (no surprise there).  When I logged in, though, my Name (full user's name) at the top right bar was replaced by:
[Invalid UTF-8]

Also, when I go to the user accounts pane for system settings, all of my account fields are blank (ie, it doesn't seem to recognize that my user account is there).

Are there any configs that I can edit so that the system now looks for user 501 and not user 1000?  Maybe something else I can do to fix this (other than changing my uid back)?

Thanks!

How did you "change" your UID?

If you just changed it in the group and passwd files, all "your" files are still owned by the old UID.

---

### Post by Jalaska13 on 2011-11-16
> **Slim Odds said:**
> How did you "change" your UID?

If you just changed it in the group and passwd files, all "your" files are still owned by the old UID.

I used (from a root shell, so I wasn't logged in):
usermod -u 501 myusername

It still doesn't mind me being logged in - I have permissions to edit files and whatnot.  You'd think if that were the issue I'd have bigger problems like not having r-w access to any of my files

---

### Post by JKyleOKC on 2011-11-16
Take a look at /etc/adduser.conf and also at /etc/passwd

The adduser.conf file has settings for last system ID and first user ID; perhaps if you change these and reboot, things will work right for you again.

However be sure to back things up, because this might not be the only place that boundary is defined, and your reboot might leave you needing to reinstall the whole thing from scratch! Be warned...

---

### Post by Jalaska13 on 2011-11-16
> **JKyleOKC said:**
> Take a look at /etc/adduser.conf and also at /etc/passwd

The adduser.conf file has settings for last system ID and first user ID; perhaps if you change these and reboot, things will work right for you again.


Unfortunately, this didn't work.  I'll keep the config because it seems like a good idea given my new uid and gid, but it didn't help anything.  Thanks for the advice, though.

---

### Post by dcstar on 2011-11-17
> **Jalaska13 said:**
> I'm dual-booting on a MBP, and I've changed my uid to 501 to be cross-compatible with my Mac OS and filesystem (so I can access my user's files on the mac partition).

Problem is, a few things are broken.
.........
Are there any configs that I can edit so that the system now looks for user 501 and not user 1000?  Maybe something else I can do to fix this (other than changing my uid back)?

Thanks!

Changing anything on the main user account is insane. The whole Ubuntu system is built on the primary admin account being UID 1000 and any changes will terminally break your Ubuntu system.

Use a Live CD to manually edit the /etc/passwd file and fix that account.

If you want to stuff around with non-standard UIDs then create another account and change that.

---

