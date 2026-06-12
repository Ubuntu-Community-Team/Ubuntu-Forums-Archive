---
title: "is there conf file for 'connect to server'?"
date: 2009-11-21
forum: General Help
---

### Post by ant2ne on 2009-11-21
Click 'Places', and then 'connect to server' and the 'connect to server' dialogue opens. You can then fill out the info and bookmark it, which is cool. I'm wondering if there is a conf file for the data entered into 'connect to server' that I can copy and distribute to multiple clients. And where might I find that conf file.

---

### Post by hwttdz on 2009-11-21
I believe it's added as a line to ~/.gtk-bookmarks , you could add a line to that file on each machine, or make a script to edit that file.  

Such as 
cat ~/.gtk-bookmarks line_to_add.txt >> .gtk-bookmarks.bak
mv .gtk-bookmarks.back .gtk-bookmarks

I'm sure you'll figure something out.

---

