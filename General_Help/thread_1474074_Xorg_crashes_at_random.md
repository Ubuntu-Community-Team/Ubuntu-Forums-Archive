---
title: "Xorg crashes at random"
date: 2010-05-05
forum: General Help
---

### Post by LinScape on 2010-05-05
Hi, Ive been having some problems with a Compaq computer with Lubuntu installed.
The problem is that Xorg crashes at random displaying a white distortion on the screen and it usually doesn't let me go to a terminal and i have to force a shutdown.
the same happened when I tried to install Ubuntu but worse.
Another side effect is that lubuntu at boot up displays its logo in 16-bit colors and then goes to normal colors.

how can i diagnose the random crashes?

---

### Post by quadproc on 2010-05-05
> **LinScape said:**
> Hi, Ive been having some problems with a Compaq computer with Lubuntu installed.
The problem is that Xorg crashes at random displaying a white distortion on the screen and it usually doesn't let me go to a terminal and i have to force a shutdown.
the same happened when I tried to install Ubuntu but worse.
Another side effect is that lubuntu at boot up displays its logo in 16-bit colors and then goes to normal colors.

how can i diagnose the random crashes?
You may get some useful information from the log files, particularly the /var/log/Xorg.0.log file.

I don't know which version of Ubuntu you are using; the 10.04 release has an awful lot of display related bugs being reported right now.

Which graphics driver are you running?

quadproc

---

### Post by LinScape on 2010-05-05
If im correct the machine has an intel video card. (and yes im running lubuntu 10.04)

---

### Post by LinScape on 2010-06-17
I dont exactly know the name of the driver right now (since i lost access to the machine) but i know it has an intel chip and the problem also occurs with other distros like macpup, puppy linux, lubuntu and ubuntu alike. It also occurs at random or when i try to install software in lubuntu.

---

