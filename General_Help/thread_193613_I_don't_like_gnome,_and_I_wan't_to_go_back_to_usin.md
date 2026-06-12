---
title: "I don't like gnome, and I wan't to go back to using KDE. (minimal)"
date: 2006-06-10
forum: General Help
---

### Post by Steveire on 2006-06-10
I used a ubuntu CD to install dapper, which means that I'm currently using Gnome. I've been using Kubuntu for breezy and Dapper testing, and I've grown used to KDE, so I want to remove my Gnome DE and install a skin and bones KDE. (I don't want to have heaps of packages I'll never use)

My POA is to aptitude install KDE (not kubuntu desktop) following instructions [here](https://wiki.ubuntu.com/InstallingKDE), and then follow instructions [here](http://www.psychocats.net/ubuntu/purekde) to remove Gnome. 

I'm not really sure about whether to install KDE or KDE-core. Most of the applications installed in KDE-core look quite essential.

After doing this, is there anything else for me to do to make mine a Kubuntu installation? I'm going to install KDM and if I can figure it out, I'll change the boot splash too.

---

### Post by Steveire on 2006-06-11
I ended up having to install kubuntu-desktop. It's fine though I suppose.

---

### Post by aysiu on 2006-06-11
You can always remove whatever extraneous packages you see. Like, if you don't use Kopete... ```
sudo aptitude remove kopete
```

---

