---
title: "how to get samba back on my machine"
date: 2010-05-15
forum: General Help
---

### Post by titanicmusic14 on 2010-05-15
I recently upgraded from 9.04 to 9.10 and have been pulling my hair out because of it. I can't get samba 3 back on the machine. It has samba4 and it wont understand my smb.conf. All i want is samba3 back but thats not working. Synaptic package manager is no help.

---

### Post by linuxman94 on 2010-05-16
Samba 4 is still in development so to install the stable version open up a terminal and copy&paste the following:

```
sudo apt-get remove samba4 && sudo apt-get install samba
```

---

