---
title: "Security for your Ubuntu box"
date: 2006-03-08
forum: General Help
---

### Post by magnusbb on 2006-03-08
Today, I found a very good guide to security on a modern Linux Workstation. Some of the tips, may not be appropriate to all, but I would recommend reading it.

[http://aymanh.com/tips-to-secure-linux-workstation](http://aymanh.com/tips-to-secure-linux-workstation)

---

### Post by kaamos on 2006-03-08
I yesterday had a "big red button" experince with that article. The author has written a "WARNING: do NOT run.." about the fork bomb. So of course I just **had** to run the code. :D System came crashing down..

---

### Post by magnusbb on 2006-03-08
Yes! I have tried the same, and I have never seen my Linux system acting like that before - except in some hardware-lockups. But I wasn't aware that a few characters could kill my computer instantly.

Everyone should try it, if they want to see how easily you can crash your system:

Open a terminal and type (but you are [COLOR="Red"]warned[/COLOR])
:(){ :|:& }; :

Followed by the deadly ENTER, and say good night to your system. There is a fix for this, in the article.

---

### Post by Mr Green on 2006-03-08
[QUOTE=magnusbb]Open a terminal and type (but you are [COLOR="Red"]warned[/COLOR])
:(){ :|:& }; :
[/QUOTE]

Now how do I get those smileys into a terminal ;)

---

### Post by nocturn on 2006-03-14
I just ran this against my SuSE system at work, which had the limits set to 4091 by default.

It is still up, but not responsive enough to run a kill command yet (after 15 minutes).

I have already put the limits on my home Ubuntu box!

---

### Post by JimS on 2006-03-14
...

Mr Green,

Goto the link provided by magnusbb above
and you will find the keystrokes for the smileys.

[COLOR="Red"]JimS[/COLOR]
[COLOR="Blue"]Prostate Cancer Aware[/COLOR]

,,,

---

