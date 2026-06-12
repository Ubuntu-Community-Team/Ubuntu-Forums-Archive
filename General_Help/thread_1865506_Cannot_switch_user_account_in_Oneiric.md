---
title: "Cannot switch user account in Oneiric"
date: 2011-10-20
forum: General Help
---

### Post by hounddog32 on 2011-10-20
I installed 11.10 clean from the CD and I cannot switch users. When I am logged in and click either another user's name or "switch user account" from the users menu, I get a blank screen with just a flashing cursor top left. The only way to get back to something usable is to ctrl+alt+F7. The same thing happens when clicking switch user from the lock screen. Any ideas - I couldn't find a bug report that matched or figure out where best to post a new bug.

---

### Post by npwanabe on 2011-10-21
Same here. I created the same 4 user accounts as I had in Natty. I used the disc to clean install keeping data and software from before. Now my account will open and I get a strange desktop. No shutdown button. 2 other accounts won't open at all upon login. Just a black screen a flash or 2 then right back to the login screen. :(

---

### Post by hounddog32 on 2011-10-21
That sounds like a slightly different problem to mine. I can log into either account, but never both at once. Have you tried deleting the ~/.Xauthority file and trying the accounts again?

---

### Post by SpinUp on 2012-04-02
I'm having a similar problem with user switching.  There seems to be a relevant bug report here:
[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/884331](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/884331)

---

