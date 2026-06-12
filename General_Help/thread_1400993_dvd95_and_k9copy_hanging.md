---
title: "dvd95 and k9copy hanging"
date: 2010-02-07
forum: General Help
---

### Post by cometdog on 2010-02-07
Trying to make a dvd9 fit on a dvd5.  Mainly would like to strip all the menus so it plays nicely.  The DVD in question is copy protected but plays just fine on my system with Movie Player or VLC.

But so far when dvd95 or k9copy tries to analyze the structure of the dvd, they just turn grey and hang.  Then my computer locks shortly after.  If I have system monitor open I can see what happens -- it's not a hard lock.  Basically the memory just starts filling up, and then when it starts filling the swap space that slows everything down and makes it unresponsive.  If I'm really patient I can get to a console and kill the process, which returns my system to normal.

Does anyone know about this issue or how to fix it?  Happens on Karmic 64-bit and 32-bit.

Handbrake works just fine, but I don't actually want to transcode the video, just strip the menus.

---

### Post by heliopaixao on 2010-03-16
Dear guy,

I am having the same problem. Did you find a solution?

heliopaixao

---

### Post by ushills on 2010-03-16
Did you run the install.sh script provided with libdvdread4.

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

I needed this to get it to work.

---

### Post by cometdog on 2010-03-18
Yes, unfortunately I have run that already and I still have the same problem.

---

### Post by thatcooldude on 2011-01-07
Having this same issue - currently taking up 8GB of RAM and a total of 9.1GB of Swap space.  Did you find any fixes?

Found [this thread]("http://ubuntuforums.org/showthread.php?t=912626&page=2") which answered my question.  Basically hanging due to the fact that it's newer copyright detection than can be decoded.  This only happens with certain DVDs.

---

### Post by cometdog on 2011-01-08
Yep, I had found out that was my problem as well.

Turns out that in some cases it's possible to make an .iso copy using ddrescue, zeroing out the intentionally corrupted bits.  Then the .iso copy will work in handbrake, etc.

You can do something like

ddrescue -d -n -b 2048 /dev/sr0 dvd.iso dvd.log

---

### Post by JohnAStebbins on 2011-01-09
> **cometdog said:**
> Yep, I had found out that was my problem as well.

Turns out that in some cases it's possible to make an .iso copy using ddrescue, zeroing out the intentionally corrupted bits.  Then the .iso copy will work in handbrake, etc.

You can do something like

ddrescue -d -n -b 2048 /dev/sr0 dvd.iso dvd.log

There are a number of patches I've submitted to the libdvdread and libdvdnav maintainers that are still pending.  One of them solves this memory consumption issue.  HandBrake uses these patches, which is why it succeeds when reading these discs. The patches can be found here:
[http://lists.mplayerhq.hu/pipermail/dvdnav-discuss/2010-August/001295.html](http://lists.mplayerhq.hu/pipermail/dvdnav-discuss/2010-August/001295.html)

---

### Post by thatcooldude on 2011-01-10
> **JohnAStebbins said:**
> There are a number of patches I've submitted to the libdvdread and libdvdnav maintainers that are still pending.  One of them solves this memory consumption issue.  HandBrake uses these patches, which is why it succeeds when reading these discs. The patches can be found here:
[http://lists.mplayerhq.hu/pipermail/dvdnav-discuss/2010-August/001295.html](http://lists.mplayerhq.hu/pipermail/dvdnav-discuss/2010-August/001295.html)

Thanks for your contribution John!

---

