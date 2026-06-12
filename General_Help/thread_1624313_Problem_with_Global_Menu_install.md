---
title: "Problem with Global Menu install"
date: 2010-11-17
forum: General Help
---

### Post by dougalkerr on 2010-11-17
I am trying to install the Mac Global Menu for the Mac look alike theme but, get the following error with the Global Menu:
The panel encountered a problem while loading "OAFIID:GNOME_GlobalMenuApplet".

This appears when I right click to 'Add to panel' from the list of apps.

Any ideas folks?
I have followed the advice on the website that has the instructions for making all the Mac theme adjustments but, can't get rid of this message.

Thanks.

---

### Post by io5cml4z on 2010-11-17
Try this:
> deb [http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu](http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu) **VERSION** main
sudo apt-get install gnome-globalmenu
Edit: Oh, I forgot, replace **VERSION** with your Ubuntu install version, e.g. Maverick

---

