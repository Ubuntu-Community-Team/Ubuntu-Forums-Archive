---
title: "Flash player"
date: 2010-03-28
forum: General Help
---

### Post by xredan on 2010-03-28
When I go on YouTube kongregate or any other site that uses flash, the flash player only semi works on YouTube i can watch videos but i cant pause fast forward rewind or press any of the other buttons. On kongregate it's a hit or miss with flash games. The games will load but i cant click the buttons on some games. :(

please help if you can thanks to anyone who replies

---

### Post by guroot on 2010-03-28
I do not have this problem with my ubuntu installation. Do you use the official Flash pluggin from adobe.com ???

---

### Post by n0dix on 2010-03-28
Is this problem happen with Firefox too?

---

### Post by kvarley on 2010-03-28
Hit Alt + F2 and type:

> metacity --replace

---

### Post by ron999 on 2010-03-28
```
Hit Alt + F2 and type:

Quote:
metacity --replace
```

What kind of numpty is gonna do that without an explanation?

---

### Post by Blackmag+c on 2010-03-28
May i suggest searching for a program called **Gnash** in the software center? It may not be compatible with your browser.

It's what I did when I ran into problems with flash player. It seemed to work a treat for me personally. This is if you are running Firefox or Konqueror. Chrome I have no idea on.

good luck

---

### Post by MichaelSammels on 2010-03-28
Not sure how you installed Flash, but I did it by going to [http://adobe.com/flashplayer](http://adobe.com/flashplayer) and then selecting the .deb file. Try reinstalling as well. Gnash is also a good suggestion.

---

### Post by xredan on 2010-03-31
I used the software center to install the plugin but i will try reinstalling it from adobe.com

---

### Post by crazy dave on 2010-04-06
I had the same problem and solved it but I'm using the 64bit version of Ubuntu, if you're using 64bit let me know and I'll tell you the workaround.

---

### Post by slakkie on 2010-04-06
The versions of the official flashplayer in the repo's is the same as from the Adobe website:

```

apt-cache policy adobe-flashplugin
adobe-flashplugin:
  Installed: (none)
  Candidate: 10.0.45.2-1
  Version table:
     10.0.45.2-1karmic1 0
        300 http://archive.canonical.com karmic/partner Packages
     10.0.45.2-1jaunty1 0
       -100 http://archive.canonical.com jaunty/partner Packages
     10.0.45.2-1intrepid1 0
        300 http://archive.canonical.com intrepid/partner Packages
     10.0.45.2-1 0
        990 http://archive.canonical.com hardy/partner Packages
     10.0.32.18-1karmic2 0
        300 http://archive.canonical.com lucid/partner Packages

extract install_flash_player_10_linux.deb
x - debian-binary
x - control.tar.gz
x - data.tar.gz

extract control.tar.gz
./
./postinst
./prerm
./md5sums
./control

cat ./control
Package: adobe-flashplugin
Version: 10.0.45.2-1

```

Just make sure you have the partner repo enabled, install adobe-flashplugin and you are good to go.

---

