---
title: "Login as root"
date: 2011-10-22
forum: General Help
---

### Post by lwalper on 2011-10-22
See the following closed discussion for history on my question.

[http://ubuntuforums.org/showthread.php?t=1867239&page=2]("http://ubuntuforums.org/showthread.php?t=1867239&page=2")

So, using the GUI to drag/drop is pretty much out of the question? I have a font on my desktop that I want to place in the usr/share/fonts/truetype folder. Since I am unfamiliar with the terminal commands to perform this simple task, it just doesn't happen? I'd like to install some fonts, but apparently I'll be unable to do so.

Though I appreciate the security concerns mentioned in the foregoing link, I'd still like to install some fonts from the GUI.

---

### Post by haqking on 2011-10-22
> **lwalper said:**
> See the following closed discussion for history on my question.

[http://ubuntuforums.org/showthread.php?t=1867239&page=2]("http://ubuntuforums.org/showthread.php?t=1867239&page=2")

So, using the GUI to drag/drop is pretty much out of the question? I have a font on my desktop that I want to place in the usr/share/fonts/truetype folder. Since I am unfamiliar with the terminal commands to perform this simple task, it just doesn't happen? I'd like to install some fonts, but apparently I'll be unable to do so.

Though I appreciate the security concerns mentioned in the foregoing link, I'd still like to install some fonts from the GUI.

if you read [rootsudo]("https://help.ubuntu.com/community/RootSudo") pointed out to you in that thread you can see you can do it with sudo from command line or launch nautilus with gksudo

---

### Post by Foxheadz on 2011-10-22
Well you can just run ```
gksu nautilus
``` to open nautilus as root, but most fonts can be installed by opening them with font viewer and clicking the "install" button

---

### Post by james.m on 2011-10-22
> **lwalper said:**
> See the following closed discussion for history on my question.

[http://ubuntuforums.org/showthread.php?t=1867239&page=2](http://ubuntuforums.org/showthread.php?t=1867239&page=2)

So, using the GUI to drag/drop is pretty much out of the question? I have a font on my desktop that I want to place in the usr/share/fonts/truetype folder. Since I am unfamiliar with the terminal commands to perform this simple task, it just doesn't happen? I'd like to install some fonts, but apparently I'll be unable to do so.

Though I appreciate the security concerns mentioned in the foregoing link, I'd still like to install some fonts from the GUI.

Your fonts need to absolutely, 100% go in **/usr/share/fonts**? **~/.fonts/** isn't sufficient?

---

### Post by lwalper on 2011-10-22
Installing from the font viewer worked great. Thanks!

---

