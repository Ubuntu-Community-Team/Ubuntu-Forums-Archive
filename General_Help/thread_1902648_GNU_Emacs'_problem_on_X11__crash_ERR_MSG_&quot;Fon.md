---
title: "GNU Emacs' problem on X11 : crash ERR_MSG &quot;Font `Ubuntu Mono 13' is not defined&quot;"
date: 2011-12-31
forum: General Help
---

### Post by joanluc on 2011-12-31
I got an GNU Emacs' problem, it can't work  on X11 and crashes with a  message "Font `Ubuntu Mono 13' is not defined" but it works fine without  X, more Xemacs can run without problem, GNU Emacs is a version 23.2.1  and Xemacs is a [version 21.4.22; August 2010]

I saw on another forum  post it could be related with a missign  "ttf-ubuntu-font-family" or some error in .emacs file or  .emacs.d/ folder but my problem is not related with  these  "ttf-ubuntu-font-family" as they are installed and it makes no  help then  i have no .emacs file and .emacs.d/ folder is empty.
 I saw also on emacs' man that it looks for fonts in /usr/lib/X11/fonts and that folder didn't exist but i made a link between  /usr/share/fonts/X11 and /usr/lib/X11/fonts and that made no help.

The  problem seems to be related with my user's profile cause it works fine  with an other user's profile on the same system (the .emacs.d/ folder on  that account is the same than mine.

Does anybody have some ideas ?

---

### Post by ehodzic on 2012-01-06
I had the same problem. Removing X resources worked around it. In particular, there is an Emacs related X resource setting shown on "xrdb -query" output:

Emacs.FontBackend:	x

An "xrdb -remove" worked around the immediate problem, but not sure what's the real issue. Perhaps some fonts missing...

Dino

---

