---
title: "Why is this grayed out?"
date: 2010-07-20
forum: General Help
---

### Post by davavanstone on 2010-07-20
Im trying to get my USB autorun to work, when i insert it i get this

[IMG]http://i975.photobucket.com/albums/ae232/davavanstone/Screenshot-6.png[/IMG]

Any ideas on what ive got to install?

---

### Post by mike555 on 2010-07-20
It's probably a auto run Windows program ......... you should be able to view the contents of the cd if they are just pictures and not some weird format ...

---

### Post by clhsharky on 2010-07-20
What options are offered in drop down?

Auto run is off by default but can be turned on. Security feature.

Sharky

---

### Post by davavanstone on 2010-07-20
Ive created the autorun script (usb), i'm not worried about the security side of things.

The menu is unclickable, if i enter media with photos, the same would happen untill i install gthumb or fspot.  I wondered if any of you knew what i have to install to bypass the security and make it run the autorun?

---

### Post by davavanstone on 2010-07-20
autorun is on in gconf-editor in the nautilus section, but it doesnt have a program to load the script if you get what i mean...

---

### Post by mc4man on 2010-07-20
Ck in file management for option under the media tab 
There are 2 places, Software and Other Media dropdown 
(depending on the filesystem on the usb drive and the nature/name of the file either may do the same., try Software
```
nautilus-file-management-properties
```

You're looking to set the autorun prompt option

If no choices avail. then you'll need to edit a file - ck. first

(while it's possible to override the prompt, ie. have the script autorun, that's a different story..

---

### Post by davavanstone on 2010-07-20
nah i was in the nautilus setting earlier, software and 'unix software' in the settings both say no applications found, if there a conf somewhere where i can add applications for nautilus to launch?

---

### Post by mc4man on 2010-07-20
What release of ubuntu are you using and are you the admin. user?

 try running  this
```
gedit ~/.local/share/applications/mimeapps.list
```

add this line and *it may open up the options*, you may or may not need to restart

```
x-content/software=nautilus-autorun-software.desktop;
```

and or 
```
x-content/unix-software=nautilus-autorun-software.desktop;
```

(( if your 'script' isn't set, (or can't be set), as executable then it's not going to run anyway

---

### Post by davavanstone on 2010-07-21
the script is set to be executable, but still after following your instructions the drop down list is still grayed out and says no applications found.

As for versions of ubuntu, it is on lucid, but im testing it on my mint 8 laptop as the lucid computer is a media pc and has no keyboard attatched etc, hope this isnt a prob?

---

### Post by davavanstone on 2010-07-21
dont worry, i dont think ubuntu can do it this way, i will use udev

---

