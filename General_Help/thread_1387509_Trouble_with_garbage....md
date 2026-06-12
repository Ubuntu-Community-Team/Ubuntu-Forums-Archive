---
title: "Trouble with garbage..."
date: 2010-01-21
forum: General Help
---

### Post by Shadowninja on 2010-01-21
So i have stuff in my garbage that i can neither delete completely nor restore... its just stuck there... how the &#@% do I get rid of these stupid folders!?!?!??!?!?!?!!

---

### Post by wojox on 2010-01-22
Try running in the terminal:

```
rm -rf /home/*/.local/share/Trash/** &> /dev/null
```

---

### Post by Jive Turkey on 2010-01-22
When running the command that wojox suggested be carefull there is no space between the "*" and the next"/" or it will delete everything in your home directory.  Safer to replace "*" with your actual username.

---

### Post by jms1989 on 2010-01-22
Try this: sudo rm -rf ~/.local/share/Trash/files/*

---

