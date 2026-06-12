---
title: "Can't find restricted extras"
date: 2010-01-31
forum: General Help
---

### Post by Desterie on 2010-01-31
Just did a fresh install of 9.10 on a friends computer.  Yay for another mind freeing himself from W-----s.  Well I tried to find ubuntu restricted extras in the ubuntu software center and when I click on the package it says not available in the current data.

I tried the old fashioned terminal way and sudo apt-get install ubuntu-restricted-extras  and got back E: Couldn't find package ubuntu-restricted-extras

so finally I try this link  [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)  I clicked on the link on that page for restricted extras and I got an error saying that it could not find package 'ubuntu-restricted-extras'

Where did it go?  Is there a way I can get the restricted extra package off my other computer and install it on my friends?

Any help is much appreciated.

---

### Post by howefield on 2010-01-31
Open a terminal (Applications > Accessories > Terminal) and type

```
sudo apt-get update
```

Enter password when prompted and try again with restricted extras..

---

