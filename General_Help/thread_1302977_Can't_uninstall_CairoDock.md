---
title: "Can't uninstall CairoDock"
date: 2009-10-27
forum: General Help
---

### Post by Pott on 2009-10-27
I got the app, tried messing around with it, messed around too much and couldn't set it up right and lost most of my options.

I want to remove it, install it again and start over.

sudo apt-get remove cairo-dock cairo-dock-plug-ins does NOT work! That's the logical method and the method from the website...

Any ideas how to totally remove the thing?

Thanks!

---

### Post by martrn on 2009-10-27
```
dpkg --get-selections | grep cairo
```

And then from the results you get (you might get a few packages)....

```
apt-get remove --purge cairopackage1
apt-get remove --purge cairopackage2
apt-get remove --purge cairopackage3
apt-get remove --purge cairopackage4
```
# etc....etc.....

---

### Post by fabounet on 2009-10-28
I don't think you need to reinstall it, just delete/rename the folder
~/.config/cairo-dock/current_theme
and restart your dock, or just choose another theme.
If you experience some bug with the latest version (currently 2.1.1-2), please report them on cairo-dock.org, so that they can be fixed. Thanks.

---

### Post by Pott on 2009-10-28
ARGH!!!

I did martrn's method, deleted all packages individually but eventually it deleted ALL INSTALLED PACKAGES on Ubuntu!!!

So I have a half functioning OS now and no way to know exactly what's missing... ARG!

Aside from a clean install, which may further mess up my partitioning, is there anyway I can get back all default programs etc...? 

Or I may just wait for tomorrow's Karmic release and start from the ground up...

---

### Post by martrn on 2009-10-28
Yes you can re-install the gnome desktop. If you can log on to a terminal, type in your username and password then type :

```
sudo apt-get install ubuntu-desktop
sudo apt-get update
```
to install the gnome desktop.

-- or --

```
sudo apt-get install kubuntu-desktop
sudo apt-get update
```
to install the kde desktop.
[URL="https://answers.launchpad.net/ubuntu/+question/36085"]
https://answers.launchpad.net/ubuntu/+question/36085[/URL].

---

### Post by Pott on 2009-10-28
Thanks :)  eventually I nuked the whole thing using Vista's disk manager, and now I'm re-partitioning the D drive as it was before, it'll be easier for Karmic tomorrow.

---

