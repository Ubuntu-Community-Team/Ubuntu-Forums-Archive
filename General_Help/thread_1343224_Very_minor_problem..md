---
title: "Very minor problem."
date: 2009-12-01
forum: General Help
---

### Post by yo2boy on 2009-12-01
After updating ubuntu 9.10 in Terminal, there was some minor error that was showing:

```
Fetched 15.5kB in 0s (131.6kB/s)
Reading package lists... Done
W: Duplicate sources.list entry http://ppa.launchpad.net karmic/main Packages (/var/lib/apt/lists/ppa.launchpad.net_b-sides_ppa_ubuntu_dists_karmic_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
yo2boy@yo2boy:~$ 
```I know that this is a very minor problem, eventhough it says to update again, it shows up 1-3 hours later when I'm updating. How do I fix it in **Terminal**?

---

### Post by coffeecat on 2009-12-01
It sounds as though you have a duplicated line in sources.list, or a line in sources.list which also appears in another *list file.

Post the contents of /etc/apt/sources.list and the contents of any /etc/apt/sources.list.d/*.list files.

---

