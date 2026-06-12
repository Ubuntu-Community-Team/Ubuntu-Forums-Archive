---
title: "Sound bug on 64bit ubuntu"
date: 2010-04-06
forum: General Help
---

### Post by helltone on 2010-04-06
Hi all,

I have a very weird sound bug on 64 bit Ubuntu 9.10 when playing Altitude (a game). If I do ```
pulseaudio --kill; pulseaudio --start
```, sound works again. Any suggestions?

Thanks in advance.

---

### Post by pbrane on 2010-04-06
You could try this:
In a terminal type
```

echo "drivers = oss" > .alsoftrc

```
Note the dot in front of **.alsoftrc**.

And then try the game. This has cured some wierd sound issues for me in some games. I don't think it fixes all types of problems so this may or may not work for you.
Let us know.

---

### Post by helltone on 2010-04-07
I seem to have solved the problem. I have installed all these:

sudo apt-get install libasound2-plugins "pulseaudio-*" paman padevchooser paprefs pavucontrol pavumeter

And also a version of libopenal and libalut from i386 Debian with dpkg --force-architecure.

---

