---
title: "How doe i get Banshee working."
date: 2009-09-03
forum: General Help
---

### Post by Kello125 on 2009-09-03
i would appreciate some help. I have done nothing and added nothing.
Last time i started with out gaining council it was a mess.

---

### Post by blueridgedog on 2009-09-03
Banshee should work fine, but you may need to install the restricted codecs:

In a terminal:

```
sudo apt-get install ubuntu-restricted-extras
```

Also, to get a few other things working, as documented at: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
sudo apt-get update
sudo apt-get install medibuntu-keyring
sudo apt-get update
sudo apt-get install libdvdcss2
sudo apt-get install w32codecs
```

---

