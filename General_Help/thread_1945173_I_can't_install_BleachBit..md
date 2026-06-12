---
title: "I can't install BleachBit."
date: 2012-03-22
forum: General Help
---

### Post by Zoaruki on 2012-03-22
If I try to install it from the software center it simply doesn't open. And if I try to open it from gdebi the program tells me that there are missing dependencies (both GUI and shell, using dpkg). It always "hang up" in the part that is processing python-support triggers.
As extra data, yesterday I updated my Python version from 2.6.2 to 2.7.2 as I'm using 10.04.
I hope you can help me. :)

---

### Post by jerrrys on 2012-03-22
[U][open a terminal and enter]("https://help.ubuntu.com/community/UsingTheTerminal"):

sudo apt-get update

sudo apt-get upgrade

sudo apt-get install bleachbit


[/U]

---

### Post by Zoaruki on 2012-03-22
Thank you for your reply. Now it installs correctly but doesn't seem to open :|

---

### Post by Paqman on 2012-03-22
If you open a terminal and use it to launch a program it'll spit out an error messages. So just open a terminal (Ctrl-T) and type:
```
bleachbit
```
Then paste the errors in here between [noparse]```

```[/noparse] tags.

---

### Post by Zoaruki on 2012-03-22
I don't want to complain about that but being a beginner in Linux doesn't make me a beginner in everything else. At least I know how to use the forum, lol.
By the way, this is what I got:
```
Traceback (most recent call last):
  File "/usr/bin/bleachbit", line 31, in <module>
    import pygtk
ImportError: No module named pygtk
```

---

### Post by ron999 on 2012-03-22
Hi
The latest version deb is available at bleachbit website ---> [http://bleachbit.sourceforge.net/]("http://bleachbit.sourceforge.net/")

---

