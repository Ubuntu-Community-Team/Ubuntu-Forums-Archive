---
title: "Lucid Lynx questions."
date: 2010-05-11
forum: General Help
---

### Post by Cityscape on 2010-05-11
1. How do I put the minimize, maximize & close buttons back on the right side?
2. everytime I leave my PC for about 5 mins and come back the screen is locked, this is very annoying and pointless as I have a desktop. How/where can I set it to never lock screen when idle?

---

### Post by fragos on 2010-05-11
Easiest way is to install Ubuntu Tweak. It has a configuration option for the top window bar.

---

### Post by DougieFresh4U on 2010-05-11
Go to  System>Preferences>Screensaver
the boxes there are check marked, undo them, I also select 'Power Management' and change to 'never'

---

### Post by kikdadog on 2010-05-12
> **DougieFresh4U said:**
> Go to  System>Preferences>Screensaver
the boxes there are check marked, undo them, I also select 'Power Management' and change to 'never'

Thank YOU !!!!!!!!!!!!!      :)

---

### Post by Cityscape on 2010-05-12
Okay, I've disabled the lock screen. Thanks a ton for helping with that.

But I could not find ubuntu tweak in synaptic. Is there not a way that I can move those buttons to the right easily without a 3rd party program?

---

### Post by TwoEars on 2010-05-12
Run this command in the terminal, it should revert it for you - 
```
gconftool -s /apps/metacity/general/button_layout -t string menu:minimize,maximize,close
```

---

### Post by DeMus on 2010-05-12
> **Cityscape said:**
> Okay, I've disabled the lock screen. Thanks a ton for helping with that.

But I could not find ubuntu tweak in synaptic. Is there not a way that I can move those buttons to the right easily without a 3rd party program?

Open a terminal (Application - Accessories - Terminal) and type gconf-editor
Go to Apps/Metacity/General
On the right you see the item button layout.
Double click on the contents and edit it to:
:minimize,maximize, close
(mind the colon on the beginning of the line it is very important)
Close the program and the terminal again.

---

### Post by fragos on 2010-05-12
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/) will give you a download to install. You can then use Ubuntu Tweak to add it's own repository to your updates. When ever I upgrade Ubuntu releases, Ubuntu Tweak is one of the first aps I run. It offers an endless list of useful repositories and a strait forward way to set system parameters.

---

### Post by DeMus on 2010-05-12
> **fragos said:**
> [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/) will give you a download to install. You can then use Ubuntu Tweak to add it's own repository to your updates. When ever I upgrade Ubuntu releases, Ubuntu Tweak is one of the first aps I run. It offers an endless list of useful repositories and a strait forward way to set system parameters.

I've read last week that Ubuntu-tweak is a program which can destroy your installation so it is not safe to use it. Don't know if it is true but better be safe than sorrow.

---

### Post by fragos on 2010-05-12
I've been using it for a number of years and never had any troubles. I wouldn't run my system without it and I recommend it to all my clients. Like always, don't change what you don't understand. I wouldn't be surprised if you accuser had pilot issues.

---

### Post by Cityscape on 2010-05-13
> **fragos said:**
> [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/) will give you a download to install. You can then use Ubuntu Tweak to add it's own repository to your updates. When ever I upgrade Ubuntu releases, Ubuntu Tweak is one of the first aps I run. It offers an endless list of useful repositories and a strait forward way to set system parameters.
Thanks a lot, I installed it. It worked so well and easy.

And by the way it didn't destroy my installation. Although I'm not quite sure I understand this Ubuntu Tweak repository thing.

By the way, Ubuntu tweak did not destroy my installation. I'm going to recommend it to a friend who is a new Ubuntu user.

---

### Post by fragos on 2010-05-13
> **Cityscape said:**
> Thanks a lot, I installed it. It worked so well and easy.

And by the way it didn't destroy my installation. Although I'm not quite sure I understand this Ubuntu Tweak repository thing.

By the way, Ubuntu tweak did not destroy my installation. I'm going to recommend it to a friend who is a new Ubuntu user.

A repository is a collection of installable files or packages. Repositories are sometimes called catalogs. These collection follow a set of rules for their file structure so that programs like the Update Manager can fetch packages from any repository it given. Ubuntu Tweak provides a higher level user interface to add repositories to the local catalog of installable packages.

---

