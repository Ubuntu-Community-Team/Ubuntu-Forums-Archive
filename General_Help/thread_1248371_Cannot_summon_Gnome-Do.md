---
title: "Cannot summon Gnome-Do"
date: 2009-08-24
forum: General Help
---

### Post by mac666 on 2009-08-24
Hey
I cannot summon Gnome-Do
I found some solutions on google but i cannot understand how to use the solutions.

Seems its a problem with Auto-hide with auto start...
How could i remove this? 
Im really new to linux... sorry!

---

### Post by exutable on 2009-08-24
Go to Applications>Accessories and press on gnome-do. This will summon it.

Now press on the arrow at the top right and press preferences, now you can change it however you choose.

---

### Post by mac666 on 2009-08-24
> **exutable said:**
> Go to Applications>Accessories and press on gnome-do. This will summon it.

Now press on the arrow at the top right and press preferences, now you can change it however you choose.
No, this does not summon it.
Its runned in background somehow and it works every now and then...

---

### Post by exutable on 2009-08-24
Well then try:

```
sudo killall gnome-do
```

and then try to summon it with the method I mentioned

---

### Post by whetherornot on 2009-09-17
I've been having problems getting it to run as well.

However, I just tried the above sudo killall gnome-do command, then restarted gnome-do and it worked. First of all, that's great, and thank you exutable. (wondering why I hadn't see the gnome-do process in top. perhaps that's an ignorant question)

Why did that work? Why isn't gnome-do working in the first place? I've got it in my startup apps, I just installed the program, just installed the jaunty actually. So I want to understand this thing. I can certainly sudo killall to make it work, but that's pretty annoying to keep doing. Any more info, exutable, or anyone?

---

