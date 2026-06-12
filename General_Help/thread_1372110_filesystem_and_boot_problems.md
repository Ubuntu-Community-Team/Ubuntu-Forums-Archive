---
title: "filesystem and boot problems"
date: 2010-01-04
forum: General Help
---

### Post by migreatstsin on 2010-01-04
Alright, i'm not a complete newbie to ubuntu, but i'm probably not as experienced as most.

Current problems with Ubuntu 9.10 Karmic:

so the problem that i'm having is that when i'm using the computer, everything goes fine, but then when i walk away from it and then come back, the computer starts getting all screwed up.  it will not let me open any programs, will not let me mount or unmount any drives, will not allow me to make any changes to any files, even move them to the trash.

the only way that i've found to fix this is to restart the computer.  when i do this, either ubuntu will state that the filesystem has errors and will go through the filesystem check on the loading screen (white ubuntu symbol) or it gives me prompt and i have to use fsck manually.  usually this works, but has taken me a few tries to get it to work.  it will then work fine, until i leave the computer for any length of time and then come back, its the same.

i've already set it so the screen-saver does not come on, which i saw that some people were having problems with.  no idea of where to go from here... help please!!!

---

### Post by migreatstsin on 2010-01-04
bump

---

### Post by migreatstsin on 2010-01-05
re-bump...

---

### Post by hariks0 on 2010-01-05
Are you using blue-proximity?

---

### Post by SecretCode on 2010-01-05
Odd. It sounds like your file system is becoming read-only. I don't know how this could happen, though. 

If you leave a terminal window open, can you enter commands (that don't change files) like ls?

Even better, can you go to a tty with ctrl-alt-f1/f2/f3...?

The place to start looking might be in the system logs (note the time the problem last started and go to System > Adminstration > Log File Viewer).

---

