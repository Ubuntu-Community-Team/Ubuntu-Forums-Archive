---
title: "Installing libdvdcss in VLC"
date: 2006-03-15
forum: General Help
---

### Post by GreveFelix on 2006-03-15
Hello,
I am trying to install libdvdcss in VLC to play original DVD. I followed the installations information ... The first step was to: 


 [COLOR="SandyBrown"]INSTALL file for libdvdcss, a DVD access library

Configuring libdvdcss
=====================

A typical way to configure libdvdcss is:

   ./configure --prefix=/usr

See `./configure --help' for more information.

It is also possible to cross-compile for the Win32 platform using mingw32:

   CC=i586-mingw32msvc-gcc CFLAGS=-I/usr/i586-mingw32msvc \
     RANLIB=i586-mingw32msvc-ranlib ./configure --host=i386-mingw32msvc \
     --target=i386-mingw32msvc --build=i386-linux
[/I][/B]
[/COLOR]


Thats why i did:

felix@ubuntu:~/libdvdcss-0.0.3$   ./configure --prefix=/usr
loading cache ./config.cache
checking host system type... i686-pc-linux-gnuoldld
checking whether make sets ${MAKE}... no
checking for gcc... no
checking for cc... no
configure: error: no acceptable cc found in $PATH
felix@ubuntu:~/libdvdcss-0.0.3$

WHAT IS AN gcc and whats cc, well at least I dont have any but ... why?
 
Thanks for help I just installed Ubuntu one week ago, and I am very convinced and happy ... greetings to the community ...

---

### Post by Perfect Storm on 2006-03-15
You need the basic compiling stuff before you can start compiling:

```
sudo apt-get install build-essential
```

If you are a non-US you can get libdvdcss by doing this trick:

```
 sudo gedit /etc/apt/sources.list
```

add:

[b]## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
[/b]

save and close it

```
sudo apt-get update
sudo apt-get install libdvdcss2
```

---

### Post by damu on 2006-03-15
I tried to follow your advices, so that I would at least get this libdvdcss. But I got this message in the terminal :

[HTML]Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candi[/HTML]

That's the problem I always had so far, even though I updated my source list
:-k

---

### Post by Perfect Storm on 2006-03-15
Try go through synaptic package manager and install it through there, sometimes it helps.

---

### Post by damu on 2006-03-15
The only way  I found to install libdvdcss2 is to download the 2 needed .deb from the net (u can find some link on this forum if you make a search with "libdvdcss2" or just google "libdvdcss2_1.2.9-1_i386.deb + download") and then

sudo dpkg -i "the path of the file/filename"

which for me was :

sudo dpkg -i home/damu/libdvdcss2_1.2.9-1_i386.deb
sudo dpkg -i home/damu/libdvdcss2-dev_1.2.9-1_i386.deb

I can now watch DVDs on Ubuntu. :) 

It's far from perfect though, as the video is slightly choppy (with all players VLC, Xine, Totem) which is very annoying... :???: 
I guess it has to do with buffering or something like that...any help much very welcome

---

### Post by Perfect Storm on 2006-03-15
Did you enable DMA on your DVD-drive? [http://doc.gwos.org/index.php/DMA](http://doc.gwos.org/index.php/DMA)

---

### Post by damu on 2006-03-16
Thanks bunch, I could sort it out with your link! \\:D/ 

The trick for me was that DMA was enabled for cdrom but not for the cdrom1, which is actually the one related to my DVD player.
To find out, I just went on Places / Computer / file system / dev , and saw that on my configuration there is not only cdrom but also cdrom1 and cdrw.
Ubuntu created this 3 items in dev for 2 physical players (a dvd player and a cd writer)...always a bit confusing this, in linux world...
So, for other ones having the same issue , make sure that DMA is actually enabled for the item corresponding to the DVDplayer,which might not be cdrom but cdrom1 or else...

...no more dual boot to XP to watch a DVD... :)  thanks again!!

---

### Post by GreveFelix on 2006-03-16
Yes, now it worked for me aswell first I got some Problems but then ... for some reason everthin worked out fine. .....:D 


In the Ubuntus Help (the button that looks like a lifebelt) Text anybody will find Help under "HArdware" they explain how to aktivate your DMA ...


Thanks ARTIFICIAL INTELLEGENCE you are the best ...

---

