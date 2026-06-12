---
title: "totaly delete  programe"
date: 2011-06-21
forum: General Help
---

### Post by cowboy7305 on 2011-06-21
Ok i had a programe on ubuntu 10.04 called licq  i have a problem with it ,and i want to totaly delete all of it from computer 
when i delete it with ubuntu software center it just deletes the program leave files behind 
i want these files deleted as well 
any help or could some one send me the codes to do this easily

---

### Post by veggen on 2011-06-21
The best thing to do is:
```
sudo updatedb
locate licq
```
and delete all resulting files **after making sure they're related to licq**.
But most probably, all you need is to delete a hidden folder in your home folder, probably named .licq or something along those lines. But you'll find it with "locate" anyway.

---

### Post by wildmanne39 on 2011-06-21
> **cowboy7305 said:**
> Ok i had a programe on ubuntu 10.04 called licq  i have a problem with it ,and i want to totaly delete all of it from computer 
when i delete it with ubuntu software center it just deletes the program leave files behind 
i want these files deleted as well 
any help or could some one send me the codes to do this easily
Hi, it is best to use synaptic, if you right click on the package you want to remove you can click to remove complete package. You might have to reinstall it now to be able to completely remove it. Also you can type this in a terminal
```
sudo apt-get --purge remove packagename
```

---

