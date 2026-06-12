---
title: "Me Menu And Pidgin"
date: 2010-07-26
forum: General Help
---

### Post by temporos on 2010-07-26
I uninstalled Empathy and installed Pidgin, because I just couldn't take Empathy's lack of features any more.  The "Me" menu doesn't work properly with Pidgin, though.  Every time I change my status via the Me menu, it knocks me off-line on three of my four accounts.

Does anyone know how to disable (or even remove) the "Me" menu?  It's only functionality is to control messaging and social networking services, right?

---

### Post by AceRoom on 2010-07-26
Just right click and ```
Remove From Panel
``` should work.

---

### Post by temporos on 2010-07-26
> **AceRoom said:**
> Just right click and ```
Remove From Panel
``` should work.
No.  I'm using the Netbook Edition of Lucid.  The Ubuntu gods (in all their eternal wisdom) disabled that option on the system panels.

---

### Post by AceRoom on 2010-07-30
Well... I haven't used the Netbook Edition. What if you try to uninstall the MeMenu?

---

### Post by temporos on 2010-07-30
> **AceRoom said:**
> Well... I haven't used the Netbook Edition. What if you try to uninstall the MeMenu?

That's what I'm asking.  Do you know what packages make up the Me Menu?  LOL  It's difficult to uninstall when I can't find which packages to modify.

---

### Post by amsterdamharu on 2010-07-30
I googled for
```
site:packages.ubuntu.com me menu social networking
```

Found the following:

[http://packages.ubuntu.com/en/lucid/indicator-me](http://packages.ubuntu.com/en/lucid/indicator-me)

This might be the package you are looking to remove.

Package name: indicator-me

---

### Post by miesogeno on 2010-10-21
for anyone else with the same problem of status error:

- just install empathy again
- remove all acounts created before (this error happens because you created an acount in empathy, even if you removed empathy afterwards, the settings remain there)
- after removing every acount created before, you shouldn't have more trouble, but if you want to, you can remove empathy again.

status in pidgin and me-menu should be fine now.

---

