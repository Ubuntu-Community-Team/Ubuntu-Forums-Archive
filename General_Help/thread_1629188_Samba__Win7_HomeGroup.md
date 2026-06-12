---
title: "Samba / Win7 HomeGroup"
date: 2010-11-23
forum: General Help
---

### Post by fofo412 on 2010-11-23
I installed xUbuntu for the first time in YEARS, and am trying to get my home network setup.  I know this is possible, because it is enabled with gnome/Ubuntu by default -- I just can't seem to get it configured properly with XFCE and synaptic.

I'd like to be able to grab music and some other files off of my desktop library from my laptop running xUbuntu.

I've installed samba and a samba client.  Does anyone know what I am supposed to do from here?  I can't find a guide online or on the forum that 1) works , 2) is recent.

Like I said, I know Ubuntu has this enabled by default.

---

### Post by cariboo on 2010-11-23
You need to configure Samba. This is done by editing /etc/samba/smb.conf.

Have a look at [this]("http://ubuntuforums.org/showthread.php?t=202605") howto

---

### Post by Morbius1 on 2010-11-23
A little confused here ( my normal state recently ). Are you trying to access a remote share from XFCE?

Unlike Nautilus in Gnome Thunar doesn't have a built in network browser. I would suggest Gigolo for this: [http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

If you're talking about the ability to right click a folder in Nautilus in Gnome and share a folder then Thunar can do that also but you need to install the following package:
```
thunar-shares-plugin
```

---

### Post by fofo412 on 2010-11-23
> **Morbius1 said:**
> A little confused here ( my normal state recently ). Are you trying to access a remote share from XFCE?

Unlike Nautilus in Gnome Thunar doesn't have a built in network browser. I would suggest Gigolo for this: [http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

If you're talking about the ability to right click a folder in Nautilus in Gnome and share a folder then Thunar can do that also but you need to install the following package:
```
thunar-shares-plugin
```

Nope, I have xUbuntu on my laptop.  I'd like to be able to create a home network or something with my Win7 machine, and get the shared files on my laptop using xUbuntu.  Not really sure how to do it. . .

---

