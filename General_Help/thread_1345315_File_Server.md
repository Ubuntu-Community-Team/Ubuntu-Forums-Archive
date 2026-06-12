---
title: "File Server"
date: 2009-12-03
forum: General Help
---

### Post by rules on 2009-12-03
Hi all

I have a machine standing here at home doing nothing and I was wondering if I could turn it into a multi platform file server (as in have mac, win and linux machines backup/copy data to it).

Any ideas ... free ideas that is :D

Cheers.

---

### Post by jbrown96 on 2009-12-03
You can install the server edition of Ubuntu on it, but you might want to use the desktop version if you are new to ubuntu. The server edition does not include a graphical mode (just a terminal), which new users may find daunting. 

Once you get that setup, you should install (and read about) ssh. Documentation [here]("https://help.ubuntu.com/community/SSH")

For a file server, sharing files on the local network, samba is the best solution. It works with ubuntu, mac, and windows. Documentation [here]("https://help.ubuntu.com/community/SettingUpSamba")

---

