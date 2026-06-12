---
title: "smplayer Upgrade Error"
date: 2011-06-14
forum: General Help
---

### Post by Chaconne on 2011-06-14
Hi, all,

I got the following error today when I was upgrading the software of my system.

```

The following packages have unmet dependencies:
 smplayer-themes : Depends: smplayer but it is not going to be installed
 smplayer-translations : Depends: smplayer (>= 0.6.9-1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

After I ran 'apt-get -f install', the following error occurred and there was no other more useful hints.

```

dpkg: error: parsing file '/var/lib/dpkg/status' near line 22351 package 'smplayer':
 missing version
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: error: parsing file '/var/lib/dpkg/status' near line 22351 package 'smplayer':
 missing version

```

The problem now is smplayer seems not installed in Synaptic, but I can still run it from the menu. The much worse thing is this error blocks all my other software upgrade no matter which command I use, but it apt-get, aptitude or synaptic. I can neither remove the 2 problematic packages smplayer-themes and smplayer-translations. 

Please shed some light on this problem if possible. I can switch to another media player, but being not able to upgrade all other software is too much.

---

### Post by Chaconne on 2011-06-14
Both 'sudo dpkg --configure -a' and 'sudo dpkg -C' yield the same outcome

```

dpkg: error: parsing file '/var/lib/dpkg/status' near line 22351 package 'smplayer':
 missing version

```

---

### Post by Chaconne on 2011-06-14
For your information. I solved the issue according to the instructions in [this post]("http://ubuntuforums.org/showthread.php?t=1642574") by restoring an old /var/lib/dpkg/status

---

