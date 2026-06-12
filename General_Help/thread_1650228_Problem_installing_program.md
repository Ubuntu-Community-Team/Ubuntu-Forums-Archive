---
title: "Problem installing program"
date: 2010-12-21
forum: General Help
---

### Post by ocky7 on 2010-12-21
Dear all,

I've been trying to install this program through the Ubuntu terminal:
[http://www.labri.fr/perso/moot/grail3.html](http://www.labri.fr/perso/moot/grail3.html)
Following the instructions, it all goes well until I come to the 'make'  command. Here it tries to make some new directories, but fails:
...
mkdir /hoi/share/Grail
mkdir: cannot create directory `/hoi/share/Grail': No such file or directory
...
etc.

I think the command should de mkdir ./hoi/share/Grail, right? So I went and changed the prefix in the Makefile file to have a period in front of it.

But it still comes up with hundreds of errors.

Does anyone have any idea on what to do?

Greetinghs,
Marty

---

### Post by 3Miro on 2010-12-21
/hoi is in Root space. To create anything there you need to use sudo (which should be avoided).

~/hoi or right after staring the terminal ./hoi is in your home folder (/home/your-username).

The second error that you get is about creating multiple levels of folders. Create them one by one:

```
mkdir ~/hoi
mkdir ~/hoi/share
mkdir ~/hoi/share/Grail

```

You can also use the "-p" option:
```
mkdir -p ~/hoi/share/Grail
```

---

