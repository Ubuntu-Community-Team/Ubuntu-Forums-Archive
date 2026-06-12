---
title: "Can't stop the auto-login"
date: 2010-08-29
forum: General Help
---

### Post by Sageth on 2010-08-29
I was going through some settings and inadvertently changed the UID for my primary logon.  I then realized what I did and changed it back and set the group back to my username.

Since then, it only auto-logs in on startup.  I cannot get it to prompt for a password again.  I've tried normal things like changing "ask for password on login" and then changing it back, but that hasn't helped.  I'm sure there's something else that I'm missing, but don't know what it is.  

Right now, it says "asked on login" but it doesn't.  Any ideas?

I'm on 10.04

---

### Post by Sageth on 2010-08-31
No ideas?  I'm sure this is something stupid, but I just can't see it.  Any help would be appreciated.

---

### Post by varunendra on 2010-09-01
If you are using gdm (Gnome Display Manager), these may help you:
[http://ubuntuforums.org/showthread.php?t=1023326](http://ubuntuforums.org/showthread.php?t=1023326)
[http://ubuntuforums.org/showthread.php?t=1206935](http://ubuntuforums.org/showthread.php?t=1206935)

Note that in Lucid, you may not find the gdm.conf or custom.conf file in /etc/gdm. In such case, look in /etc/init folder for them.

---

### Post by Sageth on 2010-09-01
You, my friend, are my hero of the week.  I spent a lot of time looking for the answer and had no idea that the .conf file existed.  It fixed me right up.  

Thanks a bunch.

---

### Post by varunendra on 2010-09-02
My pleasure!! :)

It's really a very good feeling to see a thread [Solved] in which you've contributed. Thanks for blessing me with the "feel-good-factor" so early in the morning!
:popcorn:

---

