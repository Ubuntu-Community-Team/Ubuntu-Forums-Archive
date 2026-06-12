---
title: "compiz will not load at startup"
date: 2009-12-13
forum: General Help
---

### Post by PatrickMoore on 2009-12-13
when i log onto my computer compiz is not loading at all. this is the first time ive had this issue ive been using ubuntu since 8.04 ultimately i had to restart compiz to get it to work and as a result i have to restart compiz. does anyone know why this is happening and how to resolve it?

---

### Post by lewisforlife on 2009-12-13
If you are using Gnome, have you added:

```
compiz --replace
```

to System-->Preferences-->Startup Programs.

---

### Post by PatrickMoore on 2009-12-13
worked like a charm thank you

---

### Post by lewisforlife on 2009-12-13
No problem, if you decide to install emerald, you will have to do the same thing, but, emerald --replace.

---

### Post by wtflolol on 2009-12-14
> **lewisforlife said:**
> If you are using Gnome, have you added:

```
compiz --replace
```to System-->Preferences-->Startup Programs.

Do **NOT** do this! If you do that, your GDM will first start metacity, then start nautilus (desktop) and gnome-sesssion-manager, which in turn will start compiz. So you’re starting one window manager only to replace it with another shortly afterwards. You can see this clearly because it takes a while for compiz to start up and load your window decorator (like emerald) after replacing metacity.

 The proper way to do this is to tell Gnome to use compiz as your default window manager and not use metacity at all. Simply put this in your ~/.gnomerc (create that file if it does not exist yet):


```
export WINDOW_MANAGER=/usr/bin/compiz
```

---

### Post by lewisforlife on 2009-12-14
I am fairly new to this, so I thought this was the correct way.

> The proper way to do this is to tell Gnome to use compiz as your default window manager and not use metacity at all. Simply put this in your ~/.gnomerc (create that file if it does not exist yet):


Compiz is a window manager?

---

