---
title: "Ubu11 seems awfully buggy"
date: 2011-05-24
forum: General Help
---

### Post by Mugsy323 on 2011-05-24
Am I alone in finding way too many problems with Ubuntu-11 than any upgrade should have? (Please read to end for my question.)

I updated from 10.10 to 11.04, and the first problem I had was 11.04 would not boot (I *could* boot 11.04 if I chose "load previous version" from the Grub boot menu.) This was eventually fixed reinstalling 11 on top of 11 from an install CD.

The new desktop is nothing but trouble. I eventually switched back to "Classic" mode because of it. First off, with no "Task Bar" at the bottom, you can't tell what programs have been minimized and still running in the background (and forget about launching & switching between multiple instances of the same program.) And why do you need mounted drives on BOTH the desktop AND the new Launch Bar? The new Launch Bar gets very full very fast if you have a lot of drives like I do (mostly thumb drives).

Problem: I'm suddenly finding that file & app windows don't always open, of if they do, open blank (hitting F5 to refresh simply gives me a "busy" pointer that never ends.) And right now, I can not open my Downloads, Computer, or any other folder listed under "Places" (or from the Home button on the new GUI's Launch Bar.)

I'm not sure what's going on, but 11.04 seems like it may have been released a bit too soon.

---

### Post by mikewhatever on 2011-05-24
If you want support, please post you computer specs, and especially the graphics card model.
If you want to chit-chat, check out the Cafe.

---

### Post by Mugsy323 on 2011-05-24
> **mikewhatever said:**
> If you want support, please post you computer specs, and especially the graphics card model.
Thanks for the reply (I guess).

My specs are fairly irrelevant, since Ubu is up and running, and I'm not experiencing hardware issues, but here you are:

Phenom II x4 processor.
4GB of ram.
ATI Radeon HD 5850 video card
Onboard Realtek audio.
Booting Ubuntu off an external 160GB USB drive.
Three 500GB HDD's, one IDE and two SATA.
Five USB Flash drives (one 64GB, two 32GB, two 1GB)
DSL connection.

And I don't think a "chat" will tell me why I keep having to reboot to get certain windows... like "Computer"... to open.

---

### Post by mikewhatever on 2011-05-24
Given the 'ATI Radeon HD 5850' card, which driver do you use? Does the problem you describe happen when using the Classical (no effects) option?

> **Mugsy323 said:**
> ...

And I don't think a "chat" will tell me why I keep having to reboot to get certain windows... like "Computer"... to open.

No, but it will address the other 3/4 of the OP. O:)

---

### Post by linuxinstalledfromhdd on 2011-05-24
For the sake of simplicity, why not roll it back to 10.10 for now so you can have a functional system, and post a bug report with logs and everything?

---

### Post by Mugsy323 on 2011-05-24
> **mikewhatever said:**
> Given the 'ATI Radeon HD 5850' card, which driver do you use? Does the problem you describe happen when using the Classical (no effects) option?
As far as I'm aware, Ubu is using the latest driver. I am not prompted for an update when I open the Devices dialog.

The problem occurs with both the new GUI and in Classic view.

A bit of investigation *seems* to suggest the problem is somehow connected to Wine. The latest version does not work well with 11.04, and attempting to run programs which then fail to open, seems to be choking the system and preventing other tasks to complete while Wine tries to execute its last command.

I'll know for sure after a few more tests (the problem is too inconsistent to know for sure.)

---

### Post by linuxinstalledfromhdd on 2011-05-24
Do yourselves a favor and test the latest version before you upgrade to it with a nice USB live stick of whatever the latest thing is.

---

### Post by mikewhatever on 2011-05-24
Two types of graphical drivers are available for Nvidia and ATI cards in Ubuntu. The ones used by default are open source, while the other type is the proprietary drivers supplied by the vendors. It doesn't have to be the latest, but which of the two do you use?

---

### Post by linuxinstalledfromhdd on 2011-05-24
They would need to go to the command line and cut and paste that after probing their video card.

---

### Post by Mugsy323 on 2011-05-25
> **linuxinstalledfromhdd said:**
> They would need to go to the command line and cut and paste that after probing their video card.
All a USB Live test tells you is *hardware* compatibility. Only a *full* install tested with drivers & installed applications can truly tell you if an update is bug free.

---

