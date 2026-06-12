---
title: "file does not exist, but it is right there"
date: 2012-08-10
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2012-08-10
i ran this on my gnome 2 10.04 Desktop with out a hitch, but i try it on my  xfce 4.10 12.04 laptop and i get this error
```
chad@Compaq-Presario-CQ60 ~/Unigine-Heaven-3.0 $ ./heaven 
**./heaven: line 3: ./launcher_x86: No such file or directory**
chad@Compaq-Presario-CQ60 ~/Unigine-Heaven-3.0 $ cat ./heaven 
#!/bin/bash
cd ./bin
./launcher_x86 -config ../data/launcher/launcher.xml
chad@Compaq-Presario-CQ60 ~/Unigine-Heaven-3.0 $ ls ./bin | grep launcher
launcher_x64
launcher_x86
chad@Compaq-Presario-CQ60 ~/Unigine-Heaven-3.0 $ ./bin/launcher_x86 -config ./data/launcher/launcher.xml
**bash: ./bin/launcher_x86: No such file or directory**
chad@Compaq-Presario-CQ60 ~/Unigine-Heaven-3.0 $ ls -l ./bin/launcher_x*
-rwxr-xr-x 1 chad chad 65872 Feb 26 13:11 ./bin/launcher_x64
-rwxr-xr-x 1 chad chad 61280 Feb 26 13:11 ./bin/launcher_x86 
```is this because i don't have the 32bit libraries installed?

---

### Post by pqwoerituytrueiwoq on 2012-08-10
figured out how to fix it :)
patch the launcher script to run the 64bit version if you are using a 64bit os
```
cat ./Unigine-Heaven-3.0/heaven 
#!/bin/bash
cd ./bin
if [ "`uname -m`" == "x86_64" ]; then
    ./launcher_x64 -config ../data/launcher/launcher.xml
else
    ./launcher_x86 -config ../data/launcher/launcher.xml
fi
```

---

