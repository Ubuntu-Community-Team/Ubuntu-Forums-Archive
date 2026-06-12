---
title: "It asks for 'libgtk-1.2.so.0', when I run LDOCE (= Longman Dictionary)"
date: 2012-10-14
forum: General Help
---

### Post by linuxdatabase on 2012-10-14
Guys! I get an error when I try to run the "Longman Dictionary of Contemporary English: LDOCE1; 2005". The error is this:
```
./ldoce4-bin: error while loading shared libraries: libgtk-1.2.so.0:  cannot open shared object file: No such file or directory
```


> Thx that did the job, installed GTK 1.2 and LDOCE started!
As it is mentioned [here]("http://ubuntuforums.org/showpost.php?p=4482780&postcount=5"), how should I install GTK 1.2 on Ubuntu **10.04**?

---

### Post by zombifier25 on 2012-10-14
Sorry, but there's no known way to get those libraries into 10.04. You can install the package from hady, but it **WILL** break your system.
I suggest you use a newer version of the dictionary, one that uses GTK+2 or 3.

---

### Post by ykkfaheem on 2013-02-15
You can try the solution posted here ... [ **[COLOR="DarkOrange"][COLOR="DarkOrange"][COLOR="Orange"][COLOR="Red"]Link[/COLOR][/COLOR][/COLOR][/COLOR]** ]("http://askubuntu.com/a/254162/63322")

---

