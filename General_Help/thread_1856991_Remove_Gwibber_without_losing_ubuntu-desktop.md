---
title: "Remove Gwibber without losing ubuntu-desktop?"
date: 2011-10-09
forum: General Help
---

### Post by Flywaver on 2011-10-09
I know many managed to remove Gwibber via Synaptic but how do you do it without losing ubuntu-desktop? 

There is a lot of bloatware that seems linked to ubuntu-desktop, there must be a way to bypass thus dependency?

Thanks in advance!

---

### Post by Flywaver on 2011-10-09
bump

---

### Post by Cheesehead on 2011-10-09
The short answer is 'no'. The ubuntu-desktop metapackage depends on gwibber (and, as you noted, many other packages).

Removing any dependency will require removal of the depending package - that's how package management keeps your system stable.

The slightly longer answer is 'go ahead and remove ubuntu-desktop'. It's **not** your desktop - it's just a single package (with no contents) that pulls in all the elements of your desktop like Gnome and Unity. Removing the ubuntu-desktop metapackage should not remove Gnome or Unity or anything else. Nevertheless, pay close attention to any worning the system gives you.

Removing ubuntu-desktop may have a mild consequence next time you release-upgrade; any changes to the default applications are carried in ubuntu-desktop, so you won't see them. But some people consider that an advantage.

---

### Post by Flywaver on 2011-10-12
> **Cheesehead said:**
> The slightly longer answer is 'go ahead and remove ubuntu-desktop'. It's **not** your desktop - it's just a single package (with no contents) that pulls in all the elements of your desktop like Gnome and Unity. Removing the ubuntu-desktop metapackage should not remove Gnome or Unity or anything else.

I remember deleting ubuntu-desktop on an earlier release and at restart I had lost the menus...i.e. firefox could automatically start but I couldn't use it's menu.

I guess I can't wait for the next release (beta or official) of Elementary OS :)

---

