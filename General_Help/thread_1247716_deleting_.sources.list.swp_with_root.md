---
title: "deleting .sources.list.swp with root"
date: 2009-08-23
forum: General Help
---

### Post by Lenny212 on 2009-08-23
Hi,
I need to delete the file etc/apt/.sources.list.swp
I need to be root - I believe

How do I get root permissions and then delete this file?

Thanks

---

### Post by yeeeev on 2009-08-23
Before you do that, make sure your original sources.list file is OK.
You can delete it using:
sudo rm /etc/apt/sources.list.swp

---

### Post by Lenny212 on 2009-08-25
Thanks yeev,
So simple I can't believe I didn't try that.
I need to do some more reading to get my head around terminal a bit more.
Thanks for your help.

---

### Post by P4man on 2009-08-25
If you want to accomplish the same without terminal, you can install "nautilus-gksu". That lets you open a folder as root in the nautilus file manager, by right clicking a file or folder and then > open as adminstrator.

To install that package, do:

```
sudo apt-get install nautilus-gksu
```

(or if you're really allergic to terminals, look it up in synaptic package manager and install it from there :p )

---

### Post by Lenny212 on 2009-08-28
Thanks - I will give it a go

---

