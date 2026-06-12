---
title: "Can't open folders without sudo"
date: 2012-01-09
forum: General Help
---

### Post by DJ . on 2012-01-09
I tried opening a folder without root and it gave me the white loading wheel and got stuck like that. I tried another folder; same thing. I opened a terminal and typed "sudo nautilus" and it works. What's happening and why? How can I fix it?

---

### Post by pr3zident on 2012-01-09
> **DJ . said:**
> I tried opening a folder without root and it gave me the white loading wheel and got stuck like that. I tried another folder; same thing. I opened a terminal and typed "sudo nautilus" and it works. What's happening and why? How can I fix it?

try changing the permissions of the folders 

```
 sudo chmod 777 /../../ 
```

---

### Post by DJ . on 2012-01-09
> **pr3zident said:**
> try changing the permissions of the folders 

```
 sudo chmod 777 /../../ 
```

Thanks, but no good. I tried many different folders including my home one, but it still does the same thing. I ran it in terminal and it left no logs. Also, whenever I open a folder from the desktop, I get the "opening 'foldername'" message forever.

---

### Post by DJ . on 2012-01-09
An error message while in sudo nautilus:
```
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

```Could this have something to do with it?

---

