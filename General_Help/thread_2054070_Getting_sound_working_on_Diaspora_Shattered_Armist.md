---
title: "Getting sound working on Diaspora: Shattered Armistice"
date: 2012-09-06
forum: General Help
---

### Post by unperson on 2012-09-06
Yesterday I downloaded the open source game [Diaspora: Shattered Armistice]("http://www.hard-light.net/forums/index.php?topic=81859.0").  The Linux version must be compiled from source, which I did following their instructions for installation under Ubuntu.  The game seemed to compile and install smoothly on my machine running Ubuntu lucid 10.04.4, and it runs except that I have no sound in the game.

Even with the verbose option selected, no useful error appears on the command line and I see nothing in /var/log/syslog or /var/log/messages that looks useful.  The only clue I have is that when I try switching between different sound output options in the launcher I see the message

```
openal:463: Unknown error number 0x0000a004
```

Since the game uses Open AL for sound, I assume the error has something to do with that, but I can't interpret it any more than that or see how to troubleshoot further.

If anyone has successfully gotten this working on Ubuntu (especially lucid) I'd like to know, and I welcome any suggestions as to what's going on in my case.

---

### Post by unperson on 2012-09-07
If it's any help, the information for the Open AL library in lucid says:

> Version: 1:1.12.854-0ubuntu1~lucid1

I'm still interested to hear if anyone else has managed to install this software successfully on any Ubuntu.

---

### Post by biodiesel-bri on 2012-09-10
I got it working and it plays great (I'm about 5 missions in).  I followed the instructions but in addition I found I had to install python-markdown:

```
sudo apt-get install python-markdown
```

Here's the rest of what I installed:
```
sudo apt-get install libopenal-dev libogg-dev libvorbis-dev build-essential automake1.10 autoconf libsdl1.2-dev libtheora-dev libreadline6-dev libpng12-dev libjpeg62-dev liblua5.1-0-dev cmake build-essential libopenal-dev libwxgtk2.8-dev
```

You have to follow the instructions veeeery carefully.  They did a fantastic job on the game but the instructions are needlessly convoluted; you have to jump around in the README, and also pay attention to the install directions for compiling wxlauncher (which you need to read in another file in the wxlauncher directory).

Hopefully someone with more experience and time than me will package this and get it added to the main repo.

Good luck!

---

### Post by unperson on 2012-09-11
biodiesel-bri: You installed it on Oneiric (11.10) I take it?  What version of Open AL is in use on your system (eg. as shown by 'apt-cache show libopenal-dev')?

I tried to follow the directions carefully, although I followed wxlauncher/ReadMe.txt for building wxlauncher, and that gives a slightly different cmake command to configure things before making wxlauncher than what appears in the main README.txt.  However, I went back and followed the steps in the main readme with no better results.  I'm wondering if it's just some issue with the version of Open AL in lucid.

---

