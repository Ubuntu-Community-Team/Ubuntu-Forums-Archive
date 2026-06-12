---
title: "Been thinking about switching from Gnome to Xcfe4 - help?"
date: 2012-05-14
forum: General Help
---

### Post by AlexOnVinyl on 2012-05-14
I've been thinking about switching from Gnome to Xcfe4 - the only thing stopping me is:

1) The space having all three Unity, Gnome and Xcfe4 on my system would take up.

2) How would I get rid of Gnome without compromising my whole system's configuration? 

3) Could I keep some of the Gnome packages without having to redownload them?

---

### Post by scoon on 2012-05-14
> **AlexOnVinyl said:**
> I've been thinking about switching from Gnome to Xcfe4 - the only thing stopping me is:

1) The space having all three Unity, Gnome and Xcfe4 on my system would take up.

2) How would I get rid of Gnome without compromising my whole system's configuration? 

3) Could I keep some of the Gnome packages without having to redownload them?


Hey there, 

1. apt-get install xubuntu-desktop says once it is installed it will take an additional 316mb.  

2. Here are a couple of suggestions: [**how-to-remove-the-ubuntu-gnome-desktop-after-making-the-switch-to-kde**]("http://superuser.com/questions/28781/how-to-remove-the-ubuntu-gnome-desktop-after-making-the-switch-to-kde") and [**how-to-remove-and-reinstall-gnome-3**]("http://askubuntu.com/questions/67764/how-to-remove-and-reinstall-gnome-3")

3. Depends on what you remove.

Skip

---

### Post by Myrddin Emrys on 2012-05-14
> **scoon said:**
> 1. apt-get install xubuntu-desktop says once it is installed it will take an additional 316mb.

Alternatively, the **xfce4** package is a lot smaller than **xubuntu-desktop** but still gives you a complete Xfce environment - **xubuntu-desktop** includes a bunch of non-xfce applications like (e.g.) Abiword and Gnumeric, which you may not need if you already have Libreoffice etc.

---

### Post by AlexOnVinyl on 2012-05-14
> **scoon said:**
> Hey there, 

1. apt-get install xubuntu-desktop says once it is installed it will take an additional 316mb.  

2. Here are a couple of suggestions: [**how-to-remove-the-ubuntu-gnome-desktop-after-making-the-switch-to-kde**]("http://superuser.com/questions/28781/how-to-remove-the-ubuntu-gnome-desktop-after-making-the-switch-to-kde") and [**how-to-remove-and-reinstall-gnome-3**]("http://askubuntu.com/questions/67764/how-to-remove-and-reinstall-gnome-3")

3. Depends on what you remove.

Skip

Xubuntu is compatible with all the same stuff Ubuntu is right?

Also, I think Im going to do a clean install of Ubuntu then start from there.

I wish there was an easier way to remove Gnome without borking my whole system.

> **Myrddin Emrys said:**
> Alternatively, the **xfce4** package is a lot smaller than **xubuntu-desktop** but still gives you a complete Xfce environment - **xubuntu-desktop** includes a bunch of non-xfce applications like (e.g.) Abiword and Gnumeric, which you may not need if you already have Libreoffice etc.

Thats what I did, but Im still a little nervous because I want to get rid of gnome.

Here's what I did to get rid of gnome - but this might've broke my system -

```
sudo apt-get autoremove gnome-*
```

any other suggestions?

---

### Post by forrestcupp on 2012-05-14
> **AlexOnVinyl said:**
> 
3) Could I keep some of the Gnome packages without having to redownload them?If you want to keep Gnome packages, then you have to keep Gnome for running them. Even if you do a straight Xubuntu installation, and try to install even one GTK/Gnome based app, it will pull the Gnome libs back into your system. Yes, Xubuntu is compatible with Gnome apps, but you have to have the Gnome libs installed to run them.

> **AlexOnVinyl said:**
> 
Also, I think Im going to do a clean install of Ubuntu then start from there.
If you do really want to try to do a pure Ubuntu Xfce system, you need to install Xubuntu instead of Ubuntu, and you need to make sure to never install any packages that depend on Gnome or Kde.

---

### Post by mike555 on 2012-05-14
After you install Xubuntu go into synaptic and uncheck "recommends", that way you can install good things like gedit, etc. without gnome .
   note- better not install nautilus , it messed up my xubuntu.

use synaptric to install ,not software center, because software center doesn't tell you all it's installing.

---

