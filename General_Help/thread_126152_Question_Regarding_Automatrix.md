---
title: "Question Regarding Automatrix"
date: 2006-02-05
forum: General Help
---

### Post by wilsonisme on 2006-02-05
Heya,
Will auto matrix overwrite programs, etc, already installed? For example lets say you have an older version of firefox, must you uninstall it first before using auto matrix to install the new version, or will automatrix do all the work for you? 

Does the same hold true for codecs and things like that?

Thanks,
Wilson

---

### Post by o_fortuna on 2006-02-05
[QUOTE=wilsonisme]Heya,
Will auto matrix overwrite programs, etc, already installed? For example lets say you have an older version of firefox, must you uninstall it first before using auto matrix to install the new version, or will automatrix do all the work for you? 

Does the same hold true for codecs and things like that?

Thanks,
Wilson[/QUOTE]
Automatix does not uninstall anything, including firefox, as far as I know (I know it does NOT uninstall firefox when installing the new version). Also, Automatix does everything itself. You don't need to do anything in preparation except have an active internet connection.

Everything in Automatix just works. Don't worry about it at all.

---

### Post by wilsonisme on 2006-02-05
If it doesnt uninstall a program before installing the same thing, that sounds like something "to worry about" is it not? I don't want two of everything on my system, lol.

---

### Post by dustigroove on 2006-02-05
Automatix does not intelligently install the applications you choose from the list, it simply provides a basic front end to more easily install a variety of frequently desired apps.

For example, if you install Firefox 1.5, it will not remove Firefox 1.0.7.

---

### Post by RAOF on 2006-02-05
[QUOTE=dustigroove]Automatix does not intelligently install the applications you choose from the list, it simply provides a basic front end to more easily install a variety of frequently desired apps.

For example, if you install Firefox 1.5, it will not remove Firefox 1.0.7.[/QUOTE]
Additionally, you **don't** want to remove Firefox 1.0.7, because a number of other programs (notably the help system) require the Firefox libraries.

---

### Post by wilsonisme on 2006-02-05
Um wouldnt those be installed again with 1.5?

---

### Post by psychicdragon on 2006-02-05
Automatix installs Firefox 1.5 in /opt/firefox (I believe).

If it were to remove Firefox 1.07 and install 1.5, it's possible that packages depending on the Firefox libs would break.

---

### Post by RAOF on 2006-02-05
[QUOTE=wilsonisme]Um wouldnt those be installed again with 1.5?[/QUOTE]
It's a big update from 1.0.7 to 1.5.  The libs aren't the same - apps wanting the 1.0.7 libs won't work with the 1.5 libs.

---

### Post by wilsonisme on 2006-02-06
Alright so beyond leaving two firefoxes on the system, what about all the other things Automatrix does? 

Example: If you run automatrix two times consecutivly (checking the same things each time) will you end up with TWO of everything?

---

### Post by beerorkid on 2006-02-06
I believe it would just write over the existing install.  I have goofed up a few things being the tinkerer I am, only to use automatix to get it working once again.

I would think it would leave .config files alone though.

Also with the log peeps can tell what has been installed, although few probably check it and just reinstall things over and over again when a new version of automatix is released thinking that they will get updated versions of the programs thay have installed.  When apt-get update / install will handle updating of programs, or the update notifier.

That being said you would see a bunch of people complaining that there are two of everything, which does not seem to be the case in the main thread.

---

### Post by o_fortuna on 2006-02-06
[QUOTE=wilsonisme]Alright so beyond leaving two firefoxes on the system, what about all the other things Automatrix does? 

Example: If you run automatrix two times consecutivly (checking the same things each time) will you end up with TWO of everything?[/QUOTE]
In my experience, rechecking things you've already installed has no effect. Anything that uses APT wouldn't install twice, and it includes a check to prevent you from activating DMA twice, or something.

---

