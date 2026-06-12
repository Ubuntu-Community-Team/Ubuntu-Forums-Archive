---
title: "new install 11.04 VERY slow resuming from screensaver"
date: 2011-05-25
forum: General Help
---

### Post by newseamus on 2011-05-25
I recently did a fresh install of 11.04 (previously had 9.10)
Everything works fine and dandy (I didn't have to do much tweaking at all to this version!!!)
Except:
When my computer resumes from the screensaver (GL text, set to display time) it takes nearly a minute for my DE to show up. When it finally does show up it takes another minute or more for the computer to run at normal "speed". A lot of lag and unresponsive mouse etc. 
After a few minutes the computer runs fine...I am not so linux savvy, what I know I have gleaned from forums such as this one. Is there something that 11.04 runs as default that I need to shut off to stop my slow resume problem?
thanks for the help.

---

### Post by shwaip on 2011-06-06
Hi:

gltext has a substantial memory leak. change your screensaver to something else and it should go away. On my machine, memory usage goes up by about 32 MB/s.

---

### Post by newseamus on 2011-06-07
yep that did the trick...but now i need to get a clock for my bedroom....heh

---

