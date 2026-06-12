---
title: "Sim City 2000 in Wine"
date: 2009-11-10
forum: General Help
---

### Post by a person on 2009-11-10
I cannont install Sim City 2000 in wine.  I get

```

zach@blue:~/Downloads/SimCity 2000$ wine INSTALL.EXE 
wine: Cannot start DOS application "Z:\\home\\zach\\Downloads\\SimCity 2000\\INSTALL.EXE"
      because vm86 mode is not supported on this platform.

```

Any help/suggestions?

---

### Post by MelDJ on 2009-11-10
sims seems to be rated as garbage by winehq. so i recommend installing windows through virtualbox then installing sims if you have a windows disk

---

### Post by ireneshusband on 2009-11-10
You cannot run it in Wine because it is not a Windows application. It is an MS-DOS application (older versions of Windows ran on top of MS-DOS and some games continued to run in MS-DOS mode for performance or simplicity). Try running it in Dosemu instead ("sudo aptitude install dosemu").

---

### Post by a person on 2009-11-10
> **MelDJ said:**
> sims seems to be rated as garbage by winehq. so i recommend installing windows through virtualbox then installing sims if you have a windows disk

It was rated gold when I checked (I even [double checked](http://appdb.winehq.org/objectManager.php?sClass=application&iId=504)).  I do not have a windows disc and I'd like to keep it that way :).  Thank you for your suggestion though.

---

### Post by MelDJ on 2009-11-10
oh.. i think i understood you wrong. i am sorry

---

### Post by a person on 2009-11-10
> **ireneshusband said:**
> You cannot run it in Wine because it is not a Windows application. It is an MS-DOS application (older versions of Windows ran on top of MS-DOS and some games continued to run in MS-DOS mode for performance or simplicity). Try running it in Dosemu instead ("sudo aptitude install dosemu").

Good call!  It worked perfectly in dosbox.  I can't believe I didn't think that before.

---

### Post by scarf on 2011-12-11
on my cd there are three versions: one for dos, one for win 3.1, and one for win 95.  while the dos version works fine with dosbox, the resolution isn't that great, and i had glitchy sound.

the win95 version installs and runs perfectly on wine 1.2.2-0ubuntu2~lucid1.  i just ran `wine setup.exe`.  there is an issue with it crashing when trying to load/save a city, and that is overcome by setting your windows version to NT 3.5 in the wine settings.

---

