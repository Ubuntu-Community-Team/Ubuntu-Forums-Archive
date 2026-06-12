---
title: "Ubuntu extremely slow"
date: 2010-03-25
forum: General Help
---

### Post by tsliu on 2010-03-25
Hello,
  A newbie question here. I've been running Ubuntu for a while, everything pretty smooth. Lately, I observed some weird behavior occasionally. I leave my machine on overnight and when I return the next day and type my password to log in, it takes forever, e.g., the black screen will roll up like a curtain to reveal the desktop background. Everything is very slow, like double clicking anything, or typing a command in terminal. It felt the system is almost frozen. I either have to logout or reboot to restore the speed. This also causes me unable to ssh to it from home (this is a machine at work), as ssh will hang indefinitely (although it responds to ping). 
  This doesn't happen very frequently but often enough for me to ask for help here. First, is my machine being hacked? How do I know that? I also felt this may have to do with me running Windows XP in VirtualBox--I sometimes just leave Windows running. Could it hang Ubuntu? It seems when I turned it off a few times, this doesn't happen, although I'm not too sure about this correlation. I hope someone has some insight of what this is. I'm running Ubuntu 8.10 64bit version.
  Thank you,

--tsl

---

### Post by Johnny B on 2010-03-25
run the "top" command in the terminal to see what programs are using cpu and memory when the system is running slow
other than that, check your system > preferances > power management settings

---

