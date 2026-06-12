---
title: "Gnome / gdm login slow (10+ minutes!)"
date: 2006-05-21
forum: General Help
---

### Post by AaronWyatt on 2006-05-21
After logging on through gdm, my machine is taking FOREVER to login, before showing any progress indicators. (10+ minutes!)

The last few lines of /var/log/messages read as follows: 

```
May 21 10:57:35 minklei-ubuntu gconfd (wyatt-8080): starting (version 2.12.0), pid 8080 user 'wyatt'
May 21 10:57:35 minklei-ubuntu gconfd (wyatt-8080): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
May 21 10:57:35 minklei-ubuntu gconfd (wyatt-8080): Resolved address "xml:readonly:/usr/share/gconf/local.mandatory" to a read-only configuration source at position 1
May 21 10:57:35 minklei-ubuntu gconfd (wyatt-8080): Resolved address "xml:readwrite:/home/wyatt/.gconf" to a writable configuration source at position 2
May 21 10:57:35 minklei-ubuntu gconfd (wyatt-8080): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 3
May 21 10:57:35 minklei-ubuntu gconfd (wyatt-8080): Resolved address "xml:readonly:/usr/share/gconf/local.defaults" to a read-only configuration source at position 4
May 21 10:57:35 minklei-ubuntu gconfd (wyatt-8080): Resolved address "xml:readonly:/usr/share/gconf/cdd.defaults" to a read-only configuration source at position 5
May 21 10:57:35 minklei-ubuntu gconfd (wyatt-8080): Resolved address "xml:readonly:/usr/share/gconf/debian.defaults" to a read-only configuration source at position 6
May 21 10:57:35 minklei-ubuntu gconfd (wyatt-8080): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 7
May 21 11:04:07 minklei-ubuntu gconfd (wyatt-8080): Resolved address "xml:readwrite:/home/wyatt/.gconf" to a writable configuration source at position 0
```

Note the six-and-a-half minute gap between the resolutions of /var/lib/gconf/defaults and /home/wyatt/.gconf.  So it's got something to do with gconf, right?

A google search for "resolved address xml readonly" suggests I'm getting closer.  The first four hits are posts  that describe my exact problem, including one way back from 2004, and another just a few months ago.  Unfortunately, if those people figured out a fix, they didn't follow up on the message board. =(

There are two users on this system, and they both have the same problem logging in, so the first place I look is /var/lib/gconf/defaults.  The directory is completely empty, not even any hidden files!  Strange...

My next google search is for "var lib conf defaults".  The third hit is from the [gnome.org archives]("http://mail.gnome.org/archives/gconf-list/2004-June/msg00016.html").  Here I learn that this location is for the "installed defaults/mandatory keys" they're supposed to be put there by "dh_gconf, a helper script ran at package build time."  However, for compatibility reasons, the original location /etc/gconf/gconf.xml.defaults is also supported.

Noticing that /etc/gconf/gconf.xml.defaults is also in my logfile, I peek in that directory and find the gnome configuration files in apps, desktop, schemas and system.  Just for completeness's sake, I also check ~/.gconf and find similar files.

So is the login lag due to gconfd timing out while trying to find something in /var/lib/gconf/defaults?  For lack of anything better to try, I'm going to duplicate /etc/gconf/gconf.xml.defaults in /var/lib/gconf/defaults, cross my fingers, and see what happens.

Stay tuned!

---

### Post by AaronWyatt on 2006-05-21
No luck.  Same login delay, /var/log/messages says the same thing.  I put /var/lib/gconf/defaults/ back to the way it was; empty.  Maybe there's something wrong with ~/.gconf .

---

### Post by AaronWyatt on 2006-05-21
Clearing out ~/.gconf doesn't work, either.  I'm stumped for now.  Any ideas?

---

### Post by ranf on 2006-05-23
Have a look at the file .xsession-errors in your home directory.
```
gedit ~/.xsession-errors
```

Check if the loopback network interface is up:
```
ifconfig -a | grep -A4 ^lo
```

---

### Post by boogz on 2008-05-08
Haha, i spent days trying to find out why my GDM login would take literally 5 minutes to load!, changed stuff in my /etc/network/interfaces and /etc/hosts etc etc... and in the end to find out, it was just the login theme, not sure what was wrong with it but GDM didn't like it, didn't seem to spit any errors to me though? Anyway just change it at System -> Administration -> Login Window. 

If someone encounters this, do try changing your login window theme first (if you re-added one recently) you'll save sooo much more time :) otherwise check this thread out: [http://ubuntuforums.org/showthread.php?t=585635 ]("http://ubuntuforums.org/showthread.php?t=585635") had some useful stuff which might help other people out still with this problem.

---

