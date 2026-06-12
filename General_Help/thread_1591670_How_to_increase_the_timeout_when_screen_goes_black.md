---
title: "How to increase the timeout when screen goes black?"
date: 2010-10-09
forum: General Help
---

### Post by jerrry94087@yahoo.com on 2010-10-09
My Ubuntu laptop's screen goes black in about 10 or 15 minutes.
I went into Screen Saver setup screen. Timeout when computer is considered  idle there is set to 30 minutes and black screen screen saves is picked.

Why screen goes black after only 10-15 minutes and not 30 minutes?

---

### Post by nothingspecial on 2010-10-09
Try System > Preferences > Power Management

---

### Post by jerrry94087@yahoo.com on 2010-10-09
No, it's also 30 minutes there.
And the actual timeout is 15 minutes or less.

---

### Post by glepore70 on 2010-10-09
I was just working on this issue, I've found that the various ways of setting the screen timeout in the gui are not always followed by the system.  I check the current values with xset -q  which lists the standby, suspend, and poweroff times.  I follow this web page:
[http://tldp.org/HOWTO/Battery-Powered/methods.html](http://tldp.org/HOWTO/Battery-Powered/methods.html)
when I want to remember the appropriate commands, it's an old page, but still accurate.  Putting the correct settings into the xorg.conf file seems to make them persist, but this file also gets overwritten occasionally, probably due to updates.  Good luck.

---

