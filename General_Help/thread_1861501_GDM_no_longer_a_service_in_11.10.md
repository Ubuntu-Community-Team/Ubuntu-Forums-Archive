---
title: "GDM no longer a service in 11.10?"
date: 2011-10-15
forum: General Help
---

### Post by arsenic23 on 2011-10-15
```
sudo service gdm restart
gdm: unrecognized service
```
What?
```
sudo /etc/init.d/g [tab][tab][tab]
```
Nothing.

What is this?  I need to be able to restart gdm from the command line on the fly.

---

### Post by gsmanners on 2011-10-15
It's lightdm now. So:

```
sudo service lightdm restart
```

---

### Post by arsenic23 on 2011-10-15
Oh?  Is that the case for gnome3 as well?  I think I was under the impression that gnome3 was the new base for unity.

EDIT:  Also, thank you.

---

