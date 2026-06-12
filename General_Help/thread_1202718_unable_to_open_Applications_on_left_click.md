---
title: "unable to open Applications on left click"
date: 2009-07-02
forum: General Help
---

### Post by mrakesh85 on 2009-07-02
I am not getting Applications list on left click on applications. I am able to get places and system list. Can anybody tell me what is the problem

---

### Post by synapsys on 2009-07-02
Have you tried restarting your computer?

---

### Post by mrakesh85 on 2009-07-02
> **synapsys said:**
> Have you tried restarting your computer?
yes

---

### Post by synapsys on 2009-07-02
What happens when you click on 'places' and move it left to 'applications' ?

---

### Post by Legace on 2009-07-02
Type this into Terminal:

```
cp ~/.config/menus/applications.menu ~/.config/menus/applications.menu-backup
```

Then, type this:
```
rm -f ~/.config/menus/applications.menu
```

And see if it works. If it doesn't, press ALT + F2, type in **alacarte** and press Run. Make sure the entries have been selected..

---

