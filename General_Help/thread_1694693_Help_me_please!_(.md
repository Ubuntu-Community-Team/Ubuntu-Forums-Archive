---
title: "Help me please! (:"
date: 2011-02-24
forum: General Help
---

### Post by Haylinux on 2011-02-24
Hello, fellow ubuntu/linux users.
I switched to ubuntu around two months ago, and i'm loving it, everything i could need and MORE in an OS.
I've just recently stumbled upon a problem;
i tried to add Playdeb.Net's source URL and this came up on my Update Manager window;
"Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed line 62 in source list /etc/apt/sources.list (dist parse)'"
Help, Please?

---

### Post by Foxheadz on 2011-02-24
How exactly did you add the source?

---

### Post by Krytarik on 2011-02-24
Then just open the file with the text editor and remove the respective line:
```
gksudo gedit /etc/apt/sources.list
```
Then add the repo again (if I found the right one):
[http://www.playdeb.net/updates/ubuntu/10.04/](http://www.playdeb.net/updates/ubuntu/10.04/)

---

### Post by Haylinux on 2011-02-24
> **Foxheadz said:**
> How exactly did you add the source?

Went in Ubuntu Software Center And Edit>Software Sources>Other Software>Add...
And put in "deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) maverick-getdeb games"
And all of a sudden, KABLAM! this problem

---

### Post by Haylinux on 2011-02-24
> **Krytarik said:**
> Then just open the file with the text editor and remove the respective line:
```
gksudo gedit /etc/apt/sources.list
```
Then add the repo again (if I found the right one):
[http://www.playdeb.net/updates/ubuntu/10.04/](http://www.playdeb.net/updates/ubuntu/10.04/)

i have ubuntu 10.10

---

### Post by Haylinux on 2011-02-24
> **Krytarik said:**
> Then just open the file with the text editor and remove the respective line:
```
gksudo gedit /etc/apt/sources.list
```
Then add the repo again (if I found the right one):
[http://www.playdeb.net/updates/ubuntu/10.04/](http://www.playdeb.net/updates/ubuntu/10.04/)
These are my sources.

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
# deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) maverick-getdeb games
# deb-src [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) maverick-getdeb games
# deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) maverick-getdeb
# deb-src [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) maverick-getdeb

My problem is still occurring.

---

### Post by Krytarik on 2011-02-24
> **Haylinux said:**
> i have ubuntu 10.10
Ah, then it wasn't the "Games" section, fairly near though! ;-)

What is in "line 62" then? Could you attach the file please!?

---

### Post by Haylinux on 2011-02-24
> **Krytarik said:**
> Ah, then it wasn't the "Games" section, fairly near though! ;-)

What is in "line 62" then? Could you attach the file please!?

Fixed!
Thanks for the command line!

---

### Post by Krytarik on 2011-02-24
> **Haylinux said:**
> What file.
Sorry, total nub at this in-depth stuff.
This one:
> **Haylinux said:**
> 
'E:Malformed line 62 in source list /etc/apt/sources.list (dist parse)'


---

