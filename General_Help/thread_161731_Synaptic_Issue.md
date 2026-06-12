---
title: "Synaptic Issue"
date: 2006-04-17
forum: General Help
---

### Post by OffHand on 2006-04-17
Hi all
I tried to make a encrypted folder using this guide: 

[http://ubuntuforums.org/showthread.php?t=148600](http://ubuntuforums.org/showthread.php?t=148600)

Icouldn't get it to work so I did ```
sudo apt-get remove encfs fuse-utils
```
and I deleted the directories I made.

Then did ```
sudo gedit /etc/modules
``` and removed 'fuse' again.

Rebooted.

Now I wanted to install Seahorse from the Synaptic but I get the following error.  

dpkg: syntax error: unknown group 'fuse' in statusoverride file

Anyone who know I can fix this?

---

### Post by OffHand on 2006-04-17
I have eddited the statoverride file with ```
sudo gedit /var/lib/dpkg/statoverride
``` and removed the line referring to fuse.
Problem fixed!

---

