---
title: "Firefox 3.5 &quot;Looking up...&quot;"
date: 2009-07-21
forum: General Help
---

### Post by QIII on 2009-07-21
Before you respond:  IPV6 is disabled!  about:config has been made identical to my Firefox 3.0.11, so I have all the other tweaks applied.

Firefox 3.5 hangs on "Looking up ..." on BOTH my Jaunty machine and my Karmic machine.

I have uninstalled both 3.0.11 and 3.5, purged, removed profiles, removed hidden folders and reinstalled 3.5 clean.  There are no issues with multiple profiles.

I have checked connectivity, which is fine.  Other browsers work fine.

Even so, I recycled my modem and my router.  No improvement.

Any ideas beyond the standard fare?

---

### Post by mike555 on 2009-07-21
Try setting your DNS servers to  208.67.222.222   &   208.67.220.220     .... and make sure Firefox is not set to use a proxy (unless you need to)

---

### Post by lovinglinux on 2009-07-21
It could be a dns issue. Try this [http://blog.taragana.com/index.php/archive/simple-firefox-hacks-to-boost-performance/](http://blog.taragana.com/index.php/archive/simple-firefox-hacks-to-boost-performance/)

Please tell me if it works, because I'm considering putting this tweaks on my tutorial [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567).

I use them and they did helped me one day when I was experiencing DNS issues.

---

### Post by QIII on 2009-07-21
Thanks to both of you.  I'll give each a try when I get home -- I'm currently taking a coffee break at work and using a Windows (hack, cough) machine.  FF 3.5 works perfectly well here -- I'm using it now.  

I haven't installed it on either of my Vista machines at home, nor have I tried it from my XP machine.

lovinglinux -- I'll definitely get back to you if either of the suggestions work.  I cruised the Mozilla forums and found a number of posts with this very complaint.

But since 3.5 works for so many, I have to believe that I have some environmental variable that is causing problems.  I'd be convinced it was an FF issue if each of my 5 machines at home had its own internet connection, but I am going through a common router and suspect now that the router may be the issue.  

My next step beyond these suggestions is the router, and I'll let you know if that turns out to be an issue.  Since it is possible you won't be monitoring this thread, I may get back to you with specifics via PM.  I'd be happy to give you something to add to your tutorial to help the community.

---

### Post by QIII on 2009-07-22
Solved.

Recommend the tweaks and solutions at these sites:

[http://blog.taragana.com/index.php/archive/simple-firefox-hacks-to-boost-performance/](http://blog.taragana.com/index.php/archive/simple-firefox-hacks-to-boost-performance/)

[https://www.opendns.com/start/device/ubuntu](https://www.opendns.com/start/device/ubuntu) 

[http://www.pronetworks.org/forums/how-to-speed-up-mozilla-firefox-t79734.html](http://www.pronetworks.org/forums/how-to-speed-up-mozilla-firefox-t79734.html)

---

