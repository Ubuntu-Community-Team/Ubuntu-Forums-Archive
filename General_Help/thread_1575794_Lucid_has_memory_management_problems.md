---
title: "Lucid has memory management problems"
date: 2010-09-16
forum: General Help
---

### Post by kainalu on 2010-09-16
Hello all,

I am experiencing very high memory usage since upgrading, and it has gotten worse over the months since release. I noticed with all users logged out, I can go to terminal 1 and htop puts memory usage at 600MB for an idling, non logged in desktop. This wasn't the case on karmic, and my usage has not really changed. Upon logging in, it goes up to 800MB-1GB, on the desktop and idling.

This has also been referenced at these places:

[http://ubuntuforums.org/showthread.php?t=1430763](http://ubuntuforums.org/showthread.php?t=1430763)
[http://ubuntuforums.org/showthread.php?t=1453067](http://ubuntuforums.org/showthread.php?t=1453067)
[http://ubuntuforums.org/showthread.php?t=1516666](http://ubuntuforums.org/showthread.php?t=1516666)
[http://ubuntuforums.org/showthread.php?t=1454780](http://ubuntuforums.org/showthread.php?t=1454780)

Also, nautilus takes at minimum ~200MB and upwards of ~600MB sometimes, and Ive purged thumbnails already. That is utterly ridiculous for a window manager.

Any ideas on why Lucid has gotten so bloated, and how to trim it up? Will Maverick address these issues?

---

### Post by ngrieb on 2010-09-16
Did you at one point have compiz effects on? Try killing nautilus in the terminal via: killall nautilus, and then restart it via: nautilus --replace &. You might be running two instances of a window decorator. If the --replace flag says there is nothing to replace, then just reinstate nautilus by just calling it and putting it in the background: nautilus &. Also to make sure you are not loading two instances on boot, after killing and replacing nautilus if it then seems to work better, go to the startup programs option and save the currently running background apps. Hope this helps.

---

### Post by snowpine on 2010-09-16
Hi Kainalu, nowhere in your post do you mention any performance problems or degradation, so I will assume your system is running fine.

You may find this link informative:

[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

### Post by kainalu on 2010-09-16
ngrieb: Compiz was disabled a while back on my system to check for this.

snowpine: most of the time my system runs fine, but [insert deity here] help me if I try to use something memory intensive. The memory is actually being used, not used as cache, but HTOP fails to tell me where. gnome-system-monitor, HTOP, and free all report the memory as in-use not as cache. I used to be able to run 3 virtual boxes with 512 allocated each, for testing, but now, that would be a joke to attempt.

```
free
             total       used       free     shared    buffers     cached
Mem:       1986904    1920896      66008          0     118744     746512
-/+ buffers/cache:    1055640     931264
Swap:      1052248       3080    1049168

```

Thanks guys!

---

### Post by kainalu on 2010-09-24
I found out that couchdb and something called beam.smp were eating up about 475MB of memory. They had about, i'd guess, 100 processes running. I apt-get purged them, and now I got my precious performance back. Thanks for the help!

Oh, if anyone reads this for help, please realize that by purging these programs, you will lose Gwibber. I didnt care much, because it was broken on my system most of the time anyway, but thought i'd mention it.

---

