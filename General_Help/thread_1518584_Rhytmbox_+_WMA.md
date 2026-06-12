---
title: "Rhytmbox + WMA?"
date: 2010-06-26
forum: General Help
---

### Post by WannabeFantasma on 2010-06-26
Is it normal that my Rhytmbox doesn't import WMA files?

I thought it was possible in 9.10 and here on my 10.04 it doesn't work?

Does that mean I need to find myself another Music Player? :(

---

### Post by Leppie on 2010-06-26
did you install the windows codecs from the medibuntu repo first?

to add the medibuntu repo and gpg key:
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

to install the windows codecs for x86:
```
sudo apt-get install w32codecs
```
or for x64:
```
sudo apt-get install w64codecs
```

more info here: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by WannabeFantasma on 2010-06-28
mm weird still not working... 
Might check out link better when i have more time...

Just found out, there ARE WMA files in my Rhytmbox, but most of them are not? :s

---

