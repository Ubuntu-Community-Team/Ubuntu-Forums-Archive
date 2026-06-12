---
title: "Please help a newbie"
date: 2010-08-25
forum: General Help
---

### Post by Vinsombra on 2010-08-25
Alright, I'm a linux newbie, I downloaded Ubuntu and I have stumbled my way around a bit.  Often I can find enough information to figure out what I need to do, but oftentimes i see helpful forum posts and can't understand word one.

Anyways, my current issue is: I am apparently missing "libGL.so.1"

Can I simply download this file and place it in a folder, is it system specific, does it need to be tailored to my install?

Linux newbie like don't know how to open a terminal newbie here.

---

### Post by ubudog on 2010-08-25
About 4 years ago, I was a total newbie, so I know how you feel.

Here is how you install it:
Open a terminal using Applications>Accessories>Terminal, and type:
```
sudo apt-get install libgl1-mesa-swx11
```

That should do it.  Good luck.

---

