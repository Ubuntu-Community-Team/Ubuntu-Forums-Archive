---
title: "Problems with logging in"
date: 2011-04-21
forum: General Help
---

### Post by connor3485 on 2011-04-21
So i want to start this thread by saying i normally utilize google to find all of my problems. and i have yet to find a problem like this.

with that said, this is my problem.
i am running ubuntu 11.04 beta 2 x64 with the latest updates (up to 4/21/11). 
When i try to log into my account in gdm, i entered my password and hit enter, the screen goes black and gdm restarts again showing my user. i've tried debugging this message buy running gdm in tty mode, and all i can get is the vague message "Warning: unable to find users: no seat id found." i am able to log in under the root user, but not my own user like i said. i dont know if it is related, but this problem popped up after resizing my partition to a larger size. i have done disk checks and they all show ok. 

any help with this issue would be much appreciated!

---

### Post by bmathis on 2011-04-22
I suspect that whats happening is similar to this bug [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/433928]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/433928") which seems to have an answer from the Fedora group [https://bugzilla.redhat.com/show_bug.cgi?id=545267#c51]("https://bugzilla.redhat.com/show_bug.cgi?id=545267#c51")

I don't know if that's going to help you or not, but its a start.

---

### Post by connor3485 on 2011-04-22
> **bmathis said:**
> I suspect that whats happening is similar to this bug [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/433928]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/433928") which seems to have an answer from the Fedora group [https://bugzilla.redhat.com/show_bug.cgi?id=545267#c51]("https://bugzilla.redhat.com/show_bug.cgi?id=545267#c51")

I don't know if that's going to help you or not, but its a start.

I'm not having any problems with mouse/keyboard or anything on gdm startup. its just when i try to log in to my user is when it restarts and starts over. although when i try to log into "root" it logs in just fine.

---

