---
title: "Gnome3 desktop font size"
date: 2011-10-23
forum: General Help
---

### Post by Driftu on 2011-10-23
Hello, maybe someone know how to change Gnome3 desktop font size?

Many thanks.

---

### Post by ShodanjoDM on 2011-10-23
> **Driftu said:**
> Hello, maybe someone know how to change Gnome3 desktop font size?

Many thanks.

Install dconf-tools if it hasn't already installed

```
sudo apt-get install dconf-tools
```

then launch dconf-editor

```
dconf-editor
```

navigate to org>gnome>nautilus>desktop where you'll see desktop font section.

Hope that helps.

---

### Post by lymphor on 2012-11-21
It helped me! Many thanks! ):P

---

### Post by sgage on 2012-11-21
You can also use gnome-tweak-tool to goose up the scaling factor. I like 1.2.

---

### Post by jim_deadlock on 2012-11-21
You can install gnome-tweak-tool for this, it's a more user-friendly GUI than dconf.

---

