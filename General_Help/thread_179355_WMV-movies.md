---
title: "WMV-movies"
date: 2006-05-19
forum: General Help
---

### Post by Abadon on 2006-05-19
Hi there,

I'm new in linux and ubuntu of course. I'm using ubuntu amd64 version and I could not play any videos untill today. After few updates I've noticed that all my vids are working perfectly fine and I can play them with any player I want. That's fantastic news  because I was just about to switch to 32bit version. Xvid,divx and mpg are working just fine the only one I can't play is WMV files. Any sugestion or help would be greatly appreciated.[http://ubuntuforums.org/images/smilies/icon_biggrin.gif](http://ubuntuforums.org/images/smilies/icon_biggrin.gif)

---

### Post by halfvolle melk on 2006-05-19
Do you have w32codecs installed? If not, try
```
sudo apt-get install w32codecs
```
I thinks they're in the Multiverse repository. Here's how to add it:
[https://wiki.ubuntu.com/AddingRepositoriesCliHowto](https://wiki.ubuntu.com/AddingRepositoriesCliHowto)

With w32codecs som wmv's will work, some won't.

---

