---
title: "export GDK_NATIVE_WINDOWS=true problem"
date: 2009-11-05
forum: General Help
---

### Post by Andy54321 on 2009-11-05
Hi,

I have recently become a user of Ubuntu Karmic Koala 64 bit. Encountering problem with buttons cannot be pressed in Eclipse, I read that setting GDK_NATIVE_WINDOWS=true helps. Indeed it does, but only when I do it manually in terminal (right before calling eclipse).

Though I'd like to use this workaround for all java applications. So, tried adding "export GDK_NATIVE_WINDOWS=true" to bash.bashrc and $HOME/.profile but it did not work. The variable was set to "true" and was visible by "printenv GDK_NATIVE_WINDOWS" as I expected, but Eclipse had got back to that issue with unpressable buttons.

How do set the variable globally in script, so that the workaround would work for every java application?

(Sorry, this is my first post in this forum, I was not sure where to put my thread)

---

### Post by Roti78 on 2009-11-06
Hi!

 I had trouble with opera-flash on amd64.
For me it helped that I added this to /usr/bin/opera
```
export GDK_NATIVE_WINDOWS=1 
```


Roti

---

### Post by Andy54321 on 2009-11-07
Thanks.
I also think this is too weird to get fixed, so I edited firefox.sh the same way you did to opera; wrote eclipse.sh with that export only (plus exec the actual eclipse :) ).

Well, although it is not entirely what I wanted, it works.

Hope in some day ubuntu will have both nVidia drivers and GTK more or less stable and without obvious bugs...

---

### Post by stenvoon on 2009-12-16
I've just enountered this problem of buttons not responding in Eclipse 3.5.1 on Karmic 64bit too. Just in case this helps anyone:

I fixed it by renaming the eclipse excutable to runeclipse and then creating an executable script called eclipse:

> 
#!/bin/sh
export GDK_NATIVE_WINDOWS=true
/usr/lib/eclipse/runeclipse


I skimmed the [eclipse bug report]("https://bugs.eclipse.org/bugs/show_bug.cgi?id=287307") and the comments suggest that this'll be fixed in Eclipse 3.5.2

---

### Post by ruario on 2009-12-19
If you are an Opera user and tried the fix and still have problems then read [this]("http://my.opera.com/ruario/blog/flash-problems-on-linux#first-click").

---

