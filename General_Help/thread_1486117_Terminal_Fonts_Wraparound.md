---
title: "Terminal Fonts Wraparound"
date: 2010-05-17
forum: General Help
---

### Post by ehtony110 on 2010-05-17
Hello, I am having an issue concerning the fonts in Konsole.  Directory names and certain filenames appear in a bold font that gets cut off on the right side of each string of text.  This issue only arose after upgrading to 10.04 LTS.  I can not figure out why the upgrade would change the terminal font settings in such a way.  I have a screenshot of the corrupted fonts below to better explain the problem.  Any suggestions would be greatly appreciated!

[IMG]http://imgur.com/M94j3.png[/IMG]

Thanks

---

### Post by Zorael on 2010-05-17
This happens for me too when I use certain fonts, notably not DejaVu Sans Mono (which is what I get herded into using). Tagging thread for interest. Please post here if you file a bug.

---

### Post by ehtony110 on 2010-05-18
Can do.  The bug has already been reported but nothing in the way of solutions or even acknowledgement has occurred yet.  

[https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/544814](https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/544814)

I guess I will go back to wrestling with WINE in the meantime...

---

### Post by zx1986 on 2010-09-06
how to fix it please ? :-(

---

### Post by ccosse on 2010-11-21
I had a similar problem and just fixed it as follows:
System -> Preferences -> Appearance -> Visual Effects -> NONE!

All my garbled font problems in aterm and xterm magically went away!

---

