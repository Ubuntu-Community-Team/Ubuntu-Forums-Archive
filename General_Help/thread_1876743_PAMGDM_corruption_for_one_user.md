---
title: "PAM/GDM corruption for one user"
date: 2011-11-06
forum: General Help
---

### Post by necrosymbiont on 2011-11-06
Hello All,
 
My Lucid Lynx machine froze up while I was trying to log in. My foolish attempt at a solution involved a hard reboot. I should know better. Now when I try to log in via GDM, the screen goes black, then I get returned to the GDM login screen.
 
This happens regardless of the window manager/desktop environment I use; however, it only happens for the user that was trying to log in when I did the reboot. Other users can still log in without difficulty. I can still log in via console (using Ctl-Alt-F1 or ssh).
 
I notice in my auth.log, I get the following message:
 
```

gdm-session-worker[6936]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
gdm-session-worker[6936]: pam_unix(gdm:session): session closed for user <user>

```
 
Possibly related, my .xsession-errors contains the line:
```

/home/<user>/.gnupg/gpg-agent-info-<hostname>: 1: Syntax error: ")" unexpected

```
 
I guess an authentication file used by pam has become corrupt for my user? I tried reinstalling gdm, but that didn't help. 
 
Does anyone know which file(s) might contain the problem, and what to do with them?
 
If all else fails, a workaround could involve creating a new user and giving all my data to them. Before I do that, I'd like to consider the possibility of addressing the actual problem.
 
Certainly let me know what other info you might require :-)

---

### Post by necrosymbiont on 2011-11-07
Thanks for the amazing help, Ubuntu community. :roll:

In case anyone else has this problem and is foolish enough to think these forums might help, it was quite simple. I just had a corrupt file at ~/.gnupg/gpg-agent-info-<hostname>. Deleting that file made it possible to log in again.

---

