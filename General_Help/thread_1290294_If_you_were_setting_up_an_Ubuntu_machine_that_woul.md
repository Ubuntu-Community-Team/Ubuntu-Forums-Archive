---
title: "If you were setting up an Ubuntu machine that wouldn't be updated for a long time...."
date: 2009-10-13
forum: General Help
---

### Post by Roasted on 2009-10-13
How would you set up the updates?

I currently have a Samba file server set up in my parents house which does backups of everybody's "My Documents" at early hours of the morning, however I plan to get out of there in the next year or so. Whenever I leave, my computer comes with me, but I'll leave behind an older Pentium 4 PC that should do the job of running a Samba file server just fine. 

Since the Samba file server wouldn't be on a computer that gets touched for long periods of time, how would I set up the updates? Should I just bank on auto download + auto install and roll with it? Or should I turn updates off? Or what?

---

### Post by P4man on 2009-10-13
If it aint broken, dont fix it. I would certainly NOT set auto updates, I would turn them off. Whenever you're around, you could check if there are updates you want to install, but frankly, for a file server, if it works, why bother upgrading?

---

### Post by Xbehave on 2009-10-13
Once a ubuntu version is released you generally only get get security updates (especially once everything has settled down), these updates are pretty key for any box that faces the internet and generally do not break anything.

It sounds like your ok as you are not accessible from the internet so there is no need to auto-update.

---

### Post by slakkie on 2009-10-13
No auto-updates.

Just make sure it is up to date when you leave and don't touch it again. 

I would use an LTS version of Ubuntu if I was you, so you don't have to worry about EOL upgrades when you get back.

---

### Post by ptn107 on 2009-10-13
I agree with the above if it were a mission-critical server.  Servers (file/media/web) I keep for home use I generally do set up for automatic updates.  I've had 18 months so far of auto-updating an Ubuntu 8.04 LTS machine with absolutely no problems.  Updates that are released for stable versions of Ubuntu are just bug and security fixes anyway and will not introduce more bugs or regressions.

If your server has a graphical (GNOME) desktop just set up System -> Administration -> Software Properties to accept 'Important security updates', 'Recommended updates', 'Check for updates daily', and 'Install security updates without confirmation'.

You can also edit /etc/apt/apt.conf.d/50unattended-upgrades and change:
```
// Automatically upgrade packages from these (origin, archive) pairs
Unattended-Upgrade::Allowed-Origins {
	"Ubuntu hardy-security";
//	"Ubuntu hardy-updates";
};
```
to
```
// Automatically upgrade packages from these (origin, archive) pairs
Unattended-Upgrade::Allowed-Origins {
	"Ubuntu hardy-security";
	"Ubuntu hardy-updates";
};
```
that will allow bug fixes to be automatically installed in addition to the security fixes resulting in a completely self-updating system.  The above statements are valid too though.  On a freshly installed system just update it once and forget about it.  It will work just fine.

---

