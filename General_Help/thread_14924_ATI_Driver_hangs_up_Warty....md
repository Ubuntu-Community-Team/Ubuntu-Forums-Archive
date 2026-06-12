---
title: "ATI Driver hangs up Warty..."
date: 2005-02-10
forum: General Help
---

### Post by Pawel on 2005-02-10
Welcome everybody :-)

A have just installed ATI Driver for Radeon 9200 on Warty according these instructions:
[http://xoomer.virgilio.it/flavio.stanchina/debian/fglrx-installer.html](http://xoomer.virgilio.it/flavio.stanchina/debian/fglrx-installer.html)

Everything looks good, except:
- when i want to login as different user on X'windows - usigng GDM - Ubuntu goes out => screen goes black and that's all - i have to restert my machine,

- when i go to concole using for example CTRL+ALT+F2, and i want return to X'window - - it's also hangs up: I can see my Desktop, but i cant' move cursor of my mice, i can't use my keyboard, and on the top of the screen - i can see strange thing - sth. like blur top of the windows of applicacion which is not working.

A can't find any advice for dissolve this problem ..

Best regards and
Enjoy UBUNTU :-)

P.S. Sorry for my English. i'm still learning...
----------------------------------------
My friend say's that i should try to install older version of Ati driver... - where i can find it ? ;)

---

### Post by Pawel on 2005-02-18
Hi!

[http://schemacik.alternatywa.info/pliki/x.png](http://schemacik.alternatywa.info/pliki/x.png) - it's foto of my Desktop - when X'windows goes out  :? 

I have the newest Ati driver (8.10.19), and in kernel module:

Support for AGP - as module, => Intel module
DRM => unchecked(is disabled).

---

### Post by streetbmx on 2005-02-27
Hey, Im glad i found this post, I have the same problem.  Like you said, screen just turns black when i logout or try to switch console and switch back to x. 

My specs are different however: Im running Hoary with xorg 6.8.1 and fglrx 8.8.25 on an ATI 9500 Pro. Please help.

I actually experience the same thing on my gentoo install running the 8.10.19 drivers.

---

### Post by Pawel on 2005-03-26
Hi.

At first - thanks for e-mail, and i'm sorry that i can reply so late  :oops: 

I still can't find solution for these problems (ati driver doesn't work). I'm looking all over the internet:
- at some pages people wrote that for kernel's 2.6.10 and higher - there're some patches for the ati driver. I have tried that - still didn't work.

I also wrote posts on [www.rage3d.com](www.rage3d.com) - but i don't have enough time and wishes to try one more time ;)

Actually i run kernel 2.6.10 and open driver for ATI. See scrennshot ;)

[http://schemacik.alternatywa.info/linux/radeon-kernel.png](http://schemacik.alternatywa.info/linux/radeon-kernel.png)

After recompiling the kernel i changed the XFree86 config file:
Section "Device"
    Driver                              "ATI"(as i remember)

to
Section "Device"
    Driver                              "**radeon**"
--------------------------
It works. But i can't run tv-out  :neutral:

Best Regards
Pawel W.

Sorry for my english  - but i think it's quite cimmunicative (:

---

