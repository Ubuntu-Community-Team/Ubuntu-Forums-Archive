---
title: "Ubuntu/Kubuntu"
date: 2010-01-18
forum: General Help
---

### Post by Synoc on 2010-01-18
what are the differences? I'm running a 5 year old Dell 1150 inspiron witha Wireless card that's about useless right now (referance [http://ubuntuforums.org/showthread.php?t=1356712](http://ubuntuforums.org/showthread.php?t=1356712) )

Kubnutu has a KDE interface vs a gnome, form what I understand, but anything else?

---

### Post by Ahriman on 2010-01-18
That's pretty much the only difference. Some programs will be different from KDE to Gnome (due to different design/programming/etc) but functionally they are the same.

---

### Post by Zorael on 2010-01-18
There are some concrete examples (with pictures, albeit old ones) over at [this page](http://www.psychocats.net/ubuntu/kdegnome).

---

### Post by Synoc on 2010-01-18
ok so can I install Kubuntu OVER ubuntu? or clean install only?

---

### Post by Zorael on 2010-01-18
The nomenclature is a bit confusing.

Ubuntu is both "Ubuntu with the GNOME interface", as well as it is "the core repository packages used in all *buntu flavors". Kubuntu would be "Ubuntu (packages) with the KDE interface", or "KDE from the Ubuntu core repositories", or something along those lines.

So, Kubuntu is like a set of packages that make up a subset of Ubuntu core, much like "GNOME-Ubuntu" is. As they are both independent sets of packages, you can have both GNOME-Ubuntu and Kubuntu installed at the same time, as well as Xubuntu, Fluxbuntu, Edubuntu, etc.

There are a few exceptions. Only one splash can be shown when the system boots and shuts down, so unless you make your own it will have to say either Kubuntu or Ubuntu (or Debian or whatever other themes are available from the repos). Likewise, only one login manager can be used as default; Kubuntu uses kdm, while GNOME and Xfce uses gdm.

And lastly, each distro will impose its own defaults onto your user, so if you run a very mixed setup you may find some GNOME apps being started when you double-click stuff in KDE. You can still probably work around it, but the default behavior will be a bit off.

To connect to your question, you only have to remove the GNOME-Ubuntu bits and install the Kubuntu bits, and presto; you have Kubuntu. That said, the line saying when your setup stops being merely "Ubuntu" and starts being Kubuntu is fuzzy at best. If you only install the basic KDE packages and don't install the kubuntu-desktop bundle, is it really Kubuntu? Etc.

---

### Post by Synoc on 2010-01-18
so how do I get kubuntu packages so I can do that?

---

### Post by Zorael on 2010-01-18
Install the **kubuntu-desktop** package. That should get you the whole environment.

---

### Post by Synoc on 2010-01-18
ok so I'm loading the KDM now, if I decide I like gdm better how do I switch back to that as my default?

---

### Post by Zorael on 2010-01-18
Enter this in a terminal and pick gdm.
```
$ sudo dpkg-reconfigure gdm
```

---

