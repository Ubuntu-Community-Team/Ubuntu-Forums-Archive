---
title: "installing a tar program"
date: 2010-06-20
forum: General Help
---

### Post by Catfish Dubois on 2010-06-20
I'm new to linux and am trying to install a program called Slam Soccer 2006 (it's original name is bolzplatz2006).   Anyway, no package is available, so I'm having to install it using the tar.gz file.   I've read all the Documentation that I could find on ubuntu sites, and I think I understand the  extract, configure, make, install process.   However, I keep getting stuck on the ./configure phase.   When I type ./confiure into the command line it keeps telling me that no such command exists.   I tried downloading Kludge Tarball installer so I could have a graphic interface to walk me through the problem.  Everything seems fine until I get to the configure phase and I get the following message:

sh: Can't open configure

(zenity:9078): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Error on line 4 char 128: '.' is not a valid name 

(zenity:9078): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Error on line 4 char 128: '.' is not a valid name 


Does anyone know what could be causing this?

---

### Post by Smart Viking on 2010-06-20
Hi, when you run "./configure", you must be in the files relative path, the means if per example the file "configure" is located on the desktop, you must first run

```
cd /home/<username>/Desktop
```

And then run "./configure".

I think that's what ur doing wrong if i have not misread or misunderstood. :)

---

### Post by Smart Viking on 2010-06-20
I downloaded the game, and the only thing you have to do is to double click this file: "bolzplatz2006.sh", and you might double click "settings.sh" and set the right resolution first.

Another note is that you must have Java installed to play the game. :)

EDIT: You have to extract the game somewhere first, of course.

---

### Post by Pantera91lego on 2010-06-20
Hey, 
I'm trying to install a tar.gz program, but after I have typed "./configure" I get this message:
```
configure: error: see the INSTALL doc for more info
```

May you help me please?
Thank you very much

---

### Post by Smart Viking on 2010-06-20
"tar.gz" is compressed files, so you can't call it a "tar.gz" program(it is a little like ".zip"). How you are gona install it depends on what is in it, unless it is an executable named "configure", you wont achieve anything by running "./configure" because there is no file with that name. 

Hope this helped a little, i also thought tar.gz was a type of program-installer or something when i just had come from windows. :)

---

### Post by nothingspecial on 2010-06-20
> **Pantera91lego said:**
> Hey, 
I'm trying to install a tar.gz program, but after I have typed "./configure" I get this message:
```
configure: error: see the INSTALL doc for more info
```

May you help me please?
Thank you very much

Have a look at the INSTALL doc, like it says. Installation instructions will be there.

---

### Post by Pantera91lego on 2010-06-20
I'm sorry, I wrote a wrong thing. 
I have actually extracted the tar.gz file, so now I have a folder with tens of c files that I should compile. 

I read that i should type ./configure, then make, then checkinstall but it gaves me that error when I type ./configure..

---

### Post by nothingspecial on 2010-06-20
What does the INSTALL file say.

Paste it here.

---

### Post by Pantera91lego on 2010-06-20
It says that I should install libpcap, but when I try to do that it says:

```
configure: error: Your operating system's lex is insufficient to compile
 libpcap.  flex is a lex replacement that has many advantages, including
 being able to compile libpcap.  For more information, see
 http://www.gnu.org/software/flex/flex.html .

```

Of course, when I tried to install Flex..

```

configure: error: GNU M4 1.4 is required

```
I'm downloading GNU M4 1.4 to see if I can solve the problem..
Anyway here is install.txt:

```
@(#) $Header: /tcpdump/master/tcpdump/INSTALL.txt,v 1.2 2008-02-06 10:47:53 guy Exp $ (LBL)

If you have not built libpcap, and your system does not have libpcap
installed, install libpcap first.  Your system might provide a version
of libpcap that can be installed; if so, to compile tcpdump you might
need to install a "developer" version of libpcap as well as the
"run-time" version.  You can also install tcpdump.org's version of
libpcap; see the README file in this directory for the ftp location.

You will need an ANSI C compiler to build tcpdump. The configure script
will abort if your compiler is not ANSI compliant. If this happens, use
the GNU C compiler, available via anonymous ftp:

    ftp://ftp.gnu.org/pub/gnu/gcc/

After libpcap has been built (either install it with "make install" or
make sure both the libpcap and tcpdump source trees are in the same
directory), run ./configure (a shell script).  "configure" will
determine your system attributes and generate an appropriate Makefile
from Makefile.in.  Now build tcpdump by running "make".

If everything builds ok, su and type "make install".  This will install
tcpdump and the manual entry.  Any user will be able to use tcpdump to
read saved captures.  Whether a user will be able to capture traffic
depends on the OS and the configuration of the system; see the tcpdump
man page for details.  DO NOT give untrusted users the ability to
capture traffic.  If a user can capture traffic, he or she could use
utilities such as tcpdump to capture any traffic on your net, including
passwords.

Note that most systems ship tcpdump, but usually an older version.
Remember to remove or rename the installed binary when upgrading.

If your system is not one which we have tested tcpdump on, you may have
to modify the configure script and Makefile.in. Please send us patches
for any modifications you need to make.

Please see "PLATFORMS" for notes about tested platforms.
```

---

### Post by Pantera91lego on 2010-06-20
I have installed flex, but when I try to install libpcap I get this:
```
configure: WARNING: don't have both flex and bison; reverting to lex/yacc
checking for capable lex... insufficient
configure: error: Your operating system's lex is insufficient to compile
 libpcap.  flex is a lex replacement that has many advantages, including
 being able to compile libpcap.  For more information, see
 http://www.gnu.org/software/flex/flex.html .

```

What should I do? :confused: 
tnx

---

### Post by NCLI on 2010-06-20
Install flex like it suggests?

It's in the Software Center.

---

### Post by Catfish Dubois on 2010-06-20
Thanks for the reply.  I can change the settings by clicking on the settings.sh file, but when I click on the bolzplatz.sh file, the screen flickers a couple of times like it is trying to load, but nothing happens.   I have JAVA 6 installed (as far as I can tell--there are 100 packages with some relationship to JAVA that I could install).   Is it likely that the problem that is with my JAVA installation?

---

