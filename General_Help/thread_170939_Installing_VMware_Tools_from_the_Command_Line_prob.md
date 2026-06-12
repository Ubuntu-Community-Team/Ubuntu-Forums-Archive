---
title: "Installing VMware Tools from the Command Line problem?"
date: 2006-05-05
forum: General Help
---

### Post by jacatone on 2006-05-05
'm trying to install the VMware Tools into a guest install of Kubuntu. In order to do this I need to get to root, but I keep getting an authentication error. Could someone tell me what I'm doing wrong? Below is a copy of my screen. Thanks.


[http://i70.photobucket.com/albums/i86/jacatone/0012.jpg](http://i70.photobucket.com/albums/i86/jacatone/0012.jpg)

---

### Post by 5-HT on 2006-05-05
Try *sudo -i *to simulate a root login shell.
The root account is locked by default, which is why *su* isn't working for you.
This wiki page explains the matter: [Ubuntu Wiki- RootSudo]("https://wiki.ubuntu.com/RootSudo")

Hope that helps.

---

