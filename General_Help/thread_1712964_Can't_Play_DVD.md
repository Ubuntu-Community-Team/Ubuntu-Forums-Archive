---
title: "Can't Play DVD"
date: 2011-03-23
forum: General Help
---

### Post by alphaamanitin on 2011-03-23
Hello forum,

Well, I can't play any of the Bourne Triology movies.  It is the Bourne Trilogy Package, bought at Wal-Mart UPC- 2519505204.  

All other players, (have not tested other Linux Distros) plays these DVDs.  Must be a liscencing issue with the DVD codecs used.  Does anyone know how often the library files for DVD codecs are updated?  Is this something that I should expect to be playable in the future or am I just SOL?

AlphaA

---

### Post by wojox on 2011-03-23
Did you do the usual

```
sudo apt-get update; sudo apt-get install ubuntu-restricted-extras
```

```
sudo apt-get install libdvdread4
```

```
 sudo /usr/share/doc/libdvdread4/install-css.sh
```

Reboot.

---

### Post by 3Miro on 2011-03-23
[https://help.ubuntu.com/9.10/musicvideophotos/C/video-dvd.html](https://help.ubuntu.com/9.10/musicvideophotos/C/video-dvd.html)

I don't understand the legal ramifications, but if you run the command given there you should be able to watch the DVD.

---

### Post by gandaran on 2011-03-23
do you have libdvdcss2 from [medibuntu]("https://help.ubuntu.com/community/Medibuntu") installed for playing commercial encrypted DVD's

---

### Post by alphaamanitin on 2011-03-23
> **wojox said:**
> Did you do the usual

```
sudo apt-get update; sudo apt-get install ubuntu-restricted-extras
``````
sudo apt-get install libdvdread4
``````
 sudo /usr/share/doc/libdvdread4/install-css.sh
```Reboot.


Yep, did all that.   Still will not play.  

@3Miro-I know all that, I should have been more clear that it will not play despite those libraries being installed.

AlphaA

---

### Post by madmax75 on 2011-03-23
Sometimes trying out different software players might work. VLC is probably the best, but also try out Totem, Xine etc. I've found out that for instance the DVD menus will work in some player but not in another one.

Or, maybe the DVd's are just... bad. I have sometimes got poor quality DVD's from sales that freeze up when I try to play them (there is usually a reason why they are in a sale...).

Sorry, can't think of any other methods or reasons for your problem :(

---

### Post by alphaamanitin on 2011-03-24
VLC and MPlayer both failed.  I could however browse the contents of the DVD, but not open any file.  As stated before, the DVD played fine in all other players I tested.  Next I will try to play them on a dual boot laptop and see if Windows will run it and if Ubuntu on the same hardware will run it.  Should narrow it down to a licensing issue.  

alphaa

---

### Post by alphaamanitin on 2011-03-26
Bump with "solved"

I am labeling this as solved.  The issue must be a licensing thing because on my ubuntu only dell laptop it won't play, on both my dual boot desktop and laptop it will play in windows but not Ubuntu and it plays on all my other dvd players, other computers and plain dvd player.  I have removed the libdvdread4 and reinstalled, rebooted and still nothing.  As I said before, must just be a license thing.  

AlphaA

---

