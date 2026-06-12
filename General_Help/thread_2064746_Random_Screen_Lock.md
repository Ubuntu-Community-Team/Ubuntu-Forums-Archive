---
title: "Random Screen Lock"
date: 2012-09-30
forum: General Help
---

### Post by irndog on 2012-09-30
Hi there,Im wondering if anyone is having the same issue Im having. I get random and persistent locking of the screen in Ubuntu 12.04. I know the next release is just round the corner but its driving me batty. It also seems to crash out certain programs running.

Generally the screen goes to lock whenever Im watching a video or doing anything at the PC for no reason. Ive even disabled screen lock in the preferences but to no avail. Thinking it may have been a power issue I have swapped PSU's and also HDD's instead of a dodgy install but it still keeps happpening.

Here are my system specs:

i5 750 Lynnefield
8 gig of corsair ram
PALIT Geforce 9800

Any one able to help or point me in the right direction? 

Thanks in advance.

---

### Post by 2F4U on 2012-09-30
What exactly do you mean by "screen lock", that the screen server kicks in and that you have to unlock it, or that you are kicked out of your desktop environment to the login manager?

---

### Post by irndog on 2012-10-01
It goees to the login manager with the login box down the left hand side of the screen. Its well odd.

---

### Post by 2F4U on 2012-10-01
Then it is not a screen lock, but rather your desktop environment (Unity, I am assuming) is crashing and in that process you are thrown out. In your home folder there should be a file ".xsession-errors" which contains messages (not only errors) about the desktop environment and applications running on it. It may contain useful information what happened and why it crashed.

---

### Post by radolavv on 2012-10-01
It hapens to mee too.

---

### Post by irndog on 2012-10-01
> **2F4U said:**
> Then it is not a screen lock, but rather your desktop environment (Unity, I am assuming) is crashing and in that process you are thrown out. In your home folder there should be a file ".xsession-errors" which contains messages (not only errors) about the desktop environment and applications running on it. It may contain useful information what happened and why it crashed.

Cool, thanks for that. Will have a look though that this weekend (PC's not at home) and post my findings. Many thanks!

---

