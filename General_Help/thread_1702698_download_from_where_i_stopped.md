---
title: "download from where i stopped"
date: 2011-03-08
forum: General Help
---

### Post by vivek.pandey on 2011-03-08
hi everyone
   just wondering if this is possible
yesterday i was downloading a .tar file using wget command from my terminal..the file was about 50mb . i had downloaded around 25mb when suddenly i had some network problem and i stopped downloading. so is it possible to start that download from the point i stopped i mean after 25mb

thanx to all

---

### Post by Grenage on 2011-03-08
```
wget -c *filepath*
```

You'd need to execute the command from whatever folder has the partial data.

---

### Post by 3rdalbum on 2011-03-08
> **Grenage said:**
> ```
wget -c *filepath*
```

You'd need to execute the command from whatever folder has the partial data.

+1. And if the server doesn't support continuing... then sorry, you're out of luck.

---

### Post by vivek.pandey on 2011-03-08
> **Grenage said:**
> ```
wget -c *filepath*
```

You'd need to execute the command from whatever folder has the partial data.

thanx for your reply
i get this

vivek@NEO:~$ wget -c /home/vivek/Downloads/wget-1.10.1.tar.gz
/home/vivek/Downloads/wget-1.10.1.tar.gz: Scheme missing.

---

### Post by Grenage on 2011-03-08
Sorry, you'd need to specify the file path of the file you wish to copy.  For example [http://files.com/myfile.deb](http://files.com/myfile.deb)

---

### Post by vivek.pandey on 2011-03-08
thanx for your help
its working

---

### Post by vivek.pandey on 2011-03-08
will it be applicable even if download files from some other method then wget?

---

### Post by Grenage on 2011-03-08
> **neo_aryan said:**
> will it be applicable even if download files from some other method then wget?

Syntax will obviously change, and other methods/utilities may not support resuming of downloads.  That's a very situation-specific question.

---

