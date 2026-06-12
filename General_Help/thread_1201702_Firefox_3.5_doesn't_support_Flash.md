---
title: "Firefox 3.5 doesn't support Flash"
date: 2009-07-01
forum: General Help
---

### Post by Inventech on 2009-07-01
I just upgraded from Minefield 3.6 to Firefox 3.5 and for some reason the flash plugin isn't recognized by Firefox. It works perfectly fine in Minefield.

---

### Post by abhi_69 on 2009-07-01
how do u upgrade to firefox 3.5? is it final version? do you use ppa repo called ubuntu-mozilla-daily for this purpose? i also enable this repo. but it only installs minefield, not firefox 3.5 final version.
can u inform me?

---

### Post by VCoolio on 2009-07-01
check your folder /usr/lib/firefox-3.5/plugins if there is a flash plugin. If not, make a symbolic link to it (check where your flash plugin is located), e.g.:

```
cd /usr/lib/firefox-3.5/plugins
sudo ln -s /usr/lib/flashplugin-installer/libflashplayer.so libflashplayer.so
```

And try again. 

abhi_69: [http://ubuntuforums.org/showthread.php?t=1200781](http://ubuntuforums.org/showthread.php?t=1200781) read the end of the first post.

---

### Post by Inventech on 2009-07-01
> **abhi_69 said:**
> how do u upgrade to firefox 3.5? is it final version? do you use ppa repo called ubuntu-mozilla-daily for this purpose? i also enable this repo. but it only installs minefield, not firefox 3.5 final version.
can u inform me?

[http://coffeecokeandcode.blogspot.com/2009/06/firefox-35-on-ubuntu-904.html](http://coffeecokeandcode.blogspot.com/2009/06/firefox-35-on-ubuntu-904.html)

---

