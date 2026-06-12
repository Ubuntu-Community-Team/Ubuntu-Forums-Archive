---
title: "Help with a few questions please..."
date: 2009-10-15
forum: General Help
---

### Post by Kreative_Station on 2009-10-15
:popcorn:


Hi there, I just installed my Ubuntu 9.04 version through the WUBI installer (couldn't wait for the LIVE CD download).  Also, I can't wait until the new release it's just around the corner!!

Couple quick questions though real fast.


[LIST]
[*]What is the difference between Synaptic Package Manager & Add/Remove?
[*]How do I properly install a video driver manually for my ATI 2600 HD 512mb?
[*]Any versions of Photoshop compatible with Ubuntu (debating GIMP)?
[*]I posted a thread the other day, it is no where to be found?!?
[*]Where is the "device manager", I would like to see if all devices are properly installed ( I R Windows nOOb )
[/LIST]

Any links to other posts or threads you find userful, I appreciate it much.

Thanks for the time to reply.

---

### Post by sandyd on 2009-10-15
> **Kreative_Station said:**
> :popcorn:


Hi there, I just installed my Ubuntu 9.04 version through the WUBI installer (couldn't wait for the LIVE CD download).  Also, I can't wait until the new release it's just around the corner!!

Couple quick questions though real fast.


[LIST]
[*]What is the difference between Synaptic Package Manager & Add/Remove?
[*]How do I properly install a video driver manually for my ATI 2600 HD 512mb?
[*]Any versions of Photoshop compatible with Ubuntu (debating GIMP)?
[*]I posted a thread the other day, it is no where to be found?!?
[*]Where is the "device manager", I would like to see if all devices are properly installed ( I R Windows nOOb )
[/LIST]
I have a few more questions, but I'm trying to just read more and more on the forums, there is SOOOOooo much info here.  

Any links to other posts or threads you find userful, I would LOVE to read em.

Thanks for the time to reply.
1. Add / Remove is more descriptive and doesn't list the packages by their actual packagename. Instead it converts the name to something non-techines would easily understand.

Synaptic installs programs according to the package name.
There will also be a new program in Karmic (i simply advise you to wait for it, its kind of a pain to install it, mess it up, and realize theirs already a new version to download)
called Ubuntu Software Center. Its sorta like Add / Remove + kpackagekit

2.
```

sudo apt-get install envyng-core
envyng -t

```follow onscreen instructions

3.
[http://appdb.winehq.org/appview.php?appId=17](http://appdb.winehq.org/appview.php?appId=17)
[http://appdb.winehq.org/appview.php?appId=1794](http://appdb.winehq.org/appview.php?appId=1794)
Adobe photoshop elements 7 works perfectly. i use it every day...
and mind the garbage reviews. their only garbage because their not runnable in the developmental builds of WINE....

4.
Search -> Find All Your Threads

5.
either
```

lspci

```or

```

sudo lshw

```will sufface.

and ubuntu support most hardware out of the box (except for wireless cards) so theirs not really any point

p.s. caonical ships livecds. for free.
[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)


EDIT:
aannndd. their closed temperily. their probably preparing for the karmic preorders......

---

### Post by Johnny B on 2009-10-15
if you can't wait for the live cd to download, get the torrent, its always faster, especially when a new version is released.
[http://releases.ubuntu.com/9.04/]("http://releases.ubuntu.com/9.04/")
[http://releases.ubuntu.com/9.10/]("http://releases.ubuntu.com/9.10/")

---

### Post by lisati on 2009-10-15
For finding your posts snd threads, there are a couple of ways of doing it. The quickest is to click on the "search" drop-down list and then click on "find all your threads" or "find all your posts"

---

