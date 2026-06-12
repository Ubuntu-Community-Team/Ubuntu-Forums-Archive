---
title: "Fan stops running after a couple hours. Restart required..."
date: 2011-04-17
forum: General Help
---

### Post by emtdan on 2011-04-17
I am unsure if this is a hardware problem or a linux problem.  My machine is only 3 months old so it is not the fan.  I didn't have problems until recently, and after the latest kernel update it got worse - having to restart more frequently.  

I do not experience the fan turning off in windows. I use thinkfan when I have to but it isn't a very good program for an every day basis.  The fact I can force start the fan with thinkfan when it turns off leads me to believe it is a kernel issue.  Is this possible?

---

### Post by TeoBigusGeekus on 2011-04-17
Try to boot to an older kernel from grub and see if the problem persists.
If not, modify grub to boot to this kernel and wait for an update with a newer one to see if your problem is solved.

---

### Post by emtdan on 2011-04-17
I'm running off an older kernel now ".27" instead of ".28".  So far it is doing ok. I'm hoping this is the only problem.  I love linux but between the fan and the wireless not working with network manager it is hard keep using it.  Hopefully Natty has solved a lot of issues with the new thinkpads.

---

### Post by TeoBigusGeekus on 2011-04-17
Ubuntu != Linux

What about your wireless? Have you started a thread about it?

---

### Post by emtdan on 2011-04-17
Didn't have to.  It is a well documented issue.  Here is one forum

[http://ubuntuforums.org/showthread.php?t=1597881&page=9](http://ubuntuforums.org/showthread.php?t=1597881&page=9)

There was another replica but I've since lost the link. I keep posted to that forum in hopes someone will find an answer...

EDIT: It is the Realtek Wireless card that is the issue - which is in more than just thinkpads.

---

