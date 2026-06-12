---
title: "vlc 1.0"
date: 2009-12-04
forum: General Help
---

### Post by sudoer541 on 2009-12-04
how to install vlc 1.0 on a 32 bit ubuntu 9.04?
I have the 0. installed via synaptic, I cant find a deb package for the new version.

---

### Post by dragos240 on 2009-12-04
sudo apt-get install vlc

---

### Post by sudoer541 on 2009-12-04
> **dragos240 said:**
> sudo apt-get install vlc

I did that but it gives the the old version. I am looking for 1.0

---

### Post by Kingsley on 2009-12-04
You could try your luck with the packages on this page:
[http://packages.ubuntu.com/search?keywords=vlc&searchon=names&suite=karmic&section=all](http://packages.ubuntu.com/search?keywords=vlc&searchon=names&suite=karmic&section=all)

---

### Post by dragos240 on 2009-12-04
Did you try compiling from source, or looking for a PPA?

---

### Post by dragos240 on 2009-12-04
**1.0.0 on Jaunty Jackalope**

  In order to get the latest 1.0.0 on your latest ubuntu, you should use use a version from [PPA]("https://launchpad.net/ubuntu/+ppas"). There is an [howto to use a ppa]("https://help.launchpad.net/Packaging/PPA#Installing%20software%20from%20a%20PPA").
 The version can be found on: [https://launchpad.net/~c-korn/+archive/vlc](https://launchpad.net/~c-korn/+archive/vlc)
  [B]
[/B]

---

### Post by sudoer541 on 2009-12-04
the installation is too complicated! isnt there a .deb I can download?

---

### Post by Regenweald on 2009-12-04
> **sudoer541 said:**
> the installation is too complicated! isnt there a .deb I can download?
numkay, try this slowly:

1 Applications>>Accessories>>Terminal
2 Copy and paste the commands below

```

sudo add-apt-repository ppa:c-korn/vlc

```
```

sudo aptitude update

```
```

sudo aptitude install vlc

```

Hope this was not toooooo hard.

---

### Post by dragos240 on 2009-12-04
> **sudoer541 said:**
> the installation is too complicated! isnt there a .deb I can download?

```
echo "deb http://ppa.launchpad.net/c-korn/vlc/ubuntu jaunty main" >> /etc/apt/sources.list && apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 7613768D && apt-get update && apt-get install vlc


```did it for you. Just type sudo -s, enter your password. And then paste this code into the terminal, and hit enter.

---

### Post by sudoer541 on 2009-12-04
Update manager updated vlc to the newest version. Now the bad thing is when I use the streaming services I get the following message: 












 p, li { white-space: pre-wrap; }  [COLOR=#FF0000]Your input can't be opened:[/COLOR]
 [COLOR=#000000]VLC is unable to open the MRL 'http/shout-winamp://www.shoutcast.com/sbin/newtvlister.phtml?alltv=1'. Check the log for details.



and 







[/COLOR]
p, li { white-space: pre-wrap; } 
[COLOR=#FF0000]Your input can't be opened:[/COLOR]

[COLOR=#000000]VLC is unable to open the MRL 'http://67.19.54.94:8000;stream.nsv'. Check the log for details.[/COLOR]




where is the vlc log?[COLOR=#000000][/COLOR]


 [COLOR=#000000][/COLOR]

---

### Post by Psumi on 2009-12-04
Should be in /var/log under the file system.

---

### Post by mc4man on 2009-12-04
there is no vlc log unless you first define one in tools -> preference -> show "all' ->  advanced -> logging

Then when you start vlc it will ouput info to defined log (at least in 1.0.3

Ex.
> doug@doug-desktop:~$ vlc
VLC media player 1.0.3 Goldeneye
[0x84be0a0] logger interface: using logger...


If not, then after defining then you need to start vlc with 
```
vlc  --file-logging
```

or
vlc --file-logging <Insert command here>

The 'log' is really no different than terminal output but if working as first example will create a log even when opened as a gui.

For shoutcast better to go 
Media -> service discovery ->

As far as your links the first one is no good, too mant urls, the second one will work  if there is space on the server ( family guy # 216

From terminal

```
vlc  http://67.19.54.94:8000;
```

It will either play 
> doug@doug-desktop:~$ vlc  [http://67.19.54.94:8000;](http://67.19.54.94:8000;)
VLC media player 1.0.3 Goldeneye
[0x893d340] logger interface: using logger...
[0x8887140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x89385e8] access_http access: Raw-audio server found, nsv demuxer selected
[0x8ae9c48] pulse audio output: No. of Audio Channels: 2
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1

or something like this (keep trying

> doug@doug-desktop:~$ vlc [http://67.19.54.94:8000;](http://67.19.54.94:8000;)
VLC media player 1.0.3 Goldeneye
[0x925f140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x9310498] access_http access error: error: ICY 400 Server Full
[0x9310498] access_http access error: error: ICY 400 Server Full
[0x9310498] access_mms access error: invalid HTTP reply 'ICY 400 Server Full'
[0xb74012e0] main input error: open of `[http://67.19.54.94:8000](http://67.19.54.94:8000)' failed: (null)




Or just put the url in Media -> open network stream

---

