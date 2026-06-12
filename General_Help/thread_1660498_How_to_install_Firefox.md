---
title: "How to install Firefox"
date: 2011-01-05
forum: General Help
---

### Post by wavinwayne on 2011-01-05
I am running Ubuntu 10.10. I uninstalled Firefox a few weeks ago, thinking I would never use it (I use Chrome). I decided to re-install FF as a backup in case some website(s) wouldn't function properly with Chrome. For some odd reason, when I try to install Firefox from the Ubuntu software center, it fails every time, and tells me to check my internet connection, which is functioning perfectly. Any ideas on what is going on, and how to install Firefox?

I went to the Firefox website and downloaded the Firefox setup files, but I have no idea what to do with them now. I know how to unpack the files, but that's it.

Any help is appreciated.

---

### Post by anystupidname1 on 2011-01-05
Don't bother with setup files.

```
sudo aptitude update
sudo aptitude install firefox
```

---

### Post by kimberlite on 2011-01-05
You can always use synaptic graphical package manager also. Select "System" - "Administration" - "Synaptic" from the main menu. There you can search for Firefox and install it.

---

### Post by anystupidname1 on 2011-01-05
> **kimberlite said:**
> You can always use synaptic graphical package manager also. Select "System" - "Administration" - "Synaptic" from the main menu. There you can search for Firefox and install it.

Yea, if you're one of those pointy clicky kinda peoples... :-P :P

---

### Post by kimberlite on 2011-01-05
> **anystupidname1 said:**
> Yea, if you're one of those pointy clicky kinda peoples... :-P :P

As most of newbies, like me, and probably those who ask at "absolute beginers'" .

---

### Post by lovinglinux on 2011-01-05
As others have said, I would recommend:

```
sudo apt-get install firefox
```

However, if you still want to install manually, then I would recommend getting Firefox 4.

You can see a tutorial on how to install Firefox from Mozilla at [http://www.webgapps.org/firefox/installing-other-versions](http://www.webgapps.org/firefox/installing-other-versions)

For Firefox 4 see [http://www.webgapps.org/firefox/installing-firefox-4](http://www.webgapps.org/firefox/installing-firefox-4)

---

### Post by wavinwayne on 2011-01-05
Before trying any of the suggestions given, I waited a couple of hours and again tried installing FF from the Ubuntu Software Center. This time, FF installed correctly. Thanks to those who offered suggestions.

---

