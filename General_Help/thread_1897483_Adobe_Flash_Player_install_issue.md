---
title: "Adobe Flash Player install issue"
date: 2011-12-19
forum: General Help
---

### Post by KevzJD on 2011-12-19
Hi, I've just installed Ubuntu 11.10 and im trying to install Adobe flash player from the software centre, when i click "install" it doesnt do anything. I've tried doing "sudo apt-get install adobe-flash-player" and it says it cannot find the adobe flash player package. Any suggestions?

Thanks in advance.

---

### Post by seawolf167 on 2011-12-19
Try installing the [restricted extras package ]("https://help.ubuntu.com/community/RestrictedFormats")instead (it includes flash and also includes a number of other items you may eventually want)

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by gandaran on 2011-12-19
> "sudo apt-get install adobe-flash-player"
```
sudo apt-get install flashplugin-installer
```
32-bits only, if you have 64-bits ubuntu you need a different package.

---

### Post by KevzJD on 2011-12-19
Wicked it works..thanks alot.,

---

### Post by seawolf167 on 2011-12-19
> **KevzJD said:**
> Wicked it works..thanks alot.,

:) Please mark this thread as Solved under Thread Tools

---

