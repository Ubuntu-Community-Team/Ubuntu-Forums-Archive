---
title: "[SOLVED] How the heck did my user account expire?"
date: 2006-05-17
forum: General Help
---

### Post by RavenOfOdin on 2006-05-17
Hey, I've gotten myself into a slight problem over the past half day or so. It goes as follows: I installed a theme off KDE-Look entitled "Berlin Subway", and put it in my theme manager via kcontrol.  Then I had to log out a while later to get some stuff done.

When I come back to my n*x box and attempt to log in, the message given to me in a popup box is more or less:

```

"Your account has expired, please contact the system administrator." 

```

How did this happen?  My account (the one I was given when installing Ubuntu, and definitely NOT root) shouldn't have been set to expire.  The only thing that was on a timer to expire was my password, in 4 days no less - after which I would have to select a new one.  

I've looked in all the usual logs via recovery mode and haven't found any unusual entries in kernel.log or user.log . . . as a matter of fact I'm not even recorded as having made log in attempts, in the latter.

The latest entries in Xorg.0.log relate to not being able to decipher font extensions.  Could this be related to the new theme? 

Most importantly, how do I get my account back up and running?  I've uninstalled the new theme, but no go.  I'm 95% sure I wasn't cracked because my Linux install has - mostly - not been Internet-connected over the past few days. And when it has been, its only been for a few seconds at a time.

Can anyone help me? This is getting really annoying. If I knew the new version of KDE had so much trouble with themes I woulda sticked with GNOME.

---

### Post by RavenOfOdin on 2006-05-17
Okay, I've run chkrootkit and the last utilities in recovery mode; found nothing.
So there goes that.

I think I've found how to get my account enabled again through usermod -e.

(EDIT: Done. Never mind.)

---

