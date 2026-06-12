---
title: "Removing all effects"
date: 2010-04-17
forum: General Help
---

### Post by cake nom nom on 2010-04-17
hey, i just put ubuntu 9.04 32 bit on my moms computer :D 

but i want to get rid of the default minimizing effect it looks retarded but her computers to crappy to have good effects

any idea how to take away the black square outline thing that follows the window when you minimize it?

thanks in advance 

-nomnom<3cake

---

### Post by blueridgedog on 2010-04-17
System - Preferences - Appearance then the Visual Effects tab and click "none".

---

### Post by cake nom nom on 2010-04-17
> **blueridgedog said:**
> System - Preferences - Appearance then the Visual Effects tab and click "none".

this is how the default settings are.. 8-[

any other ideas?

---

### Post by steveneddy on 2010-04-17
> **cake nom nom said:**
> hey, i just put ubuntu 9.04 32 bit on my moms computer :D 

but i want to get rid of the default minimizing effect it looks retarded but her computers to crappy to have good effects

any idea how to take away the black square outline thing that follows the window when you minimize it?

thanks in advance 

-nomnom<3cake

that is the default look in Gnome without Compiz.

Try this

You can disable this by running in terminal:

```
gconf-editor
```

Then naviagate to apps >> metacity >> general
Then tick reduced_resources



Found this with a Google search. Google is your friend.

---

### Post by cake nom nom on 2010-04-23
> **steveneddy said:**
> that is the default look in Gnome without Compiz.

Try this

You can disable this by running in terminal:

```
gconf-editor
```Then naviagate to apps >> metacity >> general
Then tick reduced_resources



Found this with a Google search. Google is your friend.

NICE kudos! \\:D/

---

