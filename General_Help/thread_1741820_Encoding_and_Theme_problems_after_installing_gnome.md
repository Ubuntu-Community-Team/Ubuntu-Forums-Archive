---
title: "Encoding and Theme problems after installing gnome3"
date: 2011-04-28
forum: General Help
---

### Post by elwin murton on 2011-04-28
Hi,

I just installed Ubuntu 11.04 Desktop amd64 and installed Gnome3 the following way:

```

sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install gnome-shell

```

After restart, I found the followint problems:

- Language support to spanish (I cant change Gnome3 to spanish)
- "acute" characters problems (maybe is the same problem)
- Really ugly buttons and theme layout (I would like to have gnome3 with a ubuntu-like theme)

I attach a screenshot that shows better what's happening. 

[[IMG]http://img198.imageshack.us/img198/324/screenshotvm.png[/IMG]](http://img198.imageshack.us/i/screenshotvm.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

Any ideas?

Thanks!

---

### Post by camelinahat on 2011-04-28
Ran into this myself. After doing some digging around I found this site:
[http://ubunturocking.wordpress.com/2011/04/13/gnome3-on-ubuntu-using-the-ppa/](http://ubunturocking.wordpress.com/2011/04/13/gnome3-on-ubuntu-using-the-ppa/)

What fixed it for me was running:
sudo apt-get remove gnome-accessibility-themes
sudo apt-get install gnome-themes-standard

The other packages recommended in the article were already instead, but for some reason needed to remove gnome-accessibility-themes before installing gnome-themes-standard

---

### Post by elwin murton on 2011-04-29
Hey! That worked. Thank you a lot!!!

---

