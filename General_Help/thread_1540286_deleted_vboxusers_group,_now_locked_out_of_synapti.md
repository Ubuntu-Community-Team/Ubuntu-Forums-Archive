---
title: "deleted vboxusers group, now locked out of synaptics &amp; terminal!"
date: 2010-07-27
forum: General Help
---

### Post by greenchance on 2010-07-27
Ok, I've spent the entire day tring to install virtualbox. My dkms is newest version, my gcc is newest version, my headers seem to be in order, and it still won't install. BUT that's not my problem. (Although if it got solved, that'd be great, too.)

As I was trying repeatedly to install, I noticed it said  "group vboxusers already exists". So brilliant me, thinking that was my problem, went and deleted it, and then headed to synaptics to uninstall virtualbox (again!) so that I could try to install it (again!), only to find myself locked out.

The exact message I get is
```
Unable to get exclusive lock

This usually means that another package management application (like apt-get or aptitude) is already running. Please close that application first.
```I've worked really hard on this install, and don't want to start over with a fresh one unless it's absolutely necessary, so I'm hoping someone out there knows how to fix this.

---

### Post by merike on 2010-07-27
Deleting usergroup is not your problem. Apparently two package-management tools are running at the same time. This can cause damage and therefore the one ran last will warn you and refuse to work.

You could:
* open system-monitor and kill all apt-get or aptitude processes in there as well as close synaptic and verify it isn't still running before opening it up again
* just go for reboot which will stop all processes for you automatically

---

### Post by greenchance on 2010-07-27
It's unlocked, but now I get this message when trying to uninstall or reinstall virtualbox
```
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Setting up virtualbox-3.2 (3.2.6-63112~Ubuntu~lucid) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing virtualbox-3.2 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 virtualbox-3.2
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

```

It seems I can get back into synaptics & terminal, but there are things that are still locked up.

---

### Post by greenchance on 2010-07-27
Bump. Logged user out and back in, but still locked up.

---

