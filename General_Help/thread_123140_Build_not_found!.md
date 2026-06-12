---
title: "Build not found!"
date: 2006-01-29
forum: General Help
---

### Post by darkpoet on 2006-01-29
Been trying Ubuntu for a few months now... been quite enjoying the process - until now.  In reference to trying to install drivers for my Eyetoy webcam... but anyways I'm sure I can follow the instructions but it seems I'm getting a serious error on step one... no Build and whereis can't find it either...
```
darkpoet@ubuntu:~/LinuxStuff/ov511-2.29$ make clean
make -C /lib/modules/2.6.12-9-386/build M=/home/darkpoet/LinuxStuff/ov511-2.29 clean
make: *** /lib/modules/2.6.12-9-386/build: No such file or directory.  Stop.
make: *** [clean] Error 2

darkpoet@ubuntu:~/LinuxStuff/ov511-2.29$ whereis build
build:
darkpoet@ubuntu:~/LinuxStuff/ov511-2.29$
```

And before anyone asks, yes I installed 'build-essential' and 'gcc' and whatever else - even tried a re-install - no luck.  I live in Korea and I use MSN to talk to my family back in Canada.  Without the webcam, I'll be forced to use XP more than I want to.  Please help.

---

### Post by GeneralZod on 2006-01-29
Which instructions are you using? Please link to the URL so we can pinpoint where things are going wrong.

---

### Post by darkpoet on 2006-01-29
Sure this is the driver I'm trying to install- [http://alpha.dyndns.org/ov511/](http://alpha.dyndns.org/ov511/) - the instructions are the README in the archive but that seems a little irrelevent.  No 'make' command will work - I always get this error... any subsequent steps result in a .ko file not found error (the .ko file I assume is the compiled driver module).  It's as if the build program itself isn't installed - but perhaps it's just not in the path or it's hidden, I don't know...

---

### Post by mo_x on 2006-01-29
You have to install the linux-headers package:
sudo apt-get linux-headers-`uname -r`
The ov511 module is included in the standard Ubuntu kernel, do you need a newer version?

---

### Post by darkpoet on 2006-01-29
I'm under the impression that the PS2 Eyetoy camera isn't quite compatible with the included drivers... but that was the ticket on make.  I searched and searched and the answer was so simple.  At least I know if I do need to do a 'make' in the future, that I can.  I just successfully did a make - though I had to use Synaptic to get the files first (I dunno why but apt-get couldn't find them)...

I just assumed that if aMsn couldn't recognize my webcam, that it wasn't working correctly...  I did read a bunch of threads on the subject of the Eyetoy and promptly jumped to a conclusion... maybe I oughta test it with another program before installing the modules I linked to above.

---

### Post by darkpoet on 2006-01-29
oh yeah mo_x - thanks!

---

