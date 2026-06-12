---
title: "synaptic won't load"
date: 2009-09-10
forum: General Help
---

### Post by jono2009 on 2009-09-10
Hi there, I've done a fresh install of 9.04 and everything has been installed/ drivers/updates...went to use Synaptic and it's not opening. Got this screenshots...used  terminal as to the best of a n00bs ability.

Any help appreciated, thanks:(

---

### Post by Efwis on 2009-09-10
open terminal then cut and paste the code below

```
sudo dpkg --configure -a
```
then enter your password
let us know how it works.

---

### Post by wojox on 2009-09-10
The command is:

```
sudo dpkg --configure -a
```

---

### Post by jono2009 on 2009-09-10
Thank you both you're fixed it...Synaptic working:lolflag:

Solved

---

