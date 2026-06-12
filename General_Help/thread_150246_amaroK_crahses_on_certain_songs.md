---
title: "amaroK crahses on certain songs"
date: 2006-03-25
forum: General Help
---

### Post by Greeface on 2006-03-25
I've been having a few problems with amaroK.  I am using Gnome, not KDE, and it crashes when I try to open a certain bunch of songs.  Sometimes it tries to open 'kmail' and crashes, and other times it just closes.  Anyone know any possible fixes?

Thanks

---

### Post by trent dillman on 2006-03-25
open a terminal (Applications > Accessories > Terminal)

type ```
amarok
``` and hit enter

open those songs and post the output

---

### Post by Greeface on 2006-03-25
hmm, I ran amaroK in the terminal and clicked on a song I know would crash and it said that it was an invalid sample rate.  I checked by right clicking the file in Nautilus and clicking Properties the Audo, and it said it was 128 kbps.  I have plenty of other songs at this bitrate and they work just fine.  Any suggestions?

Edit:  Okay, ill post the output in a second

---

### Post by adie273 on 2006-03-25
Been there, same happens to me, Amarok usually works perfectly fine, but for some reason there is the odd MP3 or something that it crashes on. Not at my ubuntu system at the moment to see what the output would be through the terminal. But if there was a fix for it i'd be that bit happier like :)

---

### Post by Greeface on 2006-03-25
Just did it again and now it just says:
```
greg@Compy:~$ amarok
amaroK: [Loader] Starting amarokapp..
amaroK: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kbuildsycoca running...
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
greg@Carl:~$ X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  7
  Minor opcode:  0
  Resource id:  0x3a00037
```


Edit:  Then I did it again and the songs that normally crash play, but it displays the 'loading' cursor in amaroK and the left context panel doesn't update.

Edit 2:  Then when I close it my CPU goes up to 100% and I can't get into the system monitor to see what is causing it (i'm assuming it's amarok).

---

### Post by Barrakketh on 2006-03-25
Could you add:
```
deb http://kubuntu.org/packages/amarok-1.3.8 breezy main
```
To your sources.list and upgrade to a more recent version of amaroK to see if that fixes your problem?  Also, are you using the gstreamer or xine engine?

---

### Post by oxEz on 2006-03-25
Does amarok crash with a specific filetype? For my part, on gentoo, amaroK 1.3.8 crashed on .WMA. I had to upgrade to 1.4-svn.

---

### Post by Greeface on 2006-03-26
I'll try updating it in a bit, thats a good idea.  It has the same issue with both the gstreamer and the xine plugins, also.  All my files are MP3, so I don't think that's the issue.  I also made sure all the files have sufficient privilidges.

I am using 1.3.1, by the way.

---

### Post by Greeface on 2006-03-26
Okay, I updated amaroK and all of the engines, but I still have the same problem :(

---

### Post by LinuxKid on 2006-03-26
**Please Note** (I'm not a moderator, don't worry ;))**:**
If you're using kubuntu, please post things related to it in the kubuntu section of the forums
If you're using gnome with amarok (is it possible?), then it fine here
If you're using kde on ubuntu, please post this in the kubuntu section of the forums as you will get much better help there

just a reminder
(hope I don't get in trouble for this :()

---

### Post by Greeface on 2006-03-27
Yeah, I'm using Gnome with amaroK.

---

### Post by adamkane on 2006-04-22
If amaroK crashes on scan or playback, then your dependencies are out of date. (Not your fault though.)

Usually all you need to do is install alsa-oss and taglib-1.4. Also you have to find a engine/sink combination that works.

See:
[http://amarok.kde.org/amarokwiki/index.php/FAQ](http://amarok.kde.org/amarokwiki/index.php/FAQ)

---

