---
title: "Firefox freezes on startup?"
date: 2010-09-07
forum: General Help
---

### Post by Dalstal on 2010-09-07
Hello!
Kind of an inexperienced user so keep the lingo simple.
I just installed a program from my bank to enable accessing my internetbank with SSL-certificates (i think?) The installation went smoothly with a tarball but now i'm unable to start firefox? I get the "starting firefox" -message but then nothing happens and when I check the system monitor the startup process seems to be sleeping.
Any ideas? I've already tried rebooting with no results whatsoever. 
I'm running ubuntu 10.04

---

### Post by viralmeme on 2010-09-07
> **Dalstal said:**
> I just installed a program from my bank to enable accessing my internetbank with SSL-certificates (i think?) The installation went smoothly with a tarball but now i'm unable to start firefox?
What's the name of this program? Try starting firefox in safemode. Or maybe it's a corrupt FF profile, i so delete the profile and start again ..

$firefox -safe-mode

---

### Post by Dalstal on 2010-09-07
It's "Nexus personal", a Bank-ID program. firefox -safe-mode gives me absolutely no reaction. How do you delete a firefox profile? Just apt-get remove firefox?

---

### Post by viralmeme on 2010-09-09
> **Dalstal said:**
> It's "Nexus personal", a Bank-ID program. firefox -safe-mode gives me absolutely no reaction. How do you delete a firefox profile? Just apt-get remove firefox?

The profile is in your home directory under .mozilla, fire up the Terminal and delete it. 'rm -r /home/user/.mozilla/*'. You will lose all your FF settings.

[http://forums.fedoraforum.org/showthread.php?t=221984](http://forums.fedoraforum.org/showthread.php?t=221984)

---

### Post by philinux on 2010-09-09
> **viralmeme said:**
> The profile is in your home directory under .mozilla, fire up the Terminal and delete it. 'rm -r /home/user/.mozilla/*'. You will lose all your FF settings.

[http://forums.fedoraforum.org/showthread.php?t=221984](http://forums.fedoraforum.org/showthread.php?t=221984)

He could backup his bookmarks first from

/home/username/.mozilla/firefox/xxxxxxxx.default/bookmarkbackups

---

