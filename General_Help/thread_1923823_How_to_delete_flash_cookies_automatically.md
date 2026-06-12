---
title: "How to delete flash cookies automatically?"
date: 2012-02-11
forum: General Help
---

### Post by completely new on 2012-02-11
Hello, recently I've set the flash directory on my PC as read-only to disable flash cookies. However, I think it would be better not to disable them completely, but have them deleted every time I close my browser, or, if that's not possible, make a script of some sort that will delete them them automatically for example, every time I start my computer. I'd need this both for ubuntu and windows since I use both systems. Thanks in advance. :)

---

### Post by raja.genupula on 2012-02-11
[http://www.orzeszek.org/blog/2009/08/12/how-to-delete-flash-cookies-conveniently/](http://www.orzeszek.org/blog/2009/08/12/how-to-delete-flash-cookies-conveniently/)

---

### Post by ottosykora on 2012-02-11
Tried the extension 'better privacy' ?

This is in fact meant for this case.

---

### Post by Frogs Hair on 2012-02-11
I use better privacy with Firefox and set it to delete when the browser closes .

---

### Post by completely new on 2012-02-11
I'm aware of the extension, maybe I should've mentioned that I use Opera because Firefox works terrible on my machine and takes forever to load a page, not to mention that it freezes constantly. Any Opera equivalent?

---

### Post by oklokl on 2012-02-11
[COLOR=#FF0000]https://addons.mozilla.org/en-US/firefox/addon/clickclean/

Click&Clean

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=212512&stc=1&d=1328991502[/IMG]





[/COLOR]Button 
chmod a+x
file.sh

[COLOR=#FF0000]#my sh
#!/bin/bash

rm -rf ~/.mozilla/firefox/*.default/Cache/0/*
rm -rf ~/.mozilla/firefox/*.default/Cache/1/*
rm -rf ~/.mozilla/firefox/*.default/Cache/2/*
rm -rf ~/.mozilla/firefox/*.default/Cache/3/*
rm -rf ~/.mozilla/firefox/*.default/Cache/4/*
rm -rf ~/.mozilla/firefox/*.default/Cache/5/*
rm -rf ~/.mozilla/firefox/*.default/Cache/6/*
rm -rf ~/.mozilla/firefox/*.default/Cache/7/*
rm -rf ~/.mozilla/firefox/*.default/Cache/8/*
rm -rf ~/.mozilla/firefox/*.default/Cache/9/*
rm -rf ~/.mozilla/firefox/*.default/Cache/A/*
rm -rf ~/.mozilla/firefox/*.default/Cache/B/*
rm -rf ~/.mozilla/firefox/*.default/Cache/C/*
rm -rf ~/.mozilla/firefox/*.default/Cache/D/*
rm -rf ~/.mozilla/firefox/*.default/Cache/E/*
rm -rf ~/.mozilla/firefox/*.default/Cache/F/*
[/COLOR]

---

