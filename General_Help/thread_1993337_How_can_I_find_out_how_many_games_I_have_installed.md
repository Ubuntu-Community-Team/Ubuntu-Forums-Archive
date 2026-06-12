---
title: "How can I find out how many games I have installed?"
date: 2012-06-02
forum: General Help
---

### Post by ingramproductions on 2012-06-02
I'm using 12.04 and I've installed quite a few games through the software center. I'd like to know how many games I've installed.

Does anybody know I can find out the number of games installed on my system?

---

### Post by satish_j on 2012-06-02
go to software center->Installed applications-->select category as Games.This should list all installed games.

---

### Post by ingramproductions on 2012-06-02
> **satish_j said:**
> go to software center->Installed applications-->select category as Games.This should list all installed games.

Thanks, that will give me a list of installed games. But if I have several hundred games, I'd have to count each one in the list.

Is there not a way to get a number?

---

### Post by Vaphell on 2012-06-02
ctrl+alt+t to open terminal
to get names
```
grep -h '^Name=' $( grep -l '^Categories=.*Game' /usr/share/applications/*.desktop )
```
to get number
```
grep -l '^Categories=.*Game' /usr/share/applications/*.desktop | wc -l
```

It checks in the standard dir where the programs installed from repos store their identifier files. Number may be inaccurate, because emulators or level editors attached to games having their own .desktop file and tagged as Category=Game; will be counted as well.

---

### Post by ingramproductions on 2012-06-02
Thanks, that is what I was looking for!

---

