---
title: "How to move firefox bookmark"
date: 2009-11-10
forum: General Help
---

### Post by jee_bee on 2009-11-10
I just setup a dualboot sytem on my wife laptop ( Ubuntu & XP )

4 partition....

-ubuntu system.
-xp system.
-data.
-restore. 

I want ubuntu and xp to share everyting:   documents, agenda, bookmark..........

[COLOR="DarkRed"]NOW IM TRYING TO SET FIREFOX IN UBUNTU TO SHARE BOOKMARK WITH INTERNET EXPLORER AND FIREFOX IN WINDOWS....  I ALREADY MOVE THE "FAVORIT" FOLDER IN WINDOWS TO MY "DATA" PARTITION......

HOW CAN I CHANGE FIREFOX DEFAULT BOOKMARK LOCATION[/COLOR]

[COLOR="Blue"]May  ave somting to do with those setting????........ \|/[/COLOR]   (   about:config    )
[IMG]http://img42.imageshack.us/img42/1625/captureko.png[/IMG]

---

### Post by lovinglinux on 2009-11-10
Best way of achieving what you want is to sync bookmarks with [Xmarks](https://addons.mozilla.org/en-US/firefox/addon/2410).

---

### Post by lovinglinux on 2009-11-10
> **lovinglinux said:**
> Best way of achieving what you want is to sync bookmarks with [Xmarks](https://addons.mozilla.org/en-US/firefox/addon/2410).

If you want to share the entire Firefox profile, then you could create a symlink from profile folder in the shared data partition to ~/.mozilla/firefox. But I wouldn't recommend doing that, because several Firefox extensions have different versions for Linux and Windows.

---

