---
title: "Tool to see how much harddisk space is left!"
date: 2006-05-04
forum: General Help
---

### Post by Tubbie on 2006-05-04
I know that you can see by Disks Manager (System > Administration > Disks) how much space is used and is left on a partition. But isn't there a easy tool that can fit in Gnome panel or something to see how much space is left on each drive. I know I had something like this for KDE, Kmount or something, but isn't there something specifc for Gnome?

Thnx already :)

---

### Post by mjm115 on 2006-05-04
install *gnome-applets*.  It contains a bunch of applets, and the one you're searching for is actually in there as the system monitor.

---

### Post by zugu on 2006-05-04
As far as I know, there is a gDesklets desklet (sic) that once activated can show you how much disk space is used and left on whatever partition you want.
```
apt-get install gdesklets
```
should get you going, but alternatively you can go to [http://gdesklets.gnomedesktop.org/](http://gdesklets.gnomedesktop.org/) , the home of the gDesklets project. There you can find a lot more gDesklets for download, presumably some that show used and left disk space.

Hope this info will help you, good luck.

---

### Post by Al3xanR0 on 2006-05-04
[QUOTE=Tubbie]I know that you can see by Disks Manager (System > Administration > Disks) how much space is used and is left on a partition. But isn't there a easy tool that can fit in Gnome panel or something to see how much space is left on each drive. I know I had something like this for KDE, Kmount or something, but isn't there something specifc for Gnome?

Thnx already :)[/QUOTE]

KDE uses Kdiskfree to accomplish this, Kdiskfree will work in Gnome just ```
apt-get install kdf
```

---

### Post by Onyros on 2006-05-04
Hi there, new forum dweller here, relatively new to Ubuntu (first installed it a couple of months ago).

Even in GNOME, I use torsmo ;) I first got to know about torsmo when I was customizing a Fluxbox DE of my own, and then started using it with GNOME as well.

Here's a screenie for you (torsmo's running on the top right corner):
[[IMG]http://img305.imageshack.us/img305/9595/screenie7kw.th.jpg[/IMG]](http://img305.imageshack.us/my.php?image=screenie7kw.jpg)

It's a really lightweight app as well, and it's quite costumizable. Other than that, you can check out conky as well, which has a few more features. For me, torsmo's more than adequate ;)

Have fun :)

---

