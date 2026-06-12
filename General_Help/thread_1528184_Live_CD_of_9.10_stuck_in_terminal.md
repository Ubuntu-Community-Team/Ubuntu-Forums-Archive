---
title: "Live CD of 9.10 stuck in terminal"
date: 2010-07-10
forum: General Help
---

### Post by RobAllen on 2010-07-10
Hey all, I am fairly new to Ubuntu but have used it before and can get around for the most part. I'm running a live CD of 9.10 on my laptop to try to fix a problem with Windows 7 and backup my drive, and I ended up stuck in full screen terminal. I did a ctrl+alt+F1 to get into it, and have tried ctrl+d, typing 'exit', typing 'logout', running 'startx', and hitting ctrl+alt+enter. None have worked, and I've got a backup running so I don't want to restart and risk data damage to my external drive. How can I get out of this full screen terminal session and back to the desktop? Thanks!

---

### Post by kukker32 on 2010-07-10
you're backing up using the terminal or other software???

and just hused the terminal meanwhile??

but anyway i use ubuntu 9.10 too. and try hitting the f11 key o enter/get out of fullscreen modes... should help..

---

### Post by RobAllen on 2010-07-10
I was using the dd command to backup my drive, and went into terminal to kill the process because I realized that dd makes a copy of the entire drive regardless of how much is on it, and I would run out of space on my backup drive before it was done. I killed the process no problem, but now I can't get out of terminal. I used ctrl+alt+F1 (for the first time) as just a shortcut, not knowing it would full screen it. I tried F11, no luck.

Any other suggestions?

---

### Post by DaithiF on 2010-07-10
Hi,
ctrl + alt + F7

or

type the command:
chvt 7

---

### Post by RobAllen on 2010-07-10
> **DaithiF said:**
> Hi,
ctrl + alt + F7

or

type the command:
chvt 7


GOT IT. Sweet, thanks!

---

