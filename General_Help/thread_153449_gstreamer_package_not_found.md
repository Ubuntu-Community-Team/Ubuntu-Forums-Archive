---
title: "gstreamer package not found"
date: 2006-04-01
forum: General Help
---

### Post by chettyk on 2006-04-01
Rather than use Automatix, I thought I would install the multimedia packages manually so that I have a better understanding of the whole process. I have been following "[RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")" in Ubuntu Wiki. I have got gstreamer0.8-mad installed and was thrilled to find that I could play MP3 files without a problem. 

The  "RestrictedFormats" wiki also suggests installing gstreamer0.8-plugins-multiverse (as well as gstreamer0.8-plugins and gstreamer0.8-ffmpeg). Although multiverse repositories are enabled in my sources.list, apt-get is not able to locate the first package:

```
 sudo apt-get install gstreamer0.8-plugins-multiverse
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gstreamer0.8-plugins-multiverse

```

When I looked in **[Ubuntu packages]("http://packages.ubuntu.com/")**, I find gstreamer0.8-plugins-multiverse listed as being in multiverse.

So how do I go about installing this package? Any help would be appreciated.

---

### Post by Sutekh on 2006-04-01
Are you *sure* multiverse is enabled?

Don't confuse these lines;  the breezy backports with the normal repositories.
```
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

```


 - To enable the multiverse repositories add **multiverse** to these lines in your /etc/apt/sources.list
```
deb http://archive.ubuntu.com/ubuntu breezy universe
deb-src http://archive.ubuntu.com/ubuntu breezy universe

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe
```

---

### Post by chettyk on 2006-04-01
Your diagnosis is dead right. I did get confused by multiverse being included in the two lines for breezy-backports. Thanks a zillion, Sutekh.

---

### Post by chettyk on 2006-04-01
[QUOTE=Sutekh]
 - To enable the multiverse repositories add **multiverse** to these lines in your /etc/apt/sources.list
```
deb http://archive.ubuntu.com/ubuntu breezy universe
deb-src http://archive.ubuntu.com/ubuntu breezy universe

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe
```[/QUOTE]

Yep, that solved the problem all right. Thanks so much, Sutekh -- and thank goodness for this forum.

---

### Post by Sutekh on 2006-04-01
[QUOTE=chettyk]Yep, that solved the problem all right. Thanks so much, Sutekh -- and thank goodness for this forum.[/QUOTE]Your welcome, glad its working!

---

