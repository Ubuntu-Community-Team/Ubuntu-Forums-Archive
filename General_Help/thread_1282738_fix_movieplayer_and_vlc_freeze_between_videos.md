---
title: "fix movieplayer and vlc freeze between videos"
date: 2009-10-04
forum: General Help
---

### Post by sponsoredwalk on 2009-10-04
On ubuntu how would I fix the freeze that comes about on the vlc player and movieplayer when the next video in a playist comes on? With vlc there is like a 20 second gap of no sound and at best scattered video while with moviepayer it just takes about 30 seconds to begin the next video. It's unbelievably frustrating as I have *at least* 15-20 queued a day. No other players are good enough or easy to use as these two. Maybe gnomeplayer but that also has a huge freeze where it says cashing 11.2%, always 11.2% :(

---

### Post by ikacer on 2009-10-04
I've never experienced these errors. Are you using the most recent version of vlc? You might also want to try MPlayer to see if it gives the same error. Here is a link with a PPA that has an up to date version of MPlayer (the version in the reps is really outdated):

[https://launchpad.net/~rvm/+archive/mplayer]("https://launchpad.net/~rvm/+archive/mplayer")

I suggest you update them to the most recent version. Try it on xine as well. If it still happens with all the players you try, then it probably isn't a problem with the players, in which case I'm not sure what to suggest. Do they play back videos fine other than this playlist issue?


On a somewhat unrelated note, I recommend SMPlayer. It is an excellent front end to MPlayer.
[http://smplayer.sourceforge.net/index.php?tr_lang=en]("http://smplayer.sourceforge.net/index.php?tr_lang=en")

---

### Post by sponsoredwalk on 2009-10-04
Yes, I have every player and encounter problems with them all lol,

[LIST]xine - got messages about my system being too slow and dropping frames 

mplayer - video speeds up ever so slightly and cannot get the audio and video back in sync ( + the disjointed screen and controls is so annoying.)

kmplayer - Can't configure it to skip forwards and backwards by pressing left and right (silly I know but vlc, gnomeMplayer and all the rest allow it) And it seems to stop sometimes for no reason, unreliable.

gnomeMplayer - great program but always caching and stalling in between video's and when you first start it up :( + if you select like 3 .avi files and right click play, 3 seperate windows come up and it's probably the worst thing about this player.

SMPlayer - Also great GUI but if you select like 3 .avi files and right click play, 3 separate windows come up and it's probably the worst thing about this player. If there is a hack to fix this please let me know!

gxine - slows the pc down like crazy and for some reason every 5 secinds there is a flash, a really quick flash, like a subliminal message saying SMOKE! gets very annoying.

movieplayer - my favourite player but the really long pause in between files has gotten out of hand and it seems like it's taking EVEN longer to start up.
[/LIST]
 
Maybe this is a common error with some of the software, idk :( I'm on ubuntu 8.04 with 256 ram if that's any help.

---

### Post by ikacer on 2009-10-05
I'm not sure what the system requirements are to watch these videos, but maybe your system doesn't quite meet them? You could try messing around with the preferences to try to improve the playback. I think the xv video output driver is supposed to have the best performance, so you should try that one. Other than that I don't know what to suggest.

anyway, for SMPlayer you can select multiple files, right click, and choose
-open with "Enqueue in SMPlayer"- instead of -open with "SMPlayer"- to add them to the playlist.

---

### Post by sponsoredwalk on 2009-10-05
Thanks a million for the "Queue with SM Player" pointer, I have messed around with vlc's settings and I think it's back to normal. That said it did work earlier for a while and then went randomly. If it's still in working order I'll come back and mark this thread as solved (hopefully!!) but thanks a million for the help! :)

---

### Post by rvm4000 on 2009-10-05
> **sponsoredwalk said:**
> SMPlayer - Also great GUI but if you select like 3 .avi files and right click play, 3 separate windows come up and it's probably the worst thing about this player. If there is a hack to fix this please let me know!


Preferences -> Interface -> Instances -> Use only one instance.

---

### Post by tooquic on 2009-11-24
install this library and you will be fine. dpkg -i [libstdc++2.10-glibc2.2_2.95.4-27_i386.deb]("http://packages.debian.org/etch/i386/libstdc++2.10-glibc2.2/download")

---

