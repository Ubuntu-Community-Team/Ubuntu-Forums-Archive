---
title: "'make' error in evolution remove-duplicates-plugin"
date: 2010-10-23
forum: General Help
---

### Post by RobbyHawkes on 2010-10-23
Hi there. This is my first post, so  I apologise in advance for any accidental breach of etiquette. 

After an awkward upgrade to Maverick Meerkat (netbook version), which ended up being a clean install, I have lost all my plugins. For the most part, I don't care, but I want the remove duplicates plugin in Evolution working again. I downloaded version 0.0.4 from [http://people.gnome.org/~carlosg/stuff/evolution/]("http://people.gnome.org/%7Ecarlosg/stuff/evolution/"), ran ./configure successfully, but when I try to run 'make', I get the following error:

> remove-duplicates.c:23: fatal error: mail/em-popup.h: No such file or directory
compilation terminated.
make[3]: *** [remove-duplicates.lo] Error 1
make[3]: Leaving directory `/home/rob/Downloads/remove-duplicates-plugin-0.0.4/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/rob/Downloads/remove-duplicates-plugin-0.0.4/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/rob/Downloads/remove-duplicates-plugin-0.0.4'
make: *** [all] Error 2The plugin is not very new, so I expect that "mail/em-popup.h" has been deprocated or changed in 10.10, but I don't know, and I don't know how to fix it.

Any help or suggestions would be greatly appreciated.

Thanks!

Rob

---

### Post by apoapo on 2010-11-25
I am very interested in a solution too. anyone?

Same error as thread starter got. evoltuion-dev has to be installed

---

### Post by cabez0n on 2010-12-09
Did you install evolution-dev package before compiling the plugin ?

Did the ./configure turned out ok ?

Marcel

---

### Post by BCtom on 2010-12-16
I'm in the exact same boat. Same error, installed Evolution Dev.... 

Have you managed to compile this?

 I really need this plugin - I can't even use Evolution right now with all the duplicates since I've upgraded. 

:sad:

---

### Post by CO_Shifty on 2011-01-29
Same problem here. The plugin would be useful to me with thousands of duplicates :(.

---

### Post by CO_Shifty on 2011-01-29
I've found the following script that for anybody who has this issue: [http://www.len.ro/2009/01/remove-duplicate-mails/](http://www.len.ro/2009/01/remove-duplicate-mails/)

It did the trick for me.

Shifty

---

