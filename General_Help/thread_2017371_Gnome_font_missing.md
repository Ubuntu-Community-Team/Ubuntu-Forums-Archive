---
title: "Gnome font missing"
date: 2012-07-05
forum: General Help
---

### Post by natrixnatrix89 on 2012-07-05
Hi guys.. I don't know what happened, but looks like gnome configuration has changed, and my system font is not found.. so All the dialogs and panels on programs are unreadable, because now i see braces everywhere. And now i can only work by logging into tty1
but I can't work like this..
I attached how my current screenshot looks like..

Could anyone please give me advice, where can i set the system font  back to defaul, or which *.conf to edit or which package to
```
dpkg-reconfigure
``` in order to see everything again.

Thank's in advance

---

### Post by natrixnatrix89 on 2012-07-05
It would be so stupid to re-install operating system only because of this..

---

### Post by msammels on 2012-07-05
What language is your system set to?

---

### Post by natrixnatrix89 on 2012-07-05
> **msammels said:**
> What language is your system set to?
English

---

### Post by natrixnatrix89 on 2012-07-05
Also I have to mention that I'm using ubuntu precise pangolin.

And the problem starts even in the lightdm login screen.
Also there's no difference whether I log in to ubuntu or ubuntu 2d

---

### Post by natrixnatrix89 on 2012-07-05
The problem could be related to pango.

when launching some applications, i noticed the error message "Unable to choose font"

---

### Post by natrixnatrix89 on 2012-07-05
Whew. Finally solved it..

The problem was that I had installed pangocairo from source. and it started causing the problems..
this post helped:
[http://ubuntuforums.org/showpost.php?p=7059332&postcount=3](http://ubuntuforums.org/showpost.php?p=7059332&postcount=3)

---

