---
title: "Trying to update sources.list"
date: 2012-07-16
forum: General Help
---

### Post by Mazate on 2012-07-16
Howdy...  I'm trying to install the linux Spotify app which requires me adding a few lines to my sources.list file.  When I go into it using gedit, I make the changes but gedit doesn't allow me to save the changes.  Anyone that can tell me what I'm doing wrong would be doing me a huge favor.   Thanks!

---

### Post by Cheesemill on 2012-07-16
You need to edit it with root permissions. Open a terminal and type:
```
kdesudo gedit /etc/apt/sources.list
```

---

### Post by Mazate on 2012-07-16
> **Cheesemill said:**
> You need to edit it with root permissions. Open a terminal and type:
```
kdesudo gedit /etc/apt/sources.list
```

Worked perfectly, thank you.

---

