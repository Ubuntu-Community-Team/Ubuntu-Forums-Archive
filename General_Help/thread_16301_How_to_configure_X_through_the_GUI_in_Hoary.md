---
title: "How to configure X through the GUI in Hoary?"
date: 2005-02-20
forum: General Help
---

### Post by Imagist on 2005-02-20
I'm completely new to linux, so I may need you to dumb this down a bit for me.  I've successfully installed Linux and X, but I can't configure the screen resolution to correct settings because the only options coming up are 800x600 and 640x480.  I need to set my resolution to 1024x768.  How do I access the Xorg configuration files from the GUI?

---

### Post by matey3 on 2008-02-11
I cant even get X to come up properly?! the res is too low but in any case the file xorg.conf is in /etc/X11/
(in Ubuntu 7x anyways) you can do:
 sudo pico (or nano) /etc/X11/xorg.conf
(I just changed my video drivers fron nvidia to vesa to get it to come up)


Does any1 know what is that little black box (the command line box) on top left of the X , for? how can I get KED or suck to load? All I get is gray screen and mouse ,no icons or start etc..?

---

