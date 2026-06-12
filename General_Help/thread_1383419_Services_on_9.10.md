---
title: "Services on 9.10"
date: 2010-01-17
forum: General Help
---

### Post by chrispche on 2010-01-17
How do you get a text view of the services that run during start up? I installed start up manager and asked it to display the text, but this is not happening.

Any idea's?

---

### Post by Leppie on 2010-01-17
what do you mean exactly?
if you want to see what's happening during boot before getting to the login screen remove the "quiet" from the kernel parameters:
```
gksudo gedit /etc/default/grub
```edit the following line like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="splash"
```after this you will have to run update-grub:
```
sudo update-grub
```if you want to see a log of all that's happing during boot once logged in:
```
dmesg
```
or the complete log:
```
dmesg | less
```

---

### Post by chrispche on 2010-01-17
> **Leppie said:**
> what do you mean exactly?
if you want to see what's happening during boot before getting to the login screen remove the "quiet" from the kernel parameters:



That's exactly what I mean.

---

### Post by Leppie on 2010-01-17
> **chrispche said:**
> That's exactly what I mean.
glad to have provided the information you wanted :)

---

### Post by chrispche on 2010-01-18
Thank you, that worked nicely.

---

