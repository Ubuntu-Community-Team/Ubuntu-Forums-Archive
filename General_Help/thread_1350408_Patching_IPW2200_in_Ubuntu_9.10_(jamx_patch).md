---
title: "Patching IPW2200 in Ubuntu 9.10 (jamx patch)"
date: 2009-12-09
forum: General Help
---

### Post by sayw3rd on 2009-12-09
Hi all,

I recently upgraded to Ubuntu 9.10 by doing a clean install. I then decided to patch my ipw2200 driver following these instructions:
[http://precompiled.de/~jamx/]("http://precompiled.de/~jamx/").

I believe I installed all the compilers, kernel headers, modules, etc, correctly, but I still run into a problem following this step:

*for ubuntu 9.10 this would be 'make IEEE80211_INC=/lib/modules/2.6.28-11-generic/build/include'*

which results in:

[I]-e 
 ERROR: ieee80211.h not found in '/lib/modules/2.6.31-16-generic/build/include/linux/'.

-e You need to install the ieee80211 subsystem from [http://ieee80211.sf.net](http://ieee80211.sf.net)
and point this build to the location where you installed those sources, eg.:

% make IEEE80211_INC=/usr/src/ieee80211/

will look for ieee80211.h in /usr/src/ieee80211/net/

make: *** [check_inc] Error 1
[/I]

The odd part is when I use terminal to go into the directory '/lib/modules/2.6.31-16-generic/build/include/linux/', I can see the file ieee80211.h there and I can also open it with gedit. I've been searching on google and jumping from forum to forum trying to find a solution but I end up going in circles and getting the same out-dated solutions that don't apply to this new patch and situation. I'm really stumped and if someone could please help me with this I'd be forever grateful. Thanks in advance!

---

### Post by sayw3rd on 2009-12-09
Anyone? Can someone with patching knowledge please help me out.

---

