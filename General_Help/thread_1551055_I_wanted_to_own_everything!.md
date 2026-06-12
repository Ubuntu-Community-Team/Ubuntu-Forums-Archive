---
title: "I wanted to own everything!"
date: 2010-08-11
forum: General Help
---

### Post by UberDutch91 on 2010-08-11
So I got tired of having to type sudo everywhere. Specifically there was something wrong with my home directory because I couldn't call mkdir without sudo. So I decided that it would be a good idea to chown the folder. And it worked! It solved my problem. However, then I got careless. I decided that I wanted to own everything. So I called:
chown -R charles.charles /

When I boot I can no longer log in. It doesn't bring up the login screen, just a box that tells me the computers name. I can now only log in while in recovery mode. I didn't understand chown at the time. I figure that it must have gotten rid of all of the symbolic links that are required to make "magical ubuntu stuff" happen.

Oh yea, I'm running karmic.

Any suggestions to fix this? Thanks.

---

### Post by clhsharky on 2010-08-11
The day I'm to lazy to sudo is the day I have no business being a system admin.
I do know how to raise privileges as needed, its well documented, left default is recommended. 

Sharky

---

