---
title: "Anyone know when packages.debian.org will be back up?"
date: 2006-02-12
forum: General Help
---

### Post by BitTorrentBuddha on 2006-02-12
I need to get the xlibmesa-glu-dev package for a game. And using forum search I can see it's been down over 4 weeks...

---

### Post by BitTorrentBuddha on 2006-02-12
OK, I found xlibmesa-glu-dev [here](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fx%2Fxorg%2Fxlibmesa-glu-dev_6.8.2-10.1_i386.deb&md5sum=e16b6d703c99380ee4c653b7d6af3841&arch=i386&type=security) but when I try sudo dpkg -i on it it lists all the dependencies, seeing as these aren't found through apt-get, is there a way I can install all dependencies for this with one fell swoop or do I have to go hunt down every package off the internet?

---

### Post by joft on 2006-02-12
Hi,

I don't know when it will be back, but in the meantime you could try to download it from a repository mirror directly - instead of doing it through the packages.debian.org interface, e.g.:

[ftp://ftp.debian.de/debian/pool/main/x/xfree86/](ftp://ftp.debian.de/debian/pool/main/x/xfree86/)

---

### Post by joft on 2006-02-12
[QUOTE=BitTorrentBuddha]OK, I found xlibmesa-glu-dev [here](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fx%2Fxorg%2Fxlibmesa-glu-dev_6.8.2-10.1_i386.deb&md5sum=e16b6d703c99380ee4c653b7d6af3841&arch=i386&type=security) but when I try sudo dpkg -i on in it reads the error ```
dpkg: error processing xlibmesa-glu-dev_6.8.2-10.1_i386 (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 xlibmesa-glu-dev_6.8.2-10.1_i386
``` how can I fix this?[/QUOTE]

Well, as you can see dpkg couldn't find the file ... Are you sure you are in the directory where you put the file when doing sudo dpkg -i ?

---

### Post by Hellscradle on 2006-02-12
at the link you posted just download the file. Then for all the sudo apt-get blahblah.dev blah for ps just leave out the xlibmesa-glu-dev line, it should compile anyways because you technically already have that lib =)

---

### Post by BitTorrentBuddha on 2006-02-12
I fixed that, I forgot to put *.deb lol, but now I need to know where I can get the rest of the dependencies, is there a simpler way than hunting them down?

---

### Post by Hellscradle on 2006-02-12
sudo apt-get install bison-1.35 flex-old libmng-dev libmikmod2-dev libogg-dev 
        libvorbis-dev zlib1g-dev libpng3-dev libjpeg62-dev **xlibmesa-glu-dev**python2.3-dev autoconf automake1.8 libcurl3-dev jam

the bold is the only thing that wouldn't run...the other packages should work just fine, they did for me

to make this compile, download the xlibmesa-glu-dev seperately and just put this into the terminal

sudo apt-get install bison-1.35 flex-old libmng-dev libmikmod2-dev libogg-dev 
        libvorbis-dev zlib1g-dev libpng3-dev libjpeg62-dev python2.3-dev autoconf automake1.8 libcurl3-dev jam

---

