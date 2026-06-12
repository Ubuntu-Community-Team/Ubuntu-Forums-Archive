---
title: "How to install java"
date: 2005-02-06
forum: General Help
---

### Post by audiored on 2005-02-06
I've searched through the forums to learn how to install java.

this is the procedure i followed:

sudo chmod a+x jre-1_5_0_01-linux-i586.bin
./jre-1_5_0_01-linux-i586.bin
sudo mv jre-1.5.0_01/usr/local/
cd /usr/lib/mozilla-firefox/plugins
sudo ln -s /user/local/jre1.5.0_01/plugin/i386/ns7-gcc29/libjavaplugin_oji.so libjavaplugin_oji.so libjavaplugin_oji.so

and i've installed the shortcut plugin from both ns7-gcc29 and ns7 folders and i've installed it in /usr/lib/mozilla/plugins as well
nothing seems to work. i still can't get java to work in firefox.

what am i doing wrong?

thanks,
jason

sorry i saw the sticky to not post questions here after i already posted.. i apologize.

---

### Post by wulf on 2005-02-06
I'm sure I didn't do all that to get Java working - I think I just added an extra repository that let me install Sun Java 1.5 (because I wanted to get Freemind working) and Firefox support just "happened". How did you install Java in the first place?

Wulf

---

### Post by audiored on 2005-02-06
i downloaded it from [www.java.com](www.java.com)

---

### Post by panabar on 2005-02-07
[QUOTE=wulf]I'm sure I didn't do all that to get Java working - I think I just added an extra repository that let me install Sun Java 1.5 (because I wanted to get Freemind working) and Firefox support just "happened". How did you install Java in the first place?

Wulf[/QUOTE]
 make sure that when you enter "java" on a terminal your system runs /usr/local/"javadirectory"/bin/java if it does not you should create a sym link and put it somewhere in your path (for example /usr/bin/)

you have to create a sym link for java_wm too

---

### Post by macewan on 2005-02-07
[http://www.ubuntulinux.org/wiki/Java15](http://www.ubuntulinux.org/wiki/Java15)

---

### Post by rudiz on 2005-02-11
[http://ubuntuguide.org](http://ubuntuguide.org)

---

### Post by alof8k on 2005-02-11
[QUOTE=audiored]I've searched through the forums to learn how to install java.

this is the procedure i followed:

sudo chmod a+x jre-1_5_0_01-linux-i586.bin
./jre-1_5_0_01-linux-i586.bin
sudo mv jre-1.5.0_01/usr/local/
cd /usr/lib/mozilla-firefox/plugins
sudo ln -s /user/local/jre1.5.0_01/plugin/i386/ns7-gcc29/libjavaplugin_oji.so libjavaplugin_oji.so libjavaplugin_oji.so

and i've installed the shortcut plugin from both ns7-gcc29 and ns7 folders and i've installed it in /usr/lib/mozilla/plugins as well
nothing seems to work. i still can't get java to work in firefox.

what am i doing wrong?

thanks,
jason

sorry i saw the sticky to not post questions here after i already posted.. i apologize.[/QUOTE]
 try ubuntuguide.org as mentioned by rudiz.  it'll get you up and running with java in minutes.

---

