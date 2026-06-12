---
title: "DVD won't play for &quot;no reason&quot;"
date: 2011-01-03
forum: General Help
---

### Post by nearlymagicman on 2011-01-03
Hey,


i got quite a surprising problem. My Totem player wont play my DVDs for (i quote) "no reason", that is the error Message it gives me.

I is NOT the DVD player (I tried two different one) and it is not the DVD (I tried three different). It just has "no reason".

I did install the restricted-extra and i also tried VLC (which just shuts itself down).


I hope you got a solution, thanks for your help.


&#8364;: I tried it with windows and it works perfectly...

---

### Post by seawolf167 on 2011-01-03
DVDs have restricted formats, so you'll need to do the following:

1st, install the restricted extras (repeating it here in case any else reads and wants to know the package name)

```
sudo apt-get install ubuntu-restricted-extras
```2nd, install libdvdread4

```
sudo apt-get install libdvdread4
```Finally, run this script

```
/usr/share/doc/libdvdread4/install-css.sh
```

EDIT: [here ]("https://help.ubuntu.com/community/RestrictedFormats")is the official how-to link

---

### Post by perspectoff on 2011-01-03
Try giving it a Scooby snack. 

If that doesn't work, try 2 Scooby snacks.

Ok, I'll log off now. I sense a "Notification" coming down the pike.

---

### Post by West201 on 2011-01-03
Add Medibuntu to your Repositories by visiting the following link

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Then sudo apt-get install libdvdcss2

---

