---
title: "mplayer with jack support (success)"
date: 2011-01-03
forum: General Help
---

### Post by buntuyu on 2011-01-03
After MANY YEARS of frustration I finally compiled mplayer with jack support, with these ./configure options:

./configure --enable-gui --enable-jack --extra-libs=" -ljack"

("--enable-gui" is probably not needed, and, of course, make sure you have your "libjack-dev" package installed or locally build jack, etc...)

Because of the long frustration, and seeing other unresolved threads discussing this (in and outside ubuntuforums), I am posting my solution.

(tried to reply to this thread -- [http://ubuntuforums.org/showthread.php?t=393605](http://ubuntuforums.org/showthread.php?t=393605) -- but, apparently, it's too old for replies)

enjoy the integration benefits that this yields! :D

---

