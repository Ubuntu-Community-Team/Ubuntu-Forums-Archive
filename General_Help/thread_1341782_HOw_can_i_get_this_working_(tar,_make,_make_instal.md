---
title: "HOw can i get this working? (tar, make, make install)"
date: 2009-11-30
forum: General Help
---

### Post by infernowolf36 on 2009-11-30
i'm trying to get rarcrack to work i have a .rar that i forgot the password to. :( 

here's what i get. 

kavik@kavik-desktop:~/Desktop$ tar -xvf rarcrack-0.2.tar.bz2 
rarcrack-0.2/
rarcrack-0.2/CHANGELOG
rarcrack-0.2/LICENSE
rarcrack-0.2/Makefile
rarcrack-0.2/rarcrack.c
rarcrack-0.2/README
rarcrack-0.2/RELEASE_NOTES
rarcrack-0.2/test.rar
rarcrack-0.2/rarcrack.h
rarcrack-0.2/test.zip
rarcrack-0.2/README.html
rarcrack-0.2/test.7z
kavik@kavik-desktop:~/Desktop$ cd rarcrack-0.2/
kavik@kavik-desktop:~/Desktop/rarcrack-0.2$ make
gcc -pthread rarcrack.c `xml2-config --libs --cflags` -O2 -o rarcrack
/bin/sh: xml2-config: not found
In file included from rarcrack.c:21:
rarcrack.h:25:48: error: libxml/xmlmemory.h: No such file or directory
rarcrack.h:26:27: error: libxml/parser.h: No such file or directory
rarcrack.h:27:36: error: libxml/parserInternals.h: No such file or directory
rarcrack.h:28:25: error: libxml/tree.h: No such file or directory
rarcrack.h:29:28: error: libxml/threads.h: No such file or directory
rarcrack.c:30: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘pwdMutex’
rarcrack.c:33: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘status’
rarcrack.c:35: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘finishedMutex’
rarcrack.c: In function ‘savestatus’:
rarcrack.c:46: error: ‘xmlNodePtr’ undeclared (first use in this function)
rarcrack.c:46: error: (Each undeclared identifier is reported only once
rarcrack.c:46: error: for each function it appears in.)
rarcrack.c:46: error: expected ‘;’ before ‘root’
rarcrack.c:47: error: expected ‘;’ before ‘node’
rarcrack.c:48: error: ‘xmlChar’ undeclared (first use in this function)
rarcrack.c:48: error: ‘tmp’ undeclared (first use in this function)
rarcrack.c:49: error: ‘status’ undeclared (first use in this function)
rarcrack.c:50: error: ‘root’ undeclared (first use in this function)
rarcrack.c:52: error: ‘finishedMutex’ undeclared (first use in this function)
rarcrack.c:53: error: ‘node’ undeclared (first use in this function)
rarcrack.c:55: error: ‘pwdMutex’ undeclared (first use in this function)
rarcrack.c:56: error: expected ‘)’ before ‘xmlChar’
rarcrack.c:66: error: expected ‘)’ before ‘xmlChar’
rarcrack.c: In function ‘loadstatus’:
rarcrack.c:87: error: ‘xmlNodePtr’ undeclared (first use in this function)
rarcrack.c:87: error: expected ‘;’ before ‘root’
rarcrack.c:88: error: expected ‘;’ before ‘node’
rarcrack.c:89: error: ‘xmlParserCtxtPtr’ undeclared (first use in this function)
rarcrack.c:89: error: expected ‘;’ before ‘parserctxt’
rarcrack.c:96: error: ‘status’ undeclared (first use in this function)
rarcrack.c:99: error: ‘root’ undeclared (first use in this function)
rarcrack.c:103: error: ‘parserctxt’ undeclared (first use in this function)
rarcrack.c:104: error: ‘node’ undeclared (first use in this function)
rarcrack.c:108: error: ‘XML_SUBSTITUTE_BOTH’ undeclared (first use in this function)
rarcrack.c:108: warning: assignment makes pointer from integer without a cast
rarcrack.c:114: warning: assignment makes pointer from integer without a cast
rarcrack.c:124: warning: assignment makes pointer from integer without a cast
rarcrack.c:127: error: ‘finishedMutex’ undeclared (first use in this function)
rarcrack.c: In function ‘nextpass’:
rarcrack.c:170: error: ‘pwdMutex’ undeclared (first use in this function)
rarcrack.c: In function ‘status_thread’:
rarcrack.c:182: error: ‘finishedMutex’ undeclared (first use in this function)
rarcrack.c:188: error: ‘pwdMutex’ undeclared (first use in this function)
rarcrack.c: In function ‘crack_thread’:
rarcrack.c:206: warning: comparison between pointer and integer
rarcrack.c:208: error: ‘finishedMutex’ undeclared (first use in this function)
rarcrack.c:205: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
rarcrack.c: In function ‘init’:
rarcrack.c:250: error: ‘pwdMutex’ undeclared (first use in this function)
rarcrack.c:251: error: ‘finishedMutex’ undeclared (first use in this function)
rarcrack.c:283: warning: format ‘%s’ expects type ‘char *’, but argument 3 has type ‘char (*)[300]’
rarcrack.c:317: warning: ignoring return value of ‘fscanf’, declared with attribute warn_unused_result
rarcrack.c: In function ‘main’:
rarcrack.c:351: error: ‘status’ undeclared (first use in this function)
rarcrack.c:353: error: ‘pwdMutex’ undeclared (first use in this function)
rarcrack.c:354: error: ‘finishedMutex’ undeclared (first use in this function)
make: *** [all] Error 1
kavik@kavik-desktop:~/Desktop/rarcrack-0.2$ sudo make install
install -s rarcrack /usr/bin
install: cannot stat `rarcrack': No such file or directory
make: *** [install] Error 1


was trying to follow from here: 
[http://ubuntuforums.org/showthread.php?t=846414](http://ubuntuforums.org/showthread.php?t=846414)

can anyone give me some info? i'm using ubuntu 9.10 Koala

---

### Post by Virtual Liberty on 2009-11-30
```
sudo apt-get install libxml2-dev
```

Try again.

---

### Post by infernowolf36 on 2009-11-30
kavik@kavik-desktop:~/Desktop/rarcrack-0.2$ make
gcc -pthread rarcrack.c `xml2-config --libs --cflags` -O2 -o rarcrack
rarcrack.c: In function &#8216;crack_thread&#8217;:
rarcrack.c:206: warning: comparison between pointer and integer
rarcrack.c:205: warning: ignoring return value of &#8216;fgets&#8217;, declared with attribute warn_unused_result
rarcrack.c: In function &#8216;init&#8217;:
rarcrack.c:283: warning: format &#8216;%s&#8217; expects type &#8216;char *&#8217;, but argument 3 has type &#8216;char (*)[300]&#8217;
rarcrack.c:317: warning: ignoring return value of &#8216;fscanf&#8217;, declared with attribute warn_unused_result
kavik@kavik-desktop:~/Desktop/rarcrack-0.2$ sudo make install
install -s rarcrack /usr/bin
mkdir -p /usr/share/doc/rarcrack
chmod 755 /usr/share/doc/rarcrack
install -m 644 -t /usr/share/doc/rarcrack CHANGELOG LICENSE README README.html RELEASE_NOTES


thanks.

---

### Post by abramo.franchetti on 2010-11-16
work fom me, thanks:guitar:

---

