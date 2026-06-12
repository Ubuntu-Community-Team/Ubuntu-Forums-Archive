---
title: "I seriously f***** up!"
date: 2011-05-11
forum: General Help
---

### Post by geraldbrent on 2011-05-11
I was messing around with compiz (it was messing with teamviewer) and accedentally f'ed up unity, now I have no launcher, or status/toolbars. What the crap do I have to do to fix it? 


P.S. I cannot launch anything (apart from making shortcuts) alt + F2 doesn't work.

---

### Post by garvinrick4 on 2011-05-11
Then hit Alt/F2 and type in gnome-terminal hit enter: Sorry hit ctrl/alt/F1 and run code then hit ctrl/alt/F7 to get back to GUI
```
unity --reset
```See what that does for you.

---

### Post by garvinrick4 on 2011-05-11
[B][U]Here is a nice link for you
[/U][/B][Ubuntu for Beginners! Tutorials, News, Reviews and Troubleshooting: Enable Desktop Cube in Unity, Ubuntu Natty]("http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html") 
**_ Reset Compiz_**

The following command will reset all the settings for Compiz. You can run it from a Terminal if available, or a tty.

```
gconftool-2 --recursive-unset /apps/compiz
```Thanks to Anonymous and ubuntu-geek for the tip.

_**Reset Unity**_

Reset all the configuration for Unity by running this command in tty1.

```
unity --reset
```

---

### Post by garvinrick4 on 2011-05-11
I seriously goofed up!
That is really good enough do not need the ***** , kind of immature.

---

### Post by geraldbrent on 2011-05-12
Thanks bro, worked perfectly!

---

