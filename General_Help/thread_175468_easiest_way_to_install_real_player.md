---
title: "easiest way to install real player"
date: 2006-05-13
forum: General Help
---

### Post by 2501 on 2006-05-13
just follow the instructions.....................

----------

1) Download the version of RealPlayer thats prepackaged for Xandros Linux. Its a .deb package that works under Hoary.

[https://helixcommunity.org/download.php/949/RealPlayer-10.0.3-rc1-xandros3.i586.deb.tar.bz2](https://helixcommunity.org/download.php/949/RealPlayer-10.0.3-rc1-xandros3.i586.deb.tar.bz2) 

2) Uncompress the .tar.zp2 file to get realplay_10.0.2-1_i386.deb

3) Open a command line shell and cd into the directory that you saved the deb file, (default is ~/Desktop

4) Use Sudo to install the file: sudo dpkg -i realplay_10.0.3-1_i386.deb



If you have the "kdelibs-data" installed, step 4 will fail due to conflicting files. Whether you want to do this or not, here's a quick workaround which might break things (though judging by the file that is in conflict between both packages, i would say it wont break anything):

4b) sudo dpkg -i --force-overwrite realplay_10.0.3-1_i386.deb

---

### Post by Jussi Kukkonen on 2006-05-16
So how is this easier than *apt-get install realplayer*? It is in multiverse repository for all Ubuntu versions...

EDIT: this is actually a real question, as I have no idea what kind of loops Real makes you jump through when you try installing. Never installed it myself...

---

### Post by oyvindaa on 2006-05-16
Do you get the realplayer itself when using apt-get? I didn't think so..but I might be wrong.

---

### Post by easyease on 2006-05-16
another easier way to have realplayer 10 is to visit klik and get it there with no chance of conflicts.
 [http://klik.atekon.de/popular.htm](http://klik.atekon.de/popular.htm)

---

### Post by easyease on 2006-05-16
To quickly prepare your system for klik, install the klik client: wget klik.atekon.de/client/install -O -|sh  and follow instructions on screen. (K)Ubuntu users, please also run sudo apt-get install binutils libstdc++5 rpm

---

