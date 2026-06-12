---
title: "Loe Graphics Mode can't boot GUI in Linux"
date: 2011-02-15
forum: General Help
---

### Post by daldude on 2011-02-15
[FONT=Arial]I can't boot up my Ubuntu into the GUI because it it gives me error message saying Ubuntu is running low graphics mode because it can't detect my hardware properly and gives several choices to either continue in low graphics mode or manually set up the hardware or restart X server and some other choices that I can't remember. If I try to  choose manually set up hardware it does not accept any selection I select, if I try continue in low graphics mode it hangs on the booting up screen and never goes past that. The way I broke it was by using[SIZE=1] [/SIZE][/FONT][FONT=Arial][B][SIZE=1][SIZE=1]synaptic manager to remove anything related to Keyring because it kept popping up a box prompting me to enter a keyring password and even after I thought I updated the keyring password under passwords and encryption keys but that did not work. What does a keyring password have to do with my video card? Why can't it detect my hardware just because I removed the keyring drivers? If I boot with the live CD it has no problem detecting my graphics card.

I tried booting into Generic Recover mode and selected fix broken packages and it went through some long process of something but still did not fix my problem.
[/SIZE]
Why is it so easy to break Ubuntu, it's easier to break then XP. Why doesn't Ubuntu have a recovery mode like XP does where you can recover to an earlier state of Ubuntu that was before you made some kind of changer or broke something by messing with settings or drivers? [/SIZE] 
[/B][/FONT]

---

### Post by konnn on 2011-02-15
You might have problem with the xorg.conf archive.First I should tell you to log in terminally and do an update an then find in that folder wich the archive is if therre is an xorg.conf-old one.

---

### Post by daldude on 2011-02-15
How do I do an update and what do I update? Where do I find the xorg.conf archive and the  xorg.conf-old one?

> **konnn said:**
> You might have problem with the xorg.conf archive.First I should tell you to log in terminally and do an update an then find in that folder wich the archive is if therre is an xorg.conf-old one.

---

### Post by konnn on 2011-02-15
When you reach the low graph mode you can reach the terminal by ctrl+alt+F1, then u login and run "sudo apt-get update && sudo apt-get upgrade".

---

