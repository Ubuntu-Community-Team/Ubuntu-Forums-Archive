---
title: "Window 3 Icons (close, min &amp; max) moved to the left !!"
date: 2010-05-01
forum: General Help
---

### Post by Tom_T on 2010-05-01
Hi

just upgraded to 10.04 - everything seems to be working OK apart from the 3 icons (close, min & max) have moved to the top left of the windows.

before they were top right.. How do I sort this ?

Thanks :)

---

### Post by WorMzy on 2010-05-01
There are a number of ways:
1) Change your theme by going to System -> Preferences -> Appearance, and choosing something with a window border that suits you
2) Install a different window manager (I recommend Emerald)
3) Open up gconf-editor and change /apps/metacity/general/button_layout to ":minimize,maximize,close".

---

### Post by Mad dog on 2010-05-01
System > Preferences > Appearance  

Choose a new theme. Enjoy.

---

### Post by jflaker on 2010-05-01
[URL="http://ubuntuforums.org/showthread.php?p=9203080#post9203080"]http://ubuntuforums.org/showthread.php?p=9203080#post9203080

[/URL]

Easy Python script if you are interested

---

### Post by Tom_T on 2010-05-01
Sorted.

In terminal : gconf-editor

goto /apps/metacity/general

change button_layout to:
:minimize,maximize,close

Worked for me :)

---

