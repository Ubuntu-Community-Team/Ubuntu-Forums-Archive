---
title: "dvd won't play, tried all fixes listed."
date: 2010-05-04
forum: General Help
---

### Post by TroubledTribble on 2010-05-04
I have a new laptop (Asus A52J) with one of the multi-use drives, it is a 64bit machine, with ubuntu 10.04 64bit installed.
[I]I used the help menu inside ubuntu and went online. followed the help instructions to install the codecs for the restricted formats. all installed properly, still no luck. Tried using VLC player, no luck. The drive won't play store bought DVDs. 
Can someone please help me figure this out??:(
[/I]

---

### Post by dv3500ea on 2010-05-04
Go to Applications -> Accessories -> Terminal
copy this:
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update && sudo apt-get install libdvdcss2
```
and paste using Ctrl-Shift-V
press enter

---

### Post by TroubledTribble on 2010-05-04
I still get the same response, "Error, could not read from resource.

---

### Post by techunit on 2010-05-04
I used this website to set it up. Worked very well no problems.

[URL="http://www.debuntu.org/how-to-play-dvd-under-ubuntu-linux"]https://help.ubuntu.com/community/RestrictedFormats
[/URL]

---

### Post by jerome1232 on 2010-05-04
Just to explain a bit he had you download a library from the medibuntu repostory that allows your computer to decrypt encrypted dvd's (most are encrypted).


What media player did you try VLC? Totem? (it's always been horrible for dvd's for me)

Does that disc play fine in a normal dvd player (checking to see if the disc is screwed up)

Does your dvd-rom play other discs? (it's reading correctly?)

---

### Post by His on 2010-05-04
Try what it says in on this page: [http://ubuntuforums.org/showthread.php?t=766683&highlight=divx+dvd](http://ubuntuforums.org/showthread.php?t=766683&highlight=divx+dvd)

You'll mostly want to read through part 1 and part 4.

---

### Post by darkstaar on 2010-05-04
VLC's error messages probably include something along the lines of:
**VLC cannot set the DVD's title. It possibly cannot decrypt the entire disc.**

---

### Post by TroubledTribble on 2010-05-04
got the older dvd's to play but Avatar wont.

---

### Post by TroubledTribble on 2010-05-04
Avatar is scrambled and won't play. mplayer says region is wrong. how do I set region in ubuntu like I did in windows 7?

can anyone tell me?

---

