---
title: "iPod trouble in Karmic"
date: 2010-04-14
forum: General Help
---

### Post by not1 on 2010-04-14
Hello sirs

This may come across as a bit of an isolated and complex problem, but I haven't been able to get my iPod Nano 5th Generation to have any sort of compatibility with any iPod management programs (except with using Nautilus I guess). This includes gtkpod, Banshee and Rhythmbox.

With Rythmbox, my iPod shows up in the pane, but I cannot interact in anyway except ejecting it. There aren't any msgbox errors.

Banshee cannot read the iTunes database or something and insists that I rebuild the database on the ipod so I can use it with banshee. I did and gained full access to Banshee's iPod management with all the features it carries. I moved my music library on to the ipod but the thing states that I have zero songs whilst banshee states otherwise.

iTunes on my Windows PC will show that I have x number of GB of "other" information after using Banshee to move music. It seems that it is transferring data sufficiently but is not recognising it as "audio"

gtkpod wont let me manage the iPod before or after Banshee's tampering. 

Can anybody help? I will supply more info if needed. 
I am a newbie :S

---

### Post by Brandon Williams on 2010-04-14
The nano 5g is not supported by the libgpod library version that's in karmic. It works just fine in the upcoming 10.04.

For a newbie, the best course of action will be to wait until 10.04 is ready for release (it's just a few weeks away) and then upgrade. The steps required to get this working on karmic are probably a bit too much for someone new to Linux and/or Ubuntu.

---

### Post by 2hot6ft2 on 2010-04-14
I don't have an iPod or iPhone but this may help.
And guess what? The website is in Australia...

Keep in mind that Ubuntu Ultimate Edition 2.4 and 2.5 are based on ubuntu 9.10.
Of course we have repos. that regular ubuntu doesn't so you may need to do some searching.
So here you go:
[iPod touch/iPhone with Ultimate Edition]("http://www.ultimateeditionoz.com/forum/viewtopic.php?f=23&t=266")

Good luck.

---

### Post by nothingspecial on 2010-04-14
You need to remove libgpod (which will remove rhythmbox and gtkpod).

Then compile the latest libgpod from source and reinstall rhythmbox and\or gtkpod

If you don`t know how to do that, post back.

---

### Post by not1 on 2010-04-15
Hey guys

[This thread]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1267180") has my exact problem (and a well established, talked about and solved problem by the look of that link). However, I have run into a situation unique to a lot of what's discussed there so I will post it here.

I followed Greya's solution that can be found [here]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1267180&page=28"):

> update, new links (built on native platform)
libplist 1.2, libgpod 0.7.92, gtkpod 0.99.15

32 bit: [http://greyarium.com/ipod/ipod_5g-i386.tar.gz](http://greyarium.com/ipod/ipod_5g-i386.tar.gz)
64 bit: [http://greyarium.com/ipod/ipod5g-amd64.tar.gz](http://greyarium.com/ipod/ipod5g-amd64.tar.gz)

before installing: (To be sure that you don't have old libraries )
sudo apt-get remove libgpod-common
sudo apt-get remove libgpod4
sudo apt-get remove libplist0
sudo apt-get remove libplist
sudo apt-get remove gtkpod-data
sudo apt-get remove gtkpod

*** Your rythmbox will be automatically uninstalled with libplist, so you have to install it later.

Double-click to install
1. libplist
2. libgpod
3. gtkpod

after installing:
sudo ln -s /usr/local/lib/libplist* /usr/lib
(sorry, i don't know how to work with cmake)

if you miss your rythmox: sudo apt-get install rythmbox

it works!

I've applied for PPA, but it will be available in few days... if i'll have time...


It doesn't work for me due to something regarding liblist - I get the same problem as the next author after greya when launching gtkpod


```
gtkpod: error while loading shared libraries: libplist.so.1: cannot open shared object file: No such file or directory
```

Now I followed the instructions accurately. It must have been something else. I suspect this means something?
```

dpkg: warning: while removing libplist, directory '/usr/local/bin' not empty so not removed.
dpkg: warning: while removing libplist, directory '/usr/local/lib' not empty so not removed.
dpkg: warning: while removing libplist, directory '/usr/local' not empty so not removed.

```

I get that when trying to remove the old libplist in terminal

Can you guys tell me what silly mistake i have done?

---

