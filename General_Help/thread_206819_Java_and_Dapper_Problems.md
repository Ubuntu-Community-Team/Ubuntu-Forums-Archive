---
title: "Java and Dapper Problems"
date: 2006-06-30
forum: General Help
---

### Post by cssutto on 2006-06-30
I have been trying for two weeks to get Firefox to find Java, with no luck.

I have tried what I thought was everything.

Java is located here: /usr/java

Downloaded once from Sun's page.  Completely uninstalled by package manager and reinstalled by package manager along with the plugin.

I have also used the commands:
 ~$ sudo  ln -s /usr/java/jre1.5.0/plugin/i386/ns7/libjavaplugin_oji.so 

and

:~$ sudo  ln -s /usr/java/jre1.5.0_07/plugin/ns7/libjavaplugin_oji.so

I always get:

ln: creating symbolic link `./libjavaplugin_oji.so' to `/usr/java/jre1.5.0_07/plugin/ns7/libjavaplugin_oji.so': File exists


I am really getting upset because I have one package to download that has to come from a web site that will not work without Java.

I also am trying to learn something about Cingular Edge and that site will not work without javascript.

So what to try next?

I am considering unstalling Firefox and reinstalling it to see if it is a flaw in my Firefox installation.

Firefox can be a pain when trying to reinstall bookmorks and I have a lot of them, so that really is not appealing although I will try it in the next day or two if I can't work out the problem.

Any suggestions would be appreciated.

CSSJR

---

### Post by jakez on 2006-06-30
from [http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper) :
"sudo apt-get install sun-java5-jre sun-java5-plugin" 
"sudo update-alternatives --config java"
Then choose the option that corresponds to J2SE.
Greetz

---

### Post by cssutto on 2006-06-30
Thank you.

The information is much appreciated, but it did not work.

The command performed as it should, gave me the three choices, but when all said and done, no plugin.

CSSJR

---

### Post by FredB on 2006-07-01
You're typing the wrong sudo ln -s ;) It misses target :)

try something like :
```
sudo ln -s  libjavaplugin.so  /etc/alternatives/mozilla-javaplugin.so
```

---

### Post by cssutto on 2006-07-01
Thanks, but that did not work either.

The last command I tried a few minutes ago was

/usr/lib/mozilla-firefox/plugins$ sudo ln -s /usr/local/java/jre1.5.0_07/plugin/i386/ns7-gcc29

This is by my understanding, according to the instructions on the Sun help page.

CSSJR

---

