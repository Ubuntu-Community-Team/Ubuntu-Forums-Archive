---
title: "System unresponsiveness after a couple hours' use after 9.10 to 10.04 upgrade"
date: 2010-05-07
forum: General Help
---

### Post by Tamale on 2010-05-07
Hello all,

I installed ubuntu 9.10 fresh on my laptop last year and have been using it with no problems for up to 12 hours at a time ever since.

After upgrading to 10.04, which went very smoothly for the most part, I'm not encountering total inability to use the system after a good period of normal operation.

After anywhere from 2-4 hours of normal operation, the system will suddenly become extremely unresponsive. I can click on items and enter text into dialog boxes, but I don't see the results of my actions until at least 20 seconds after performing them. The system monitor applet I have in my taskbar stops moving during this time, then updates at very sparse intervals (similar 20 second time frames).

A cursory glance at my dmesg logs shows a good deal of "link is slow to respond, please be patient (ready=0)" errors, which led me down a path of investigating a known [bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/297058") where other users are experiencing unresponsiveness, but my issues differs from theirs because I've never had this problem on this hardware before.. it only started happening after my upgrade to 10.04.

Could anyone help me further diagnose this issue to resolution?

Thanks in advance..

---

### Post by Tamale on 2010-05-11
So, I've narrowed this down to a compiz issue. While the system is sluggish, if I simply ssh into my machine and killall compiz everything becomes usable again (after restarting compiz or starting metacity instead). Is there a known bug in 10.04 with compiz that would cause this behavior?  How can I fix it? Compiz is the main reason I run ubuntu.

---

