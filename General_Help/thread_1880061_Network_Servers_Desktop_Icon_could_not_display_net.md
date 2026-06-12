---
title: "Network Servers Desktop Icon could not display network:/// unknown application"
date: 2011-11-12
forum: General Help
---

### Post by own3mall on 2011-11-12
What's supposed to open when you double click on the Network Servers shortcut?  I had a problem with Samba, and I reinstalled and removed a lot of packages.  Now my shortcut will not open.  I get the following error:

 could not display network:///
and it asked me what program to open it with?

How do I reset the shortcut and make it work properly?  It doesn't want to open.

---

### Post by own3mall on 2011-11-13
Reinstalling nautilus fixed the issue.

```


sudo apt-get remove nautilus
sudo apt-get install nautilus


```

---

