---
title: "update-rc.d scripts"
date: 2006-06-14
forum: General Help
---

### Post by ubuntuthinking on 2006-06-14
Hello all,
Doing a bit o' research on boot scripts I found several ways to get various things accomplished via update-rc.d, rcconf and BUM (my personal favorite)

One Question:
Is there a way to use Nautilus or ls to see the list of scripts managed by rc.d?

Likely a simple issue but you all know the forrest and trees story... thanks,:rolleyes

---

### Post by joshrobinson on 2006-06-14
[QUOTE=ubuntuthinking]Hello all,
Doing a bit o' research on boot scripts I found several ways to get various things accomplished via update-rc.d, rcconf and BUM (my personal favorite)

One Question:
Is there a way to use Nautilus or ls to see the list of scripts managed by rc.d?

Likely a simple issue but you all know the forrest and trees story... thanks,:rolleyes[/QUOTE]

/etc/init.d

---

### Post by ubuntuthinking on 2006-06-15
hmm, thanks!

yet I'm comfused, for example tinyproxy is listed in /etc/init.d but i have removed it from the System>Preferences>Start Up Programs.

So my assumption is that rc.d uses init.d as a "pool" of resources but only has selected applications commence at startup.

Consequently I looked into rc2.d etc. and found tinyproxy listed in several run levels but it does not start - I don't want it to I would just like to know where is the list of selected start up applications.  thanks

---

### Post by gwpritch on 2006-06-15
/etc/init.d does in fact contain all the scripts for startup services. 
/etc/rc2.d simply contains symlinks to the scripts which are set to start in runlevel  2 . rc3.d runlevel 3 etc.
Any Symlink beginning with an uppercase S will be started in numerical order. Replacing the S with a K essentially kills the service on startup. Removing the link also prevents startup as long as the service is not started under rcS.d.

---

