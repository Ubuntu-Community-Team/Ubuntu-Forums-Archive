---
title: "What settings does remastersys keep?"
date: 2011-03-22
forum: General Help
---

### Post by mooserider2 on 2011-03-22
I am interested in creating a ubuntu remixed distro, with remastersys. I want to know if firefox addons, backgrounds, and other settings will be set to default on the live cd. Thank you.

---

### Post by mooserider2 on 2011-03-22
This seems like it would be an easy thing to answer... I just need to know if it keeps firefox addons and config.:(

---

### Post by Frogs Hair on 2011-03-22
Best to read it from their site.[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

---

### Post by mooserider2 on 2011-03-22
Well I looked around on the website, and couldn't find out anything specifically about firefox addons. Now that I think about it though firefox settings for addons are stored in the home folder, are they not? Just moving my home to /etc/skel/ should solve it. Please correct me if I am wrong.

---

### Post by mooserider2 on 2011-03-23
Still need help here...:(

---

### Post by Fragadelic on 2011-05-20
Are you using backup mode or dist mode?

---

### Post by aysiu on 2011-05-20
```
sudo cp -R ~/.mozilla /etc/skel
sudo chown root:root /etc/skel
``` should do the trick.

---

### Post by Fragadelic on 2011-05-20
Whatever you setup properly as global default on the system will be used for dist mode.  If you only have your settings in your specific user and use dist mode, none of those changes are used since you didn't apply them to the global config settings.

---

### Post by Fragadelic on 2011-05-20
> **aysiu said:**
> ```
sudo cp -R ~/.mozilla /etc/skel
sudo chown root:root /etc/skel
``` should do the trick.

What you have to remember about this is that it will copy everything over from the .mozilla folder including any cached files, history, passwords saved, etc. so if you really want to do it this way you will need to clean up the mozilla config first.  You can do this either through the Mozilla preferences or by using the "Bleach Bit" app which I highly recommend for anyone making a dist iso.

Bleach Bit was not created by me but it allows you to clean things up nice before you create the dist mode iso.  FWIW, I use this for my own dist remasters of both ubuntu respins and debian respins and highly recommend it.  It also helps clean some other stuff up and should help reduce the size of the final iso.

---

### Post by linuxinstalledfromhdd on 2011-05-20
You want:

[I]sudo -s
cp -Rf .config/ .fontconfig/ .gconf/ .gconfd/ .gnome2/ .mozilla/ .nautilus/ /etc/skel/
cp -Rf .config/ .fontconfig/ .gconf/ .gconfd/ .gnome2/ .mozilla/ .nautilus/ /root/
cd /etc/skel
chown -R root:root .config/ .fontconfig/ .gconf/ .gconfd/ .gnome2/ .mozilla/ .nautilus/
cd /root
chown -R root:root .config/ .fontconfig/ .gconf/ .gconfd/ .gnome2/ .mozilla/ .nautilus/[/I]

---

### Post by linuxinstalledfromhdd on 2011-05-20
And just so you know that configuration is for Classic Gnome in 11.04.  Unity you will have to figure it out yourselves.

---

### Post by Fragadelic on 2011-05-20
This may lead to the live user creation failing.

Whenever you copy user files to /etc/skel, they need to be purged of that user's specific config settings as the errors from these will not allow the live user to be created.

```
#SKELUSER should be set to the username from which the config files were copied.
#If your username where you copied from was "ubuser" then do this before you run the rest without the # at the beginning
#SKELUSER=ubuser
rm -rf /etc/skel/.gconf/system/networking
rm -rf /etc/skel/.local/gvfs-metadata
for i in /etc/skel/.gnome2/keyrings/*; do rm $i; done
find /etc/skel | grep "$SKELUSER" | xargs rm -rf '{}'
grep -Rl "$SKELUSER" /etc/skel | xargs rm -rf '{}'

```

---

### Post by linuxinstalledfromhdd on 2011-05-20
Thanks man.. user frag is a legend.

---

### Post by Fragadelic on 2011-05-20
Blindly copying the user's config folders to /etc/skel is the reason that 99% of the folks that end up posting questions about the live user password or similar posts did on their original system.

Those files with user specific settings including folder references will cause user creation to fail during the live boot and there will be no live user created so the iso is useless.

---

### Post by aysiu on 2011-05-20
> **linuxinstalledfromhdd said:**
> You want:

[I]sudo -s
cp -Rf .config/ .fontconfig/ .gconf/ .gconfd/ .gnome2/ .mozilla/ .nautilus/ /etc/skel/
cp -Rf .config/ .fontconfig/ .gconf/ .gconfd/ .gnome2/ .mozilla/ .nautilus/ /root/
cd /etc/skel
chown -R root:root .config/ .fontconfig/ .gconf/ .gconfd/ .gnome2/ .mozilla/ .nautilus/
cd /root
chown -R root:root .config/ .fontconfig/ .gconf/ .gconfd/ .gnome2/ .mozilla/ .nautilus/[/I]
You actually want ```
sudo -i
``` and not *sudo -s*

---

### Post by Fragadelic on 2011-05-20
The proper way of setting most of these takes a bit longer as you should be putting them in /etc/gconf in the appropriate file.

Some apps have settings in /usr/share or /usr/lib ,etc.

If you do make changes to the global files, you will want to divert them so any package updates won't overwrite them.

I use a little script I made to divert files:
```
#!/bin/bash

if [ -f $1 ]; then
dpkg-divert --add --rename --divert $1.orig $1
cp $1.orig $1
echo "$1 diverted to $1.orig"
fi
```

I called it "remdivert" and put it in /usr/local/bin.

The only thing you need to pass it is the filename with full path included.

For example: if you changed /etc/grub.d/10_linux config file for grub setup to have something different in it, you would do the following:

sudo remdivert /etc/grub.d/10_linux
This will leave your 10_linux that you modifed there and create one called 10_linux.orig.

Diverted files are what dpkg, apt and aptitude will update if there is a package update that contains the original file.

In the example above you will want to make the 10_linux.orig read only and not executable or it will run during grub creation anyway.  You don't have to do this for most other things.

[http://manpages.debian.net/cgi-bin/man.cgi?query=dpkg-divert](http://manpages.debian.net/cgi-bin/man.cgi?query=dpkg-divert)

---

