---
title: "What's the difference between these two?"
date: 2012-01-03
forum: General Help
---

### Post by DeadlyOats on 2012-01-03
In the "Additional Drivers" dialogue box, I see the following two options:

"NVIDIA accelerated graphics driver (version current) [recommended]"

and

"NVIDIA accelerated graphics driver (post-release updates) (version current-updates)

When I click between the two to read their descriptions, they say EXACTLY THE SAME THING.  The one that says, "recommended" kind of looks like it's not as good as the other one, because that other one says it has "current-updates".  You'd think *that* would be the "*recommended*" one.  It has "*CURRENT UPDATES*".

It's confusing.

So, what difference is there, between the two.  What reason should I need to choose one over the other, and not just 'cause one says it's "recommended"?

---

### Post by The_Third on 2012-01-03
I'm pretty sure that the one with "current updates" has better support for older graphics cards. Sorry, ain't got any sources but I do remember seeing that somewhere.

---

### Post by crazy bird on 2012-01-03
When i do a fresh install i always choose for the recommended driver. After that driver is installed i add the PPA of x-swat and upgrade the driver from that PPA:
 
- open a terminal
- type the following command: **sudo add-apt-repository ppa:ubuntu-x-swat/x-updates** 
- press enter and if asked for, type your pasword and press enter again
- then type: **sudo apt-get update** and press enter
- then type: **sudo apt-get upgrade** and press enter
 
If everything goed well, your nvidia driver will be updated with the latest stable upstream release.

---

### Post by tiznom on 2012-01-03
Do we have an answer for the original question? I'd like to know why the post-release updates are not the recommended choice, too.

---

### Post by Pilot6 on 2012-01-03
At the moment both nvidia-current and nvidia-current-updates are the same version 280.13. So there is no difference.
Generally speaking 'current' drivers are better tested and 'updates' are new. You first install current. If there are no problems you stay with them or can try updates for improvements, but there may be new bugs.
For instance, I have problems with the newest 290.10 on my GT430 card and I use 280.13. Is that the answer?

---

### Post by Bobhuber on 2012-01-03
> **pilot6 said:**
> at the moment both nvidia-current and nvidia-current-updates are the same version 280.13. So there is no difference.
Generally speaking 'current' drivers are better tested and 'updates' are new. You first install current. If there are no problems you stay with them or can try updates for improvements, but there may be new bugs.
For instance, i have problems with the newest 290.10 on my gt430 card and i use 280.13. Is that the answer?
+1

---

### Post by DeadlyOats on 2012-01-04
Thanks for your replies, folks!  That helped a lot.

---

