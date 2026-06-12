---
title: "I get this error how to fix"
date: 2009-07-21
forum: General Help
---

### Post by MarkBowlin on 2009-07-21
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by merlinus on 2009-07-21
Make sure that no other updaters or installers are running, e.g. synaptic, apt-get.  Open a terminal and type in the command:

```
sudo dpkg --configure -a
```

---

### Post by MarkBowlin on 2009-07-21
Setting up java-common (0.30ubuntu4) ...

Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 2 added doc-base file(s)...
Registering documents with scrollkeeper...

---

### Post by merlinus on 2009-07-21
Looks like your problem is solved.

---

### Post by MarkBowlin on 2009-07-21
Thanks

---

### Post by MarkBowlin on 2009-07-21
$ sudo apt-get install sun-java6-jre
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java6-jre: Depends: sun-java6-bin (= 6-14-0ubuntu1.9.04) but it is not going to be installed or
                          ia32-sun-java6-bin (= 6-14-0ubuntu1.9.04) but it is not installable
                 Recommends: gsfonts-x11 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by merlinus on 2009-07-21
Did you try

```
sudo apt-get -f install
```

---

### Post by MarkBowlin on 2009-07-21
just did now have a pop up
Package configuration with ok at bottom what to do now?
Because java is still not working on pogo games

---

### Post by michy99 on 2009-07-21
Use Tab key to select OK. Press Enter.

---

### Post by MarkBowlin on 2009-07-21
Thanks all

---

### Post by MarkBowlin on 2009-07-21
Will I need to reboot because still not working in POGO GAMES

---

### Post by michy99 on 2009-07-21
> **MarkBowlin said:**
> Will I need to reboot because still not working in POGO GAMES

Worth a try.

---

