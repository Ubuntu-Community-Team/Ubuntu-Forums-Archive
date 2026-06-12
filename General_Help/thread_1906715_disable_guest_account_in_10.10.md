---
title: "disable guest account in 10.10"
date: 2012-01-09
forum: General Help
---

### Post by Unguidedone on 2012-01-09
I would like to know how to delete and not allow a guest account on my system.

```
julio@julio-ThinkCentre-M52:~$ users
julio julio
julio@julio-ThinkCentre-M52:~$ 

```i was able to find the topic for 11.10 but not for 10.10  :(

also when i booted my computer apparmor gave me a debug error message:
[IMG]http://i913.photobucket.com/albums/ac340/Happy_Mask_Salesman/whatisthis.png[/IMG]


Any help would be most welcome, thanks :D

---

### Post by Unguidedone on 2012-01-11
no help?

---

### Post by jerrrys on 2012-01-11
This link is for lightdm, but gdm should be similar.

[http://ubuntuforums.org/archive/index.php/t-1843933.html](http://ubuntuforums.org/archive/index.php/t-1843933.html)

Or you should just be able to remove the package:

gdm-guest-session

---

