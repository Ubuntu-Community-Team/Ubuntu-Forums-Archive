---
title: "How do I stop application when logging off?"
date: 2011-05-14
forum: General Help
---

### Post by dwhitney67 on 2011-05-14
I used **System->Preferences->Startup Applications** to start up a shell script (application) when I login.  How do I stop this application when I log out?

I've tried creating a ~/.logout file, where I determine the PID of the application I want killed (so that I can kill it), however it would appear that this file is never referenced when I log out of my Gnome session.

P.S.  I'm using Ubuntu 10.10 (or whatever the last release of 2010 is designated as).

---

### Post by Dave_L on 2011-05-14
This gets executed on logout: /etc/gdm/PostSession/Default

---

### Post by dwhitney67 on 2011-05-14
Thanks Dave_L.

With a little Googling, I found a related (yet outdated) [article]("http://help.lockergnome.com/linux/Kill-process-logout--ftopict421032.html") indicating something very similar.

---

