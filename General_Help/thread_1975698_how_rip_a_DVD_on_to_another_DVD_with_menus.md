---
title: "how rip a DVD on to another DVD with menus?"
date: 2012-05-07
forum: General Help
---

### Post by rhythmiccycle on 2012-05-07
I want to copy a DVD, so it its exactly the same as the original, including the menus.

What programs should I use?

---

### Post by evilsoup on 2012-05-07
There are two steps in this process. First, you need to create a .ISO image of the DVD, and then you need to burn that image to the second DVD. This will create an exact replica, and should preserve menus etc.

Brasero is the default DVD ripping/burning program. I've never had problems creating ISOs from DVDs with it, but unfortunately I find it pretty useless at burning blank DVDs (note that I'm still using Ubuntu 11.04, the version of Brasero on your machine might work perfectly fine). I use XFburn for burning the ISO file.

---

### Post by forrestcupp on 2012-05-07
k9copy is great for copying DVDs. It's in the repos. It will even shrink a double layer DVD to fit on a single layer blank one. This software can perform all the necessary steps in one.

If you want to get past the copy protection on commercial DVDs, you'll have to install another library to bypass the CSS protection to work in conjunction with k9copy. If you're not in the U.S., you can do a search for libdvdcss2 for that.

---

### Post by rhythmiccycle on 2012-05-07
> **forrestcupp said:**
> k9copy is great for copying DVDs. It's in the repos. It will even shrink a double layer DVD to fit on a single layer blank one. This software can perform all the necessary steps in one.

If you want to get past the copy protection on commercial DVDs, you'll have to install another library to bypass the CSS protection to work in conjunction with k9copy. If you're not in the U.S., you can do a search for libdvdcss2 for that.


what is the library?

---

### Post by rhythmiccycle on 2012-05-07
i now running "k9copy assistant"

after installing I ran two lines of code from this site:

[https://help.ubuntu.com/community/K9Copy]("https://help.ubuntu.com/community/K9Copy")

i tried Brasero but but it was just loading for over an hour with out making any progress. 

after k9copy finished I'll post again and let everyone know if it worked.

---

### Post by rhythmiccycle on 2012-05-07
K9copy keeps freezing

It will seem to be working, but then it will freeze after about, 5 or 10 minutes.

---

### Post by forrestcupp on 2012-05-08
It's probably freezing because you didn't install the "library" and it can't get past the copy protection. I already told you that it is libdvdcss2, but if you're in the U.S., that isn't legal. You'll have to google it yourself.

Edit: actually the web site you linked to tells you how to install it from medibuntu.

---

### Post by perspectoff on 2012-06-12
If you don't require shrinking, you can just copy the VIDEO_TS and AUDIO_TS folders from the DVD to the hard drive and then burn them (using Brasero or K3b or Gnomebaker) to a new DVD.

Well, you could if my DVD writing in (K)Ubuntu weren't screwed up these days (for DVD-R type)... I'm not sure if the problem is some problem in cdrkit (genisoimage, wodim, etc.) and if installing cdrtools would be better, but I don't remember problems with wodim (1.1.11) in the past. Nowadays I can't seem to burn any DVD over 3.8 GB without problems, though...

The symptoms are freezing during a burn (usually when it reaches the 3.8 GB mark), screwed up disks (no matter which front-end package -- Brasero or k3b or Gnomebaker -- is used), and an "error 254."

It's my biggest gripe with the last several versions of (K)Ubuntu.

I've been forced to convert all my DVDs to digital files (.AVI or rarely .MKV) which are smaller and able to be stored on DVDs under the 3.8 GB limit... For this I use k9copy as a front-end to mencoder, or just mencoder directly (see [http://ubuntuguide.org/wiki/Video_Conversion](http://ubuntuguide.org/wiki/Video_Conversion) ).

Perhaps the current DVD problem has something to do with this recent update to libdvdread (i.e. maybe the problem wasn't fixed completely/correctly)?

libdvdread (4.2.0-1ubuntu3) precise; urgency=low

* Add 103-iforead-tt-srpt-pointerfix.patch: Fix read/write beyond end of
an array due to using a length value taken from the DVD, which can
exceed the allocated size, causing a segmentation fault.
(LP: #894170)

---

