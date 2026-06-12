---
title: "Transmission won't run"
date: 2009-09-10
forum: General Help
---

### Post by bogman on 2009-09-10
I was experimenting with using different ports for transmission and it crashed and wouldn't run after that.  I've uninstalled and reinstalled with no change.  I tried to run it from Applications and Gnome do and neither will work.

I'd appreciate any help.

---

### Post by Vaphell on 2009-09-10
run transmission from terminal and see if you get some error message there

---

### Post by wojox on 2009-09-10
Open Synaptic and mark for complete removal.
Then go to your home folder and View hidden files
Look for .config
Open and look for transmission - delete it.
Open a terminal:

```
updatedb
```

Reinstall transmission.

---

### Post by bogman on 2009-09-10
Thanks wojox,

I followed your instructions and Transmission works now.

I greatly appreciate your (extremely fast) help.

Problem solved.

---

