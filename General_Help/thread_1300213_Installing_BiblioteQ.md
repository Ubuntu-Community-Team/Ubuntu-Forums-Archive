---
title: "Installing BiblioteQ"
date: 2009-10-24
forum: General Help
---

### Post by Cthulhu_Dreams on 2009-10-24
All right, I'm irritated out of my mind.  I'm trying to install BiblioteQ.  Naturally its not .deb nor can it be compiled according to the usual make file thing (as far as I can tell) it came with instructions which I tried to follow - but still I can't get the damned thing to start. Nothing happens when I run the script manually and when I run it through the terminal the bash doesn't like it.

I read the instructions which are ******* useless to anyone who isn't an expert already.

[http://biblioteq.sourceforge.net/](http://biblioteq.sourceforge.net/)

---

### Post by P4man on 2009-10-25
are you getting any errors? What have you tried ?

---

### Post by Cthulhu_Dreams on 2009-10-25
I just can't make sense of the whole damned thing. 

I'm fairly sure I installed the dependencies correctly, but the instructions don't make any sense in relation to the source:

                                 [LEFT]Once the aforementioned dependencies have been resolved, please complete the following operations:[/LEFT]
 
[LIST=1]
[*][LEFT]Create     the /usr/local/biblioteq directory.[/LEFT]
[*][LEFT]Copy     the BiblioteQ executable to /usr/local/biblioteq.[/LEFT]
[*][LEFT]Copy     the icons.d directory to /usr/local/biblioteq.[/LEFT]
[*][LEFT]Create     the /usr/local/biblioteq/translations.d directory.[/LEFT]
[*][LEFT]Copy     the translations.d/*.qm files to     /usr/local/biblioteq/translations.d.[/LEFT]
[*][LEFT]Copy     the biblioteq.conf file to /usr/local/share.[/LEFT]
[*][LEFT]Copy     the biblioteq.sh script to /usr/local/bin.[/LEFT]
[/LIST]
 Particularly line c.  There is no configure file, there is no make file.  Attempting to make BiblioteQ produces "make: *** No rule to make target `BiblioteQ'.  Stop."  While you can make the file "biblioteq"  the contents of the file are confusing.

```
#!/bin/sh

ostype="`uname -s`"

if [ $ostype = "Darwin" ]
then
    open /Applications/BiblioteQ.d/BiblioteQ.app &
else
    cd /usr/local/biblioteq
    ./BiblioteQ &
fi

exit 0
```There IS no BiblioteQ file!  Its not in the sources, its nothing I can seem to make, so I fail to see how this script could run properly; muchless complete step C and run the damn program.

Am I just being retarded? Have I missed something obvious?

**I'd really appreciate it if someone else tried to install this program. I think it would be a lot easier to see if something is wrong with the source if someone is looking at the same things I am.**

---

### Post by P4man on 2009-10-25
I downloaded the tarball and had a look, and im as stumped as you. It doesnt look complete. Their support pages are a laugh too. Im not sure what you intend to do with the app, but it doesnt look promising. If you want to just try it out, might do something silly as running the .exe under wine?

---

### Post by Cthulhu_Dreams on 2009-10-25
I can't get to the correct computer to test this out, so maybe you can.  Hopefully it works.

> Hi,

The tar file does not contain a binary release as there are
too many Linux distributions.

In order to compile BiblioteQ, you'll need Qt 4.4.3 (or
greater) with PostgreSQL and SQLite support, and YAZ.

Assuming you have Qt installed and your environment is
properly configured, run qmake -o Makefile biblioteq.pro &&
make.

Thank you for the questions. This suggests the doc.d
director should include more information. :o)

What distributions are you using?

Assuming that makes it work, hopefully someone also having this problem will be able to refer to this in the future.

---

### Post by Cthulhu_Dreams on 2009-10-25
I tested it out, was able to make one of the files, but when when I did make BiblioteQ I got the following:

```
I'm using Ubuntu (Hardy Heron).  I was able to do the qmake step, but when I tried to do the "sudo make BiblioteQ" I got the following output:

/usr/local/biblioteq$ sudo make BiblioteQ
g++ -c -pipe -fpermissive -Wall -Werror -Werror -Wall -W -D_REENTRANT -DQT_SHARED -DCONFIGFILE='"/usr/local/share/biblioteq.conf"' -DQT_NO_DEBUG -DQT_SQL_LIB -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -I../../share/qt4/mkspecs/linux-g++ -I. -I../../include/qt4/QtCore -I../../include/qt4/QtCore -I../../include/qt4/QtNetwork -I../../include/qt4/QtNetwork -I../../include/qt4/QtGui -I../../include/qt4/QtGui -I../../include/qt4/QtSql -I../../include/qt4/QtSql -I../../include/qt4 -Iinclude.d -I../include -I/usr/X11R6/include -I. -Iinclude.d -o qtbook.o qtbook.cc
In file included from include.d/qtbook_book.h:25,
                 from include.d/qtbook.h:46,
                 from qtbook.cc:48:
include.d/generic_thread.h:18:22: error: yaz/zoom.h: No such file or directory
qtbook.cc: In member function ‘void qtbook::slotSelectDatabaseFile()’:
qtbook.cc:8630: error: ‘class QFileDialog’ has no member named ‘setNameFilter’
make: *** [qtbook.o] Error 1

```

Any ideas?

---

### Post by P4man on 2009-10-26
Do you have yaz installed? If not install it first

```
sudo apt-get install yaz
```
May also need libyazpp3-dev and/or libyaz3-dev.
Cant test it here now im afraid

---

### Post by Cthulhu_Dreams on 2009-10-26
Yeah I had yaz installed, he told me to setup the dev files too. It didn't work, but unforunately I'm not at the computer so I can't show you the output.  I actually think it may have something to do with QT.  I searched for it in synaptic but I'm not sure I got the correct version.  Can anyone tell me what version is the repos?  Since I was able to run qmake I assume I atleast got the packages right....

---

### Post by jaccall on 2010-05-12
I managed to compile successfully once I installed libyazpp3-dev and libyaz3-dev.

Thanks for your advice!

--
Lou S

---

### Post by 311005901 on 2010-05-20
I'm glad you got it working!

If you are able to, can you please make a .deb of this? :popcorn:

I'd like to install it at a local high school.

---

