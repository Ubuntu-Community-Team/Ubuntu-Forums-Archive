---
title: "Cant log to my session when booting"
date: 2011-05-17
forum: General Help
---

### Post by Amokrane on 2011-05-17
Hi,
 
I have an issue here with my computer using ubuntu 10.10 on a 64 bits machine. When I start it, I have the login screen, I enter my credentials but instead of starting the session it reloads the login screen again.
I checked the disc using fsck and it seems clean. How should I proceed to diagnose and repair this issue?
 
Thanks!
 
_[Edit]_
I went to the log files, this is what I got:
 
*_auth.log_*
> 
pam_unix (gdm:session): session opened for user amokrane by (uid=0)
 
pam_ck_connector (gdm:session): nox11 mode, ignoring PAM_TTY :0 pam_unix
 
(gdm:session) :session closed for user amokrane

 
*_messages.log_*
> 
No ACPI video bus found

 
I also took a shot with my camera of the black screen that appears between the two login screens, it says something like:
> 
fsck from util-linux-ng 2.17.2

/dev/sdc4 : propre, xxxx files, xxxx blocs

Starting AppArmor profiles

Skipping profiles in /etc/apparmor.d/disable: usr.bin.firefox

Setting sensors limits

Starting postgreSQL ...


---

