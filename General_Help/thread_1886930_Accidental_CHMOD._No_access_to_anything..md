---
title: "Accidental CHMOD. No access to anything."
date: 2011-11-25
forum: General Help
---

### Post by Hovercat on 2011-11-25
Well, I was originally trying to recursively make /media/samba/misc/ 0777, but I accidentally typed "sudo chmod 0777 /*", which made everything writeable. So to undo it, like an idiot, I typed "sudo chmod 0644 /*", and now I have no access to anything, including sudo, and the root account is disabled.

Am I going to lose all my stuff?

---

### Post by hansdown on 2011-11-25
Hi, Hovercat.

Let's see, if we can recover your data, then work on the rest.

Running a live CD, or USB, open a terminal, and 

```
gksudo nautilus
```

You should be able to navigate to your data, and save it to a USB.

---

### Post by Hovercat on 2011-11-25
> **hansdown said:**
> Hi, Hovercat.

Let's see, if we can recover your data, then work on the rest.

Running a live CD, or USB, open a terminal, and 

```
gksudo nautilus
```

You should be able to navigate to your data, and save it to a USB.

Afterwards I'll have to reinstall, correct?

---

