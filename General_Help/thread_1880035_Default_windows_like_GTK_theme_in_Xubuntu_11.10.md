---
title: "Default windows like GTK theme in Xubuntu 11.10"
date: 2011-11-12
forum: General Help
---

### Post by Macfunky on 2011-11-12
Just installed Xubuntu 11.10 and i'm loving it. The only problem i am having is that a few applications are defaulting to the windows 95 like GTK theme. I imagine this must be something to do with GTK3? Xfce still uses GTk2 as far as i know. For instance i open gedit and it looks like windows 95. Only a few programmes do this. Is there a workaround?

---

### Post by ankspo71 on 2011-11-13
Hi,
I think you'll need to install gtk3-engines-unico if it is not already installed, and be sure you are using a theme that supports gtk3 (Greybird is one). 

Here is a discussion about GTK3 themes and Gedit in Xubuntu 11.10. Several theme names are mentioned here that can be downloaded at gnome-look.org
[http://ubuntuforums.org/showthread.php?t=1866476](http://ubuntuforums.org/showthread.php?t=1866476)

Here is the link that says gtk3-engines-unico is needed for gtk3 in  Greybird.
[http://shimmerproject.org/project/greybird/](http://shimmerproject.org/project/greybird/)

Gtk3 themes will have a subdirectory called gtk-3.0 inside them. Here's a quick way to see if any of your installed themes support gtk3:

```
find /usr/share/themes -name gtk-3.0*
find ~/.themes -name gtk-3.0*
```

Screenshot below is Gedit using Greybird (Gtk3) in Xubuntu 11.10

---

