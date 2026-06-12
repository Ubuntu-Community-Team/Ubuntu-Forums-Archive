---
title: "Password for authentication not same as sudo?"
date: 2011-09-24
forum: General Help
---

### Post by mebison on 2011-09-24
Hi everyone, I'm having a password issue.

I just installed Ubuntu 11.04 using Wubi.  I'm trying to update drivers to get my wireless (and graphics) working at full steam.  However, when I try to install the drivers (system->administration->additional drivers) it won't take my authentication password.  However, my password works just fine if I use it in sudo commands?

These should be the same password, right?  Any ideas how to straighten this out?

---

### Post by papibe on 2011-09-24
Welcome to the forums!

It looks like a case of mis configured gksudo (the graphical sudo). Go into a terminal and run:
```
gksu-properties
```
It'll open a window. Under Behavior there's a field called 'Authentication mode'. If it says su, change it to sudo.

I hope it helps,
Regards.

---

### Post by mebison on 2011-09-24
> **papibe said:**
> Welcome to the forums!

It looks like a case of mis configured gksudo (the graphical sudo). Go into a terminal and run:
```
gksu-properties
```It'll open a window. Under Behavior there's a field called 'Authentication mode'. If it says su, change it to sudo.

I hope it helps,
Regards.


Thanks for the welcome!

I just checked the gksu and it was set to sudo already.  I've also noticed strange behavior in the login that makes me think there's an issue with the case sensitivity of my username.  When I get to the login screen, it prompts me to log in under "Mebison".  Most of the time, that doesn't end up working, and I have go to "log in as a different user" and log in as "mebison" and then I get in.  Perhaps there's something similar where the authentication program is seeing me as "Mebison" while the sudo commands see me as "mebison"?  I don't know if that makes any sense, or not??

---

### Post by papibe on 2011-09-24
I'm not complete sure, but it seems that it could be applications that may have problems with a case sensitive user (read [here]("http://askubuntu.com/questions/46739/case-sensitivity-of-account-usernames")).

If you are willing to try changing your user to all lowercase, try [this]("http://ubuntuforums.org/showpost.php?p=7958725&postcount=11") instructions.

After that restart your machine and tell us how it goes,
Regards.

---

