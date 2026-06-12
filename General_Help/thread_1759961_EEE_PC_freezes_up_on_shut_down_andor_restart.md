---
title: "EEE PC freezes up on shut down and/or restart"
date: 2011-05-16
forum: General Help
---

### Post by mileniasm on 2011-05-16
Hi everyone!

I love Ubuntu, and I've been using it ever since a friend of mine recommended it last year. The problem I've been having lately is that no matter what version I use, and how I install it, it keeps freezing up on shut down and/or restart. It's been doing that for the past 6 months or so, and I had stopped using it for awhile, because I wanted to wait for the latest release and see if it keeps happening. Well it does...

I am currently using the new windows installer, wubi, and I don't see any difference from the way it was before, when I installed it directly, not through Windows... I keep seeing the same problem, however, and I am really starting to get tired of it.

Can anyone help me please? 

Thanks in advance!

---

### Post by rolfy on 2011-06-27
This could be caused by problems with the wlan adapter that have been around since maverick. This solution worked for me: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/594866/comments/14](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/594866/comments/14)

(It froze when I shutdown after making this change, but the next time I booted, it shutdown properly.

I'm sorry, I don't even know what that code is doing - I suspect it may disable the wireless altogether (I don't care, since I'm not using it) - There seem to be quite a few solutions out there to the wlan problem, though, so find one that works for you.

Best of luck!

EDIT: Actually, my wireless still seems to be working just fine, too.

---

### Post by mileniasm on 2011-07-02
THANK YOU! THANK YOU! THANK YOU!

Rolfy, you rock!!! I installed nautilus so I can open the file as admin, and I added the code described in the forum link you gave me. It worked like a charm. For awhile before that, my wireless wasn't working, and this solution fixed both my problems. 

Thanks!

---

### Post by rolfy on 2011-07-11
You're very welcome (and I'm just a dwarf standing on the shoulders of giants - glad I happened to be on the right giant at the right time to help)

---

