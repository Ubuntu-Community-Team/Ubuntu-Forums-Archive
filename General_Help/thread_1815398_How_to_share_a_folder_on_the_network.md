---
title: "How to share a folder on the network"
date: 2011-07-31
forum: General Help
---

### Post by garethfoxwilliams on 2011-07-31
I'm probably missing something really simple here...

In Ubuntu, with Nautilus, there is an easy GUI method of making folder to be shared and visible over the network. 

I can't seem to find the means of doing this in Xubuntu, either in Thunar or Gigolo.

I can use either of these to browse folders on other networked machines I have shared using Nautilus. 

I had Nautilus for a while on my XFCE machine and used that to share some folders, but I removed it as it was conflicting with Thunar at times.

---

### Post by Morbius1 on 2011-07-31
Once upon a time there was a package called - thunar-shares-plugin. This package did for thunar what nautilus-shares did for Nautilus. The package has vanished and I can't find out why.

What I do is install nautilus-share which brings in Nautilus and do it from there. I haven't had any problems with nautilus conflicting with thunar as you have had however.

---

### Post by garethfoxwilliams on 2011-07-31
I might have to try that, but I believe I was having a conflict on start-up. I was ending up with a blank / empty desktop. It may have been related to the Dropbox plug-in which likes Nautilus. However the Dropbox applet still seems to work with no Nautilus on the machine!

I'm hoping for some advice on a terminal-based solution a bit like chmod / chown.

---

### Post by Morbius1 on 2011-07-31
Both thunar-shares-plugin and nautilus-shares are file manager plugins for something Samba calls Usershare.

You can always use the traditional Classic Samba share using the following package:
```
system-config-samba
```

---

### Post by garethfoxwilliams on 2011-07-31
OK, thanks.

I had to install system-config-samba via the terminal and then run it as root, at least from the terminal, but that has certainly made my "Videos" directory visible on the network.

It seems I can also run it as user from the main application menu too.

My machine remains Nautilus free!!

Thanks for the help

---

