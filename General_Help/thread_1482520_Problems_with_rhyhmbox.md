---
title: "Problems with rhyhmbox"
date: 2010-05-13
forum: General Help
---

### Post by msaleiro on 2010-05-13
Hi all!

Today I decided to reinstall Ubuntu 10.04 on my laptop since the locales got messed up when I upgraded from ubuntu 9.10. However, this time Rhythmbox got messed up. Whenever I play any song from my playlist it only plays one song and then crashes or hangs, or starts showing the CD covers in a separate window, or says that it needs for a plugin "decoder/msword" (msword? wtf?) or it sometimes says that the file that it is trying to play appears to be a text file... I have already installed the ubuntu-restricted-extras package which contains the mp3 drivers. How can i fix it? It seems like Rhythmbox is on crack or something.. please help! Thanks in advance!

---

### Post by mike555 on 2010-05-13
not sure how to fix ,but you might want to try "exaile"

---

### Post by vandorjw on 2010-05-13
that is actually not such a bad idea.

if exaile does the same thing, that means it is not necessarily rhythmbox that is the problem.

---

### Post by chipper_farley on 2010-05-13
This may be oversimplifying but have you tried removing it and the installing again?

sudo apt-get remove rhythmbox

and then after that's done...

sudo apt-get install rhythmbox


It just sounds like the program is hosed.  maybe a reinstall will fix it.

Good luck.

---

### Post by msaleiro on 2010-05-13
Yes, I've tried to reinstall rhythmbox, rhythmbox plugins, ubuntu-restricted-extras, gstreamer.. and nothing changed. I was just trying to keep with rhythmbox because of the script that I use in conky to show the song names and other stuff.. Anyway, I'm currently installing Exaile and I'll give it a try. Thanks for the sugestion btw. 
If anyone has other suggestions on how to fix rhythmbox I'll be grateful!

---

### Post by msaleiro on 2010-05-13
OK guys, thanks a lot and forget Rhythmbox, I'll keep with Exaile. It works, the multimedia keys weren't working but I've already fixed it. Exaile for the win! Thx to all of u

---

