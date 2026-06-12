---
title: "Runescape: Music but no sound effects"
date: 2011-03-26
forum: General Help
---

### Post by blazemore on 2011-03-26
```

     rory@rory-kubuntu ~ $ uname -a
Linux rory-kubuntu 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 18:42:20 UTC 2011 x86_64 GNU/Linux 
```
```

     rory@rory-kubuntu ~ $ java -version
java version "1.6.0_24"
Java(TM) SE Runtime Environment (build 1.6.0_24-b07)
Java HotSpot(TM) 64-Bit Server VM (build 19.1-b02, mixed mode) 
```
I have /etc/alternatives/java set to use padsp to route sound through pulseaudio. This gives me music, but no sound effects.

Any clues? I remember getting this working before but can't for the life of me remember how I did it.

---

### Post by gylti on 2011-07-03
There is no hope its still same problem after all these years

---

### Post by FrodoUnderhill on 2011-10-23
I got it to work in google chrome by executing 
padsp google-chrome
from a command line.
Make sure ubuntu-restricted-extras is installed as well.

In firefox, you can fix it with a bit of console hacking too...

```
sudo su
mv /usr/bin/java /usr/bin/java.bin
touch /usr/bin/java
chmod +x /usr/bin/java
```

Then open /usr/bin/java in your favorite text editor, and put in the following :

```
#! /bin/bash
padsp java.bin "$@"
```

Works for me, Kubuntu 11.10.  Beware the firefox hack has to be reapplied every time java is updated.  But, seeing as how google finds this thread in the first search result, I wanted to make sure this info was here next time I go looking for it :)

---

