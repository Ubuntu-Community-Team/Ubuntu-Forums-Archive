---
title: "delete file"
date: 2010-01-18
forum: General Help
---

### Post by bayarja on 2010-01-18
hi experts. i can't delete file. it's in /var/lib/...
error - > permission denied. what should i do? sorry my english.

---

### Post by ST3ALTHPSYCH0 on 2010-01-18
```

sudo rm /var/lib/filename

```

---

### Post by bayarja on 2010-01-18
sorry. i forget, it's not file. it's director. 
sudo rmdir /var/lib/filename .i use this code but not work

---

### Post by argosreality on 2010-01-18
rmdir will not remove a directory if there are files within it. To remove the directory with files you need to do```
$ sudo rm -rf DIR (where DIR is the directory)
```and unless you know everything thats in that directory I'd really recommend adding an -i to the switchs so that it ASKS you to ok what your deleting.

---

### Post by bayarja on 2010-01-18
thanks argosreality.

it's ok. but other director with lock image. is it ok?

---

### Post by rnerwein on 2010-01-19
sorry
have you already reinstalled your system ???
ciao

---

### Post by prasys on 2010-01-19
```
sudo rm -rf DIR
```

-r here stands for folder
-f stands for force

Be sure to know what you're doing with the command. It can be dangerous , do double check the DIR that you wanna remove

---

### Post by jamesisin on 2010-01-19
Um, why are you deleting things in /var/lib?

---

### Post by ad_267 on 2010-01-19
> **jamesisin said:**
> Um, why are you deleting things in /var/lib?

+1, I would have asked that first too.

---

### Post by argosreality on 2010-01-19
> **ad_267 said:**
> +1, I would have asked that first too.Yes, should have been asked first but well...I cant completely hide the childish portion of myself kinda wondering what would happen...

---

