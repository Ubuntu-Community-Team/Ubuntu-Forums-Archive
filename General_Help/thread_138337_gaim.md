---
title: "gaim"
date: 2006-03-01
forum: General Help
---

### Post by BatteryCell on 2006-03-01
Alright so gaim 1.5 works fine, but whenever I try to compile gaim 2.0 it gives me errors about GTK...but dont I have to have GTK installed for gaim1.5 to work...this is my question...what am I missing??

---

### Post by gingermark on 2006-03-01
You do need some Gtk libs to run Gaim 1.5 - in all likely-hood you installed it with Adept or apt-get and the dependencies were taken care of for you.

Also keep in mind you need the development libraries to compile a program - these are not required when you install a binary.

The documentation that comes with the source code should tell you what you need. I compiled the package a while ago, and looking at my log I seemed to have installed the following packages:

libgcrypt7 (1.1.90-9ubuntu1)
libgcrypt7-dev (1.1.90-9ubuntu1)
libgnutls10 (1.0.4-8ubuntu1)
libgnutls10-dev (1.0.4-8ubuntu1)
libgpg-error-dev (1.0-1)
libopencdk8-dev (0.5.5-10)
libtasn1-2-dev (0.2.10-4)
libcrypto++5.2c2 (5.2.1c2-5)

I can't be certain all of them are necessary though.

I compiled it using checkinstall, so have a .deb file for Gaim 2.0 Beta2. It's too big to attach, but I've uploaded it [here]("http://www.savefile.com/files/8962384"), so feel free to use it if you want. I make no promises, but if you are using the ix86 version of Kubuntu it should work.

Just save it somewhere, navigate there in Konsole, and type ```
sudo dpkg -i gaim-2.0.0beta2_i386.deb
```

If you do decide to use the .deb and it doesn't work consider installing some of those packages listed, at least the ones that don't end in '-dev' as installing this way doesn't take care of dependencies.

---

