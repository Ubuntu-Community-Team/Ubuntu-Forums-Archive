---
title: "[SOLVED] firefox does not upgrade to 3.5"
date: 2009-07-17
forum: General Help
---

### Post by zero777zero on 2009-07-17
firefox 3.5 appeared in my upgrade manager, i installed it, rebooted, rechecked upgrade manager, its no longer there, however firefox 3.0 is installed :S clicking the firefox desktop icon launches firefox 3.0 :S

---

### Post by zero777zero on 2009-07-18
bump

---

### Post by zero777zero on 2009-07-18
bump

---

### Post by ptn107 on 2009-07-18
Installing Firefox 3.5 only installs it side-by-side with Firefox 3.0, and 3.0 will remain the system default.  The only way to launch 3.5 would be to go to Applications -> Internet -> Shiretoko when you want to use it (or make a desktop shortcut).  To make Ubuntu recognize Firefox 3.5 as the default browser do the following:

```
sudo rm /usr/bin/firefox && sudo ln -s /usr/bin/firefox-3.5 /usr/bin/firefox
```

It you want to remove firefox 3.0 you can do the following:

```
sudo aptitude purge firefox-3.0 firefox-3.0-branding firefox-3.0-gnome-support
```

---

### Post by zero777zero on 2009-07-18
thanks, this worked like a charm ;P

why shiretoko instead of proper firefox tho? trademark problems or something?

---

### Post by ptn107 on 2009-07-18
I believe it's the development codename.

---

### Post by LightningCrash on 2009-07-18
> **zero777zero said:**
> thanks, this worked like a charm ;P

why shiretoko instead of proper firefox tho? trademark problems or something?

shiretoko was the build name of FF3.5 or some jazz like that.

---

### Post by philinux on 2009-07-18
I would have kept 3.0.11 and ran them side by side for now as many addons and themes have not been upgraded yet.

---

### Post by rainlsot on 2009-07-18
that explains what "shiretoko" was...thanks guys..

---

### Post by CatKiller on 2009-07-18
> **ptn107 said:**
>  To make Ubuntu recognize Firefox 3.5 as the default browser do the following:

```
sudo rm /usr/bin/firefox && sudo ln -s /usr/bin/firefox-3.5 /usr/bin/firefox
```

Or, y'know, set the System &#8594; Preferences &#8594; Preferred Applications &#8594; Web Browser option to firefox-3.5.

Linux **is** a multi-user OS, you know.

> **zero777zero said:**
>  why shiretoko instead of proper firefox tho?

Because they can't both be called Firefox without having their menu entries being confusingly identical. Since Firefox 3.0 is the one that shipped with Jaunty, that's the one that gets the prize. Firefox 3.5 will be shipped with Karmic, so it will be called Firefox then. I don't know if Firefox 3.0 will be referred to a Gran Paradiso in Karmic or just removed entirely.

---

### Post by lovinglinux on 2009-07-18
The 4 most popular methods of installation of Firefox 3.5 (Psychocats, Ubuntuzilla, Repository, Shiretoko/Swiftfox) are available in the "Install Other Versions" section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567). 

There is also a detailed explanation of each installation method provided, comparing the most important differences. I personally tested all of them and they work like a charm, but I recommend methods 1 (Psychocats) and 2 (Ubuntuzilla).

---

### Post by jpm_newbie on 2009-07-19
To make Ubuntu recognize Firefox 3.5 as the default browser do the following:

```
sudo rm /usr/bin/firefox && sudo ln -s /usr/bin/firefox-3.5 /usr/bin/firefox
```Catkiller, thank you for the last piece of the puzzle.  I couldn't get Firefox 3.5 to launch when the pc told me it already had it.  :D

---

### Post by phillw on 2009-07-19
> **jpm_newbie said:**
> To make Ubuntu recognize Firefox 3.5 as the default browser do the following:

```
sudo rm /usr/bin/firefox && sudo ln -s /usr/bin/firefox-3.5 /usr/bin/firefox
```Catkiller, thank you for the last piece of the puzzle.  I couldn't get Firefox 3.5 to launch when the pc told me it already had it.  :D


Does that method retain all the bookmarks & passwords ?

Regrds,

Phillw

---

### Post by lovinglinux on 2009-07-19
> **phillw said:**
> Does that method retain all the bookmarks & passwords ?

Regrds,

Phillw

Passwords, bookmarks and all Firefox **3.0** settings are stored in profiles under **~/.mozilla/firefox**, while Shiretoko **3.5** stores under **~/.mozilla/firefox-3.5**. Nevertheless, Shiretoko copies all profiles from **~/.mozilla/firefox** when you first launch it.

The method you are referring to has nothing to do with Firefox settings, just the program executable files. Nevertheless, keep in mind that when the new Ubuntu release (Karmic Koala) comes out, Firefox 3.5 will be the default browser and will use **~/.mozilla/firefox** again, so you will probably need to copy your settings from **~/.mozilla/firefox-3.5** back to **~/.mozilla/firefox**.

I recommend making backups of your profile using [FEBE](https://addons.mozilla.org/en-US/firefox/addon/2109) extension, because you can restore a backup to any Firefox version you have. It will save the files in the correct profile folder, depending on which Firefox version you are using to restore the profile.

More info [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567)

---

