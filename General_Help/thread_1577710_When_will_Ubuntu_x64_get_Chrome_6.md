---
title: "When will Ubuntu x64 get Chrome 6?"
date: 2010-09-19
forum: General Help
---

### Post by josephellengar on 2010-09-19
Huh.  I've been able to upgrade to Chrome 6 on my W7 machine and on my Ubuntu 32-bit netbook, but I haven't gotten it on my Ubuntu x64 machine.[/quote]

---

### Post by howefield on 2010-09-19
> **rossholley said:**
> Huh.  I've been able to upgrade to Chrome 6 on my W7 machine and on my Ubuntu 32-bit netbook, but I haven't gotten it on my Ubuntu x64 machine.

Unless I'm mistaken, you can get it.

Version 6.0.472.62

---

### Post by josephellengar on 2010-09-19
> **howefield said:**
> Unless I'm mistaken, you can get it.

Version 6.0.472.62

I just ran update-manager.  Package information is 18 hours old.  System is up to date.  Chrome version 5.0.375.70.  Am I missing something?

---

### Post by howefield on 2010-09-19
Have you disabled the google repository ?

To be fair, after getting speed issues with the google repository I download the package from google fairly frequently, and then disable the repository it automatically adds to the sources.list. 

Either way, I'm just letting you know version 6 is available.

---

### Post by luceerose on 2010-09-19
Add the following lines to /etc/apt/sources.list
```
deb http://dl.google.com/linux/deb/ stable non-free main 
deb http://dl.google.com/linux/deb/ testing non-free main
```

Then install the 'google-chrome-beta' package either through Synaptic or sudo apt-get.
It's version 6.0.472.62

---

### Post by josephellengar on 2010-09-19
> **howefield said:**
> Have you disabled the google repository ?

To be fair, after getting speed issues with the google repository I download the package from google fairly frequently, and then disable the repository it automatically adds to the sources.list. 

Either way, I'm just letting you know version 6 is available.

Good catch!  Thanks!

---

