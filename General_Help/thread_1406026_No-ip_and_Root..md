---
title: "No-ip and Root."
date: 2010-02-13
forum: General Help
---

### Post by ex-para on 2010-02-13
Every time I try to install No-ip in Ubuntu 8.04 I come to the bit where I have to go into root and then I am finished because I have no root password. I have done other things but never used su only sudo and the usual password as instructed in most cases. I have tried other systems similar to No-ip but it is always the same, root password needed. Is there some way round this?

---

### Post by Ahadiel on 2010-02-13
If a command requires root access, just prefix it with sudo.

---

### Post by ex-para on 2010-02-14
Thank you very much for the reply but I had tried that and it did not get me what I needed. I am going to abandon this No-ip venture as it seems it is going to take more time than it is worth and I can afford.
Thanks again.

---

### Post by sisco311 on 2010-02-14
no-ip is in the repos:
```
sudo apt-get install no-ip
```
[uhelp]community/DynamicDNS[/uhelp]

---

