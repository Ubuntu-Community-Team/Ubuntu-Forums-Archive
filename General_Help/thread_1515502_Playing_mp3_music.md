---
title: "Playing mp3 music"
date: 2010-06-22
forum: General Help
---

### Post by prahar on 2010-06-22
Hey guys,

I am totally new to linux systems and ubuntu. I've been working on windows all my life, and want to get rid of it. For now, however, I am just running Ubuntu 9.10 from my USB drive, just to get a feel of what it offers.

Basically, the problem is, I am unable to play any of my music files (.mp3). It keeps asking to download some plugin, which it later says cannot be found.

I am running Ubuntu 9.10 which is presently just booted from the drive. I haven't really gotten to installing it. However, if I am unable to play the files, I guess I won't convert after all. 

Help!

PS - I didnt know exactly where to put this thread. I'm sorry if it's in the wrong forum.

---

### Post by ankit singh on 2010-06-22
Type this code in terminal
```
sudo apt-get install ubuntu-restricted-extras
```

This will install all media formats.

---

### Post by Klump on 2010-06-22
The easiest way (and the only one I know) is to install ubuntu-restricted-extras package via synaptic or by typing into the console
```
sudo apt-get install ubuntu-restricted-extras
```That should be it.

---

### Post by ankit singh on 2010-06-22
After that go to System>Admin..>Synaptic and search for libdvdcss and libdvdread4  and install it.This libraries are required for reading dvds

---

### Post by prahar on 2010-06-23
> **ankit singh said:**
> Type this code in terminal
```
sudo apt-get install ubuntu-restricted-extras
```This will install all media formats.


Hey! I tried this...and it says such a package does not exist.

---

### Post by tommcd on 2010-06-23
> **prahar said:**
> Hey! I tried this...and it says such a package does not exist.
First, make sure the universe and multiverse repositories are enabled (they should be by default):
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)
Then, either hit the "reload" button when prompted as it says in the link, or run in the terminal:
```
sudo apt-get update
```
Then install the ubuntu-restricted-extras package.
Also enable the **medibuntu** repositories and get the w32 codecs (if you are running 32bit Ubuntu) or the w64 codecs (if you are running 64bit Ubuntu):
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
These codecs will enable support for Windows media files.

Also see this on installing software in Ubuntu:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

And welcome to the Ubuntu forums!

---

### Post by MooPi on 2010-06-23
Let's try a more direct route: ```
sudo apt-get install lame mpg123
```
This should allow you to play and encode new music to mp3 format.

---

