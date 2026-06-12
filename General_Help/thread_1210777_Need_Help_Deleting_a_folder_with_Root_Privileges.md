---
title: "Need Help Deleting a folder with Root Privileges"
date: 2009-07-11
forum: General Help
---

### Post by Evildemon989 on 2009-07-11
So, I have a folder on my desktop that has root privileges, and I want to get rid of it. How can I do this in terminal?

---

### Post by howefield on 2009-07-11
> **Evildemon989 said:**
> So, I have a folder on my desktop that has root privileges, and I want to get rid of it. How can I do this in terminal?

type in the terminal

```
gksu nautilus
```

After entering your password, the file manager window will open and you should then be able to navigate to the folder and delete.

Or use the command in terminal

```
sudo rm -r folder
```

---

### Post by philcamlin on 2009-07-11
gksu nautilus

delete it from there

---

### Post by Evildemon989 on 2009-07-12
Thanks!

---

