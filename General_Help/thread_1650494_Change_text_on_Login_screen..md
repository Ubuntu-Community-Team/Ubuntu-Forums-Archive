---
title: "Change text on Login screen."
date: 2010-12-21
forum: General Help
---

### Post by nathanrulz30 on 2010-12-21
Hello, I am trying to change the text on the login screen (below the ubuntu logo) where it says Ubuntu. This is so I can replace the word with a random phase/personalise it for who the computer is for with there name etc. Any help would be much appreciated :D

Oh and if this has been posted I'm sorry in advance iv been crawling threw the Internet for hours and these forums for about 20minutes.

---

### Post by matt_symes on 2010-12-21
Hi

This may help (i have not read it myself)

[http://askubuntu.com/questions/10458/how-can-i-use-my-own-image-for-the-boot-splash-screen](http://askubuntu.com/questions/10458/how-can-i-use-my-own-image-for-the-boot-splash-screen)

Kind regards

---

### Post by Verbeck on 2010-12-21
this tool could add a new liine
from a terminal
```

sudo add-apt-repository ppa:gdm2setup/gdm2setup && sudo apt-get update
sudo apt-get install python-gdm2setup

```and run it from system>administration>login screen (GDM2setup)
edit: use 'enable banner' option

---

