---
title: "A problem with login in..."
date: 2010-06-15
forum: General Help
---

### Post by mp3c on 2010-06-15
After I installed Ubuntu 10.04 LTS on my Desktop off my CD, I went ahead and created 3 new Users in the Users and Groups. After those were created, I tried logging off. There, the Screen had the login window, the time/date and the power button. The mouse works, yet cannot click on anything. This happened after logging in for the first time, and booting into Ubuntu. 

Any solutions,
mp3c

EDIT:I re-installed Ubuntu, and the problem persists. Is it that the ISO file I have is corrupt, or that something went wrong while booting.

---

### Post by trifgabi on 2010-06-15
> **mp3c said:**
> After I installed Ubuntu 10.04 LTS on my Desktop off my CD, I went ahead and created 3 new Users in the Users and Groups. After those were created, I tried logging off. There, the Screen had the login window, the time/date and the power button. The mouse works, yet cannot click on anything. This happened after logging in for the first time, and booting into Ubuntu. 

Any solutions,
mp3c

EDIT:I re-installed Ubuntu, and the problem persists. Is it that the ISO file I have is corrupt, or that something went wrong while booting.

I did notice a huge lag when you log in as a user, as opposed to administrator. Did you try waiting a couple seconds before clicking?

---

### Post by happyhamster on 2010-06-15
- Is the problem when logging out, or logging back in again? In the latter case, when at the login screen, try pressing ctrl-alt-F3 (to get into a console), then pressing ctrl-alt-F7 (to switch back to the login screen again). Can you login now?

- Or: press ctrl-alt-F3, and login at the command prompt. Then restart gdm with: 

sudo service gdm restart

- Or: press ctrl-alt-F3, and login at the command prompt. First, stop gdm:

sudo service gdm stop

- Then start x (the graphical environment):

startx

- Good luck.

---

### Post by mp3c on 2010-06-18
Thanks guys:
I did a Wubi installed and solved it.
Turns out I burned the disc incorrectly.

---

