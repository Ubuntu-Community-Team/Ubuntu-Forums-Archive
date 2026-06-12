---
title: "New sudo problem"
date: 2009-10-29
forum: General Help
---

### Post by teward on 2009-10-29
Doesn't prompt for sudo password anymore after modifications were made to the sudoers file (refer to this thread: [http://ubuntuforums.org/showthread.php?t=1304741](http://ubuntuforums.org/showthread.php?t=1304741)).

Anyone know why?

***EDIT:  Question: After I enter the password for sudo, it stores it until I log off, doesn't it?  That would explain the sudo -K command being useful. ***

---

### Post by Giblet5 on 2009-10-29
There's no way to guess unless you post the contents of your /etc/sudoers file.

Odds are, you have a line like
```
%admin ALL=NOPASSWD: ALL
``` in there somewhere...

---

### Post by sisco311 on 2009-10-29
> **TrekCaptainUSA said:**
> Doesn't prompt for sudo password anymore after modifications were made to the sudoers file (refer to this thread: [http://ubuntuforums.org/showthread.php?t=1304741](http://ubuntuforums.org/showthread.php?t=1304741)).

Anyone know why?

***EDIT:  Question: After I enter the password for sudo, it stores it until I log off, doesn't it?  That would explain the sudo -K command being useful. ***

The default timestamp for sudo is 15 minutes in Ubuntu.

[quote=man sudo]Once a user has been authenticated, a timestamp is updated and the user may then use sudo without a password for a short period of time (15minutes unless overridden in sudoers).
[/quote]

**sudo -K** removes the timestamp.

---

### Post by teward on 2009-10-29
> **sisco311 said:**
> The default timestamp for sudo is 15 minutes in Ubuntu.

any way to override this to make the timestamp less?

---

### Post by sisco311 on 2009-10-29
> **TrekCaptainUSA said:**
> any way to override this to make the timestamp less?

append the *Defaults* line with *timestamp_timeout=<number of minutes>*
i.e.
```
Defaults env_reset, insults, timestamp_timeout=5
```

Set it to 0 to always prompt for a password.

---

### Post by Giblet5 on 2009-10-29
> **TrekCaptainUSA said:**
> any way to override this to make the timestamp less?

From the sudoers(5) manpage:

"timestamp_timeout
    Number of minutes that can elapse before sudo will ask for a passwd again. The default is 5. Set this to 0 to always prompt for a password. If set to a value less than 0 the user's timestamp will never expire. This can be used to allow users to create or delete their own timestamps via sudo -v and sudo -k respectively."

---

### Post by teward on 2009-10-29
Thanks for all the help!

+1 respect points to you all for all your help with both of my questions today!

---

