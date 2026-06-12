---
title: "Help, please - Wifes APT is hosed"
date: 2011-01-16
forum: General Help
---

### Post by mfaust731 on 2011-01-16
I was trying to install lives on my wifes laptop (10.10) and added a PPA - apparently with bad links.
Now apt throws up an error when it trys to start.

> Could not initialize the package information.
an unresolvable problem occurred while initializing the package information.
'E:TYPE 'n' is not known on line 2 in source list in /etc/apt/sources.d/hrickards-lives-lucid.list, E: the list of sources could not be read' 

I have dissabled the offending source and verified it was commented out in /etc/apt/sources.list  
rebooted and it still gives me the error.

I need help, what else do I need to do?

Thanks

---

### Post by plucky on 2011-01-16
> **mfaust731 said:**
> I was trying to install lives on my wifes laptop (10.10) and added a PPA - apparently with bad links.
Now apt throws up an error when it trys to start.



I have dissabled the offending source and verified it was commented out in /etc/apt/sources.list  
rebooted and it still gives me the error.

I need help, what else do I need to do?

Thanks

Remove the actual list with ```
sudo rm /etc/apt/sources.d/hrickards-lives-lucid.list
```

Then run ```
sudo apt-get update
```

Good Luck

---

### Post by mfaust731 on 2011-01-16
Thanks Mate

---

