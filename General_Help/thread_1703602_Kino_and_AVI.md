---
title: "Kino and AVI"
date: 2011-03-09
forum: General Help
---

### Post by iamgeniusrnti on 2011-03-09
OK, whenever I open an AVI in Kino it only shows a few random frams and skips to the end.

When I use Winff, I can convert it to DV which opens fine in movie player.  But again when Kino takes in the now DV file, it does the exact same thing.

Is there an editor that works with AVI files?  I want to cut and splice videos.

Thanks!

---

### Post by linuxsyst on 2011-03-09
I used [cinelerra]("http://cinelerra.org/") to do it.
You could try [here]("http://www.heroinewarrior.com/cinelerra/cinelerra.html") for a cinerella documentation page.

```
Debian

   [x86]("http://cinelerra.org/getting_cinelerra.php#apt-x86") | [Athlon64]("http://cinelerra.org/getting_cinelerra.php#apt-AMD64") | [PowerPC]("http://cinelerra.org/getting_cinelerra.php#apt-ppc")  

x86 (Intel, AMD, PC compatibles)
   x86 Debian packages are built from SVN by Andraz Tori, and hosted at    [www.kiberpipa.org](www.kiberpipa.org).
  To install the package add this line to your sources list:

  For i386 processors:
  deb [here]("http://www.kiberpipa.org/~minmax/cinelerra/builds/sid/") ./

  For Pentium4 processors:
  deb [here]("http://www.kiberpipa.org/~minmax/cinelerra/builds/pentium4/") ./

  For Athlon processors:
  deb [here]("http://www.kiberpipa.org/~minmax/cinelerra/builds/athlonxp/") ./

   Apt-source:
   deb-src [here]("http://www.kiberpipa.org/~minmax/cinelerra/builds/sid/") ./

  You will need some additional packages not found in Debian's official   repositories, provided by Christian Marillat: 
  deb [http://www.debian-multimedia.org/]("http://www.debian-multimedia.org/") sid main

  In order to use the mirror you need to add in your gpg keyring marillat's gpg-key 
    gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys 1F41B907
   gpg --armor --export 1F41B907 | sudo apt-key add - 

  If you don't use sudo, do the following under root :
  gpg --armor --export 1F41B907 | apt-key add - 
 
 For athlon64 processors
 AMD64 Debian packages are built from SVN by Valentina Messeri. 
To install the package add this line to your sources list: 
  deb [http://giss.tv/~vale/debian64]("http://giss.tv/~vale/debian64") ./

Apt-source:
  deb-src [http://giss.tv/~vale/debian64]("http://giss.tv/~vale/debian64") ./
```

---

### Post by iamgeniusrnti on 2011-03-10
Thx!  Though that software was ind of whacky.  I'll have to dink around with it a little more.

---

