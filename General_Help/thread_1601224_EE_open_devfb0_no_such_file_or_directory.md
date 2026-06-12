---
title: "EE open /dev/fb0: no such file or directory"
date: 2010-10-20
forum: General Help
---

### Post by neobahamut72 on 2010-10-20
hey, i tried to install a music program (amarok or somethin i think) and when i tried to restart, i got the EE open /dev/fb0: no such file or directory. running in low graphics mode error.
 
didnt make any other changes, it goes straight to command line after this. how can i get it to go back to normal...ive tried to load up recovery mode and such, but no dice. any recommendations?

---

### Post by Cuddles McKitten on 2010-10-20
Try this and see if it helps:

```
sudo apt-get --reinstall xserver-xorg
```

If that doesn't work, post the output of:

```
lspci -vv
```

---

### Post by neobahamut72 on 2010-10-20
that command didnt do anything.
 
and the 2nd one let out a bunch of stuff, but i cant copy and paste that...so i duno

---

