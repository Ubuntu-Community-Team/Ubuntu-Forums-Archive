---
title: "A few post installation issues with Lubuntu 10.10"
date: 2011-02-06
forum: General Help
---

### Post by Jose Catre-Vandis on 2011-02-06
Trying out Lubuntu 10.10 as it now seems to have come of age.

Pretty good out of the box experience, but a couple of problems:

My function keys (F1 - F12) don't seem to work properly in terminal. When using alsamixer or htop they either don't work, drop me out of the program, or perform a function of a different FN key. Never had this problem with any Ubuntu variant before. Is it LXterminal causing the problem or something else?

Synaptic's quick search box is greyed out

How to completely replace PCmanFM with Thunar across the system?

Thanks

---

### Post by SteveDee on 2011-02-06
> **Jose Catre-Vandis said:**
> ...Synaptic's quick search box is greyed out...

Because Lubuntu is a light version of Ubuntu, some functionality is missing on a few applications including Synaptic.

I think the quick search box in Synaptic relies upon the Xapian search engine.

---

### Post by Jose Catre-Vandis on 2011-03-04
bump - especially regarding the function keys?

---

### Post by Jose Catre-Vandis on 2011-04-23
> **SteveDee said:**
> Because Lubuntu is a light version of Ubuntu, some functionality is missing on a few applications including Synaptic.

I think the quick search box in Synaptic relies upon the Xapian search engine.

Correct. One needs to install:
```
sudo apt-get install apt-xapian-index
```
to get the quick search box and index to work

---

