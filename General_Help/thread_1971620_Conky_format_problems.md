---
title: "Conky format problems"
date: 2012-05-02
forum: General Help
---

### Post by tgwaste on 2012-05-02
First things first:

System:  Ubuntu 64bit 11.10 running Unity 3D
Conky version: 1.8.1


Issue:

There seems to be an issue with formatting the time but only when it contains hours and minutes.

Heres my test config:

TEXT
${color Tan2}${font Arial:bold:size=10}TIME ${color DarkSlateGray}${hr 2}
${color Tan2}${font Arial:bold:size=8} $alignc ${time %A %d %Y} 
${color Gray}${font Arial:bold:size=25} $alignc ${time %H:%M}
${color Tan2}${font Arial:bold:size=8} $alignc ${time %A %d %Y}
${color Tan2}${font Arial:bold:size=10}${color Tan2}WEATHER ${color DarkSlateGray}${hr 2}${color Gray}


In screenshot #1 youll see a big gap underneath the time to the next item (im displaying weekday info here twice for testing purposes).

If you comment out the time:

#${color Gray}${font Arial:bold:size=25} $alignc ${time %H:%M}

Youll see in screenshot two there is no more gap.

Ive litterally tried everything and googled everything.  Is that one specific thing %H:%M that is cause a problem somehow.

any ideas?


Edit: im mistaken, its actually the size=25 causing the gap.  anything > 10 and it makes a gap.

---

### Post by QIII on 2012-05-02
(A handy reference...

[http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html))

Try adding a negative voffset on the line after the large font clock to close up the space.  Don't give it too big a number or you'll overlap.  Try with say -10 or -20 to see how it moves.  The values are in pixels.

---

### Post by tgwaste on 2012-05-02
> **QIII said:**
> (A handy reference...

[http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html))

Try adding a negative voffset on the line after the large font clock to close up the space.  Don't give it too big a number or you'll overlap.  Try with say -10 or -20 to see how it moves.  The values are in pixels.


That did it.  Thank you so much!

---

