---
title: "system is not normal after upgrading 12.04"
date: 2012-03-05
forum: General Help
---

### Post by johnfriend on 2012-03-05
Hi, I have installed ubuntu 12.04 beta version in my laptop. due to power problem, upgradation stopped partially. when i try to boot my laptop it doesn't show anything. i tried ctrl+alt+f2 and typed 'sudo dpkg-reconfigure -phigh -a'. it asked to configure chillispot. i tried my best.but i couldn't recover. how to recover my laptop. kindly help me.

---

### Post by splater on 2012-03-05
I would suggest a backup with a live CD or USB stick and after a brand new installation with this beta.

Laurent

---

### Post by johnfriend on 2012-03-05
> **splater said:**
> I would suggest a backup with a live CD or USB stick and after a brand new installation with this beta.

Laurent
but I couldn't mount my external HD  . what to do?

---

### Post by nd456 on 2012-03-05
Has this drive worked before? If yes...
You probably will have to manually force mount...
[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)
If no...
You have a new issue on your hands...

---

### Post by dcstar on 2012-03-06
> **splater said:**
> I would suggest a backup with a live CD or USB stick and after a brand new installation with this beta.


I would suggest **never, ever** using a pre-release version for any "upgrade".

It isn't ready yet, only experienced bug hunters should use pre-release software that is still having bugs resolved and is weeks away from being suitable for general use.

---

### Post by Mark Phelps on 2012-03-06
> **johnfriend said:**
> Hi, I have installed ubuntu 12.04 beta version in my laptop. 
The Release Notes for 12.04 CLEARLY state that this version is only for Developers and Testers since it has  "issues".  So, which of these are you?

The Release Notes are linked to the download page -- and put there for a reason.

Suggest next time, READ the release notes before you download something.

---

### Post by Hikayu on 2012-03-06
It's quite a sticky situation now, and it wasn't a bug that caused this; it was a premature termination of the upgrade. This can happen easily in any upgrade.

Look, john, what you have to do right now is most likely to reinstall Ubuntu. There are ways to do this without losing *any* data, though. I'm very sure you can figure this out yourself, don't hesitate to ask if otherwise.

In a nutshell, the steps are as follows:
[LIST=1]
[*]Make a small partition
[*]install temp OS
[*]install new OS
[*]copy config files
[*]copy data files
[*]reinstall some core packages
[*]delete old partition
[*]expand original partition
[*]reconfigure GRUB to allocate the new partition. Or you could relabel it back.
[/LIST]

---

