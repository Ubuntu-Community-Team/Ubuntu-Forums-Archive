---
title: "Is there a way to lock virtual terminal?"
date: 2011-05-06
forum: General Help
---

### Post by l07 on 2011-05-06
Metacity can be locked, but what about a logged-in session in a virtual terminal?

---

### Post by nothingspecial on 2011-05-06
```
sudo apt-get install vlock
```


To see the options (and warnings)

```
man vlock
```

---

### Post by l07 on 2011-05-08
Thanks.

---

### Post by pathakvirendra on 2011-07-19
[B]I  have disabled direct root login ( sudo passwd -dl root) on ubuntu  server 11.04 . To lock virtual console I am using vlock. Now if I lock  entire virtual console (vlock -n ) and to unlock it i enter root  password , it say root Authentication failed !!!!!!!!!
Is dere any way to use vlock facility even after disabling direct root login??? Plz help[/B]

---

