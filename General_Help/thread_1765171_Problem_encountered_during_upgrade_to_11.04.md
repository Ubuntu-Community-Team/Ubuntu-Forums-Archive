---
title: "Problem encountered during upgrade to 11.04"
date: 2011-05-22
forum: General Help
---

### Post by RelativelyNew on 2011-05-22
I was minding my own business when a pop-up appeared telling me there was a new version of Ubuntu available for upgrade.  Having read that it would take a while, I clicked on upgrade and walked away.  Here is the message that is displayed when I boot Ubuntu:

There are 4 messages that start with init: with some messages after that.  The next line reads "The disk drive for / is not ready or present and gives me the option to wait, skip mounting or do something manually.  I waited. Nothing.  I don't want to click on the others because I don't know what they will do. 

Anyone have a clue what's going and how I might be able to fix it or just cancel the whole process and go back to the previous version?

---

### Post by linuxinstalledfromhdd on 2011-05-22
1) Pulse M to get the console
2) Remount / as RW: mount -n -o remount,rw /
3) Finish the upgrade: dpkg --configure -a

---

### Post by RelativelyNew on 2011-05-22
It worked!  Thank you so much!

---

