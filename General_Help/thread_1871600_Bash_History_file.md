---
title: "Bash History file"
date: 2011-10-29
forum: General Help
---

### Post by spiky001 on 2011-10-29
Ok a quick Question the file .bash_history in a user,s home can I delete the file? If so will a new 1 get created when they use terminal? Basically I need to clear all the history for a user  and start with a clean history.

---

### Post by haqking on 2011-10-29
> **spiky001 said:**
> Ok a quick Question the file .bash_history in a user,s home can I delete the file? If so will a new 1 get created when they use terminal? Basically I need to clear all the history for a user  and start with a clean history.

```
history -c
```

or

```
rm ~/.bash_history
```

and it will recreate itself

---

### Post by spiky001 on 2011-10-29
Thks haqking just wanted to make sure it was recreated

---

