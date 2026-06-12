---
title: "Errors Help"
date: 2011-04-08
forum: General Help
---

### Post by Tomau000 on 2011-04-08
When trying sudo apt-get install <package name> I get this:

Errors were encountered while processing:
gconf2
mutter-common
libmutter-private0
mutter
gnome-shell
E: Sub-process /usr/bin/dpkg returned an error code (1)

Anyone have a fix?

---

### Post by spikoley on 2011-04-09
Try this command.

```
sudo apt-get -f install
```

---

### Post by jerenept on 2011-04-09
> **Tomau000 said:**
> When trying sudo apt-get install <package name> I get this:

Errors were encountered while processing:
gconf2
mutter-common
libmutter-private0
mutter
gnome-shell
E: Sub-process /usr/bin/dpkg returned an error code (1)

Anyone have a fix?

Unity causes dependency problems with Gnome-Shell, if thins is the problem you are trying to solve here.

I don't think spikoley's suggestion will help, it's more a matter of, Unity or GS.

---

