---
title: "Problems installing Opera"
date: 2010-06-03
forum: General Help
---

### Post by dewey_daniels on 2010-06-03
Well this whole morning I have been having problems installing opera.It comes in a tar.gz file which I extracted to my desktop.In command prompt I did a [br]>  cd /home/derek/Desktop/opera-10.10-4742.gcc4-shared-qt3.x86_64 
  That then changed the directory. Like all the guides said I did a ./configure command and got this [br]> derek@derek-laptop:~/Desktop/opera-10.10-4742.gcc4-shared-qt3.x86_64$ ./configure
bash: ./configure: No such file or directory
. So one guide said if configure doesn't work than just go right to make so. [br]> derek@derek-laptop:~/Desktop/opera-10.10-4742.gcc4-shared-qt3.x86_64$ make
make: *** No targets specified and no makefile found.  Stop.. 
Please can someone help me to solve this. If you do respond type it out so a five year old could do sense I am sick and tired of the same guide that i always seem to mess up.

---

### Post by dewey_daniels on 2010-06-03
Bump :(

---

### Post by WorMzy on 2010-06-03
Where did you download it from? [http://www.opera.com/browser/download/](http://www.opera.com/browser/download/) gives you a .deb by default. If it's not giving you the .deb option then try following this link:

[URL="http://www.opera.com/download/get.pl?distro=ubuntu&id=32632%2C32629%2C32628&pack=&location=51&thanks=yes&sub=++++"]
Opera 10.10 for Linux x86-64[/URL]


If you're still having problems, then try adding the following to your software sources (System -> Administration -> Software Sources -> Add):
```
Type:          Binary
URI:           http://deb.opera.com/opera/
Distributions: stable
Components:    non-free
```

You should then be able to install Opera from Synaptic, Software Centre, or Terminal.

---

### Post by azertyh on 2010-06-03
hi,
go to [www.opera.com](www.opera.com) and download the .deb. it's easier to install : just double-click the file .deb and follow the instructions.

---

### Post by dewey_daniels on 2010-06-03
Well thanks for that bit of info.But sense I still need help with the tar.gz files could someone explain how to install them

---

### Post by Linuxforall on 2010-06-03
tar.gz files usually have a ./opera file and therefore you need to execute that.

---

### Post by gaussian on 2010-06-03
make and ./configure are for programs that you need to compile. Opera is a (closed-source) binary package. 

What I would recommend is:

1) Open "Software Sources", go to "Other Software" and click on add
2) Put the following line in add:
```

deb http://deb.opera.com/opera/ sid non-free

```
This adds Opera Repositories to your system
3) Go to terminal and give the following command:
```

wget -O - http://deb.opera.com/archive.key | sudo apt-key add -

```
This adds the Opera validation key to your system
4) Go to Synaptic and install Opera from there.


This way you will have an Opera package that is automatically updated (e.g. when the upcoming 10.60 is released).

---

### Post by dewey_daniels on 2010-06-03
If you meant what I think you meant I got this.Also I cant just run .sh files for some reason. Yes they are check to make them executable but then just don't run. 

>  [email]derek@derek-laptop:~/Desktop/opera-10.10-4742.gcc[/email]4-shared-qt3.x86_64$ ./opera
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
usr/lib/opera/opera: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory


---

### Post by WorMzy on 2010-06-03
Just downloaded the tar.gz, and it has a install.sh file. So all you need to do is run ```
sudo ./install.sh
``` while in the Opera folder.

---

### Post by dewey_daniels on 2010-06-03
Well if this simplifies things sense no one understand what I want to do.How do Install tar.gz files such as Assault Cube 1.02

---

### Post by Linuxforall on 2010-06-03
> **dewey_daniels said:**
> If you meant what I think you meant I got this.Also I cant just run .sh files for some reason. Yes they are check to make them executable but then just don't run.

You have to install qt libs, why don't you do this, install the regular deb, that pulls in the necessary qt libs, then remove it and run the tar.gz Opera.

---

### Post by WorMzy on 2010-06-03
You're having the same problem as the creator of this topic was (is?): [http://ubuntuforums.org/showthread.php?t=1500686](http://ubuntuforums.org/showthread.php?t=1500686)

---

### Post by WorMzy on 2010-06-03
> **dewey_daniels said:**
> Well if this simplidies things sense no one understand what I want to do.How do Install tar.gz files such as Assault Cube 1.02

Open a terminal, browse into the extracted directory, run```
ls
``` and see if there's a configure, makefile, install.sh, or something else like that. If there's an INSTALL, or README, then have a look at those to see if they contain any instructions.

---

### Post by dewey_daniels on 2010-06-03
> **WorMzy said:**
> Just downloaded the tar.gz, and it has a install.sh file. So all you need to do is run ```
sudo ./install.sh
``` while in the Opera folder.


Thank you thank you thank.This is what i trying to get at. Thanks again.I guess this is solved but i dont know how to change it.

---

### Post by WorMzy on 2010-06-03
Ah. We got there in the end. :)

To mark as solved, use thread tools as per this screenshot:
[[img]http://www.ubuntu-pics.de/thumb/73229/_all_variants__open_an_gui_based_app_on_x_server_from_tty___ubuntu_forums___mozilla_firefox_103_BQ6HEO.png[/img]](http://www.ubuntu-pics.de/bild/73229/_all_variants__open_an_gui_based_app_on_x_server_from_tty___ubuntu_forums___mozilla_firefox_103_BQ6HEO.png)

---

