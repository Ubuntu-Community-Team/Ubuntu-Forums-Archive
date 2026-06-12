---
title: "Can't run other programs. What am I doing wrong?"
date: 2011-05-25
forum: General Help
---

### Post by Kenc3 on 2011-05-25
I have two books on ubuntu 11.04. I tried to download yWriter5. It sits in my download folder and I cannot open it anywhere. I even have problems finding the download folder sometimes.
I also tried a harder one with a Windows program under Wine. That didn't work either. 
There must be a way that I do not know to make the programs with Ubuntu download buttons work with Ubuntu11.04 on my PC. I am running a dual boot with Vista. 
I am just lost for now with Linux and Ubuntu.

---

### Post by linuxinstalledfromhdd on 2011-05-25
Sounds like are missing some software. You might want to check out a walkthrough to get your applications installed to view ebooks.. like adobe reader.. 

[http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)

---

### Post by Kenc3 on 2011-05-25
I have the ebooks on my kindle which I keep open while I am working at this.
The problem is that I cannot get any of the programs to work. I found yWriter and it said something about the end of the last file doesn't have something to allow it to be opened. I have a list of the files on the screen and one of them is a .exe but when I click on that one it doesn't open and says something is missing.

---

### Post by linuxinstalledfromhdd on 2011-05-25
Why not just install Kindle on Ubuntu?

[http://cinderbox.net/2011/05/13/how-to-install-kindle-for-ubuntu/](http://cinderbox.net/2011/05/13/how-to-install-kindle-for-ubuntu/)

---

### Post by dFlyer on 2011-05-25
> **Kenc3 said:**
> I have the ebooks on my kindle which I keep open while I am working at this.
The problem is that I cannot get any of the programs to work. I found yWriter and it said something about the end of the last file doesn't have something to allow it to be opened. I have a list of the files on the screen and one of them is a .exe but when I click on that one it doesn't open and says something is missing.

The .exe file is a windows file and requires wine to run. as for yWriter it's not in the repositories so is it a .deb file? if so, you will need to install it with sudo dpkg -i full.name.of.file. if during install it fails because of missing lib, try this: sudo apt-get -f install.

---

### Post by wildmanne39 on 2011-05-25
> **Kenc3 said:**
> I have two books on ubuntu 11.04. I tried to download yWriter5. It sits in my download folder and I cannot open it anywhere. I even have problems finding the download folder sometimes.
I also tried a harder one with a Windows program under Wine. That didn't work either. 
There must be a way that I do not know to make the programs with Ubuntu download buttons work with Ubuntu11.04 on my PC. I am running a dual boot with Vista. 
I am just lost for now with Linux and Ubuntu.
Hi, also running programs in wine you need to right click on it and make it executible.

---

### Post by Kenc3 on 2011-05-25
Gary I tried apt-get -i and it said no such command. I tried it with -f and got the same message.
When I try it without the -"letter" It returns No such package.
I am waiting for a copy of the Ubuntu Iso to download now so I can make a USB boot disk. After that I have Write it Now 4 ( a windows program) to download so I can try to run it using wine again. Maybe I did it wrong the last time. It has not asked me what to open it with yet. I choose save but I never know where it waves them.

---

