---
title: "Help Find Lost App..."
date: 2011-05-21
forum: General Help
---

### Post by mparker81 on 2011-05-21
I was dual booting my old laptop and then the mobo went out. I then bought a new pc and tucked the old one away in the closet. I primarily used the Ubuntu machine for "backing up" dvds. I have a 2 year old and she is pretty rough on dvds...   

Anyhow I haven't messed with it for over a year and I am now dual booting on an old desktop, but I am having a hard time ripping/burning dvds....   I cant remember the 2 apps I used to use...  

I remember one was DeVeDe  but i cant remember what I used to go from dvd to avi...  

I have access to the old hard drive via sata to usb cable, Is there a way i can find an app list or something from it?

---

### Post by AlphaLexman on 2011-05-21
You should use one of these:
[LIST]
[*]apropos [keyword]
[*]locate [program_name]
[*]which [alias, function or program_name]
[/LIST]
Or try:
```
find . -type f -name "*dvd*"
```
```
find . -type f -name "*avi*"
```
from the mounted directory.

---

