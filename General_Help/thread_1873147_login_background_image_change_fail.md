---
title: "login background image change fail"
date: 2011-10-31
forum: General Help
---

### Post by JPBodner on 2011-10-31
Hi

I'm trying to change the background image for the login screen.  I updated the appropriate line in /etc/lightdm/unity-greeter.conf as follows:

background=/home/jeff/themes/olho.jpg

but when I logout and login, the background is simply black with white dots.  This file path is fine (isn't it?)

```
jeff@TheMachine:~$ cd /home/jeff/themes
jeff@TheMachine:~/themes$ ls
background.jpeg  blue.png  olho.jpg
 

```

Anyone know why I'm failing miserably at such a simple task?

---

### Post by dmoconnell on 2011-11-01
I had great success by following this guide. save for two things. 1) i logged into root 2) while in root i copied my image into the /usr/share/backgrounds folder. then (while still in root) changed the line about the background and it worked great
heres the link to the OMG Ubuntu article. (if it doesn't work then do the changes i did)
[http://www.omgubuntu.co.uk/2011/09/tool-change-lightdm-wallpaper-ubuntu-11-10/](http://www.omgubuntu.co.uk/2011/09/tool-change-lightdm-wallpaper-ubuntu-11-10/) 

Dm

---

### Post by JPBodner on 2011-11-03
Thanks for the reply.  I see now that the problem is that it is using my background, but the resolution is such that it isn't filling the screen properly. Any way to tell it to stretch/fill the screen?  Or what resolution should it be?

---

### Post by JPBodner on 2011-11-03
Solved.  

I used the simple-light-dm manager to point to an image. Then I went to my home directory and into the hidden folder .simplelightDMManager.  There I changed the permission of the file therein to read only for "others",

---

### Post by Frogs Hair on 2011-11-03
The login settings in Ubuntu Tweak work well for changing the background image and it has been updated for 11.10 .[http://www.noobslab.com/2011/09/install-ubuntu-tweak-on-ubuntu-1110.html](http://www.noobslab.com/2011/09/install-ubuntu-tweak-on-ubuntu-1110.html)

This does not remove the grid lines .

---

