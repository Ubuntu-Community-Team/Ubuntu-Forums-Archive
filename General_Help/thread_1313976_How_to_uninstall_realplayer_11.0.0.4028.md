---
title: "How to uninstall realplayer 11.0.0.4028"
date: 2009-11-04
forum: General Help
---

### Post by Richiegs on 2009-11-04
I sucessfully installed Realplayer, but there is no sound from the radio on the internet. I tried to uninstall Realplayer by **Add/Remove** from Application and **Synaptic Package Manager**. It didn't list Realplayer. Can anyone please tell me how to uninstall Realplayer? Thank you 

Richie

---

### Post by liquidbee on 2009-11-04
How did you installed it ?

---

### Post by hal10000 on 2009-11-04
you can only remove software with **Add/Remove** if you installed it as a debian package (those packages with a .deb suffix) but i guess you installed it as a tar.gz or zip package from somewhere in the internet. If you're lucky, you may find some uninstallation info in the zipped file or at the place where you downloaded it. If you can't find this info, then you have to find out where it was installed to.

Common places may be the /opt or the /usr/local directories. If you can find a directory called realplayer (or similar) in one of these directories then you can remove it:
```
sudo rm -r /opt/realplayer
```
or
```
sudo rm -r /usr/local/realplayer
```

If you can't find it in one of these places, then you might be in trouble to get completely rid of it.
You could search in /usr/lib and in /usr/share for filrs and directories related to realplayer and remove them, but it may be a lot of work.


**A hint for future installations: **If you want to install a software, always try to find it with your package manager (use synaptic, it's better then the Add/remove feature) There are about 28000 packages provided in your repositories and in the very very most cases you will find here what you want.

To install realplayer 11 with synaptic (or Add/Remove), you first have to activate the **medibuntu** repository.

---

### Post by realzippy on 2009-11-04
Suggest to enable the medibuntu repository which also contains a realplayer version and some useful codecs ;-)

[http://www.medibuntu.org/](http://www.medibuntu.org/)


[B]sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \
 --output-document=/etc/apt/sources.list.d/medibuntu.list &&
sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update[/B]

---

### Post by Richiegs on 2009-11-04
> **liquidbee said:**
> How did you installed it ?
I installed Realplayer using command in the Terminal.

---

### Post by liquidbee on 2009-11-04
> **Richiegs said:**
> I installed Realplayer using command in the Terminal.

What command ? Please be more specific.

---

