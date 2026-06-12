---
title: "To upgrade to 686, what commands (pentium 4)?"
date: 2006-05-01
forum: General Help
---

### Post by jms830 on 2006-05-01
To upgrade my ubuntu system for a pentium 4 chip, do I simply need to do
```
sudo apt-get install linux-image-2.6.12-9-686

```

or are there more things i have to install??

Oh and what can I apt-get remove afterwards to keep my system clean? (its a fresh install of breezy)

---

### Post by trent dillman on 2006-05-01
```
sudo apt-get install linux-686
```

This metapackage should install what you want, and update it as well!

I'd keep the 386 kernel around for a while, as a working backup kernel...

---

### Post by cskeide on 2006-05-01
A simple
```
sudo apt-get install linux-686
```
should do the trick.

After this you could always remove linux-386 and its dependencies.
```
dpkg -l | grep linux- | grep 386
```
Those packages should be safe to remove after you've rebooted into your new 686 kernel and made sure everything works.

A nice little command to remove those packages:
```
sudo dpkg -P `dpkg -l | grep linux- | grep 386 | cut -d " " -f 3`
```
PS. Use at own risk =)

---

### Post by jms830 on 2006-05-01
sounds good, thanks!

---

### Post by ketsugi on 2006-05-01
What are the benefits of using a 686 kernel for a P4 instead of the 386 kernel? Should I be expecting performance increases?

If I'm using a Mobile P4, should I still go for the 686 kernel or is there a different build to grab?

---

### Post by Bloch on 2006-05-01
I moved to the 686 kernel and have experienced no problems. I have not noticed any difference. There seems to be few benchmarks and comparisons done on comparing the two. I'd like to find out if there is any benefit. Otherwise I'd have to advice a totally non-technical user, don't bother, leave your system alone, even if only to avoid the couple of extra entries on the grub boot-up screen

---

