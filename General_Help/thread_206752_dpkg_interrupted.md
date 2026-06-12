---
title: "dpkg interrupted"
date: 2006-06-30
forum: General Help
---

### Post by you3o8 on 2006-06-30
Newbie (to all things Linux); trying to divorce Bill, but struggling.  I have the latest ubuntu release on my old Dell and was trying to install "squid."  The package installer hung so I had to reboot.  When the machine came up, I tried to install again and got a message that said I had a package installer running already.  I ran Synaptic Package Manager and got the following error:

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

What do I do now?

Stranded!

---

### Post by invalid on 2006-06-30
[QUOTE=you3o8]Newbie (to all things Linux); trying to divorce Bill, but struggling.  I have the latest ubuntu release on my old Dell and was trying to install "squid."  The package installer hung so I had to reboot.  When the machine came up, I tried to install again and got a message that said I had a package installer running already.  I ran Synaptic Package Manager and got the following error:



What do I do now?

Stranded![/QUOTE]
Open a terminal and type:
```
sudo dpkg --configure -a
```

---

### Post by you3o8 on 2006-06-30
Thanks loads Invalid; it seems to have worked.

---

