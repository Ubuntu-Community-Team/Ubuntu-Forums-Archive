---
title: "session problem"
date: 2006-06-19
forum: General Help
---

### Post by tefflox on 2006-06-19
hi, this is my first post to the forum.  I'm new to linux, and very impressed. I'm getting just about everything I need up and going fine, except with my Session properties.  I can't figure it out.  There are two sessions "Default" and my username, and lately I checked "automatically save session" and then I restart and it brings up my home folder and the session properties window.  I unchecked the automatic save, restart and it still opens these two windows, and the properties in current session settings are all modified?  Is there a way to restore an installation default settings for sessions?  Also it is unclear what the "restart, normal, and settings" options mean in program "state".  Here is my "Current Session" with all the strange new settings:

50 normal gnome-session-properties
20 restart metacity
40 restart gnome-panel --sm-config-prefix /gnome-panel-rWdu72/
40 settings gnome-volume-manager --sm......
40 restart nautilus --sm-config.....
50 normal gnome-power-manager -sm-conf......
50 settings update-notifier --sm-conf......
50 restart gnome-cups-icon --sm-conf....

the long "--sm-conf.." values weren't there before trying the auto save session...

How can I change back to the "default" session?

thx

---

### Post by amireldor on 2007-06-23
hello

i had a similar problem, this session thing is a PITA but u can restore the default session by deleting ~/.gnome2/session

saw this solution [here]("https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/34321")

---

