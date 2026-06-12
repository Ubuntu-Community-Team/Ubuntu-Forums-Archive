---
title: "VLC media player: files go out of sync over time"
date: 2011-07-08
forum: General Help
---

### Post by Objekt on 2011-07-08
I can't pinpoint when it started, but some time in the past several weeks, files have started going out of sync when I view them in VLC Media Player.  Initially, sound and video are perfectly synchronized.  After 10-20 minutes, it becomes obvious that the actors' mouths are not moving when I hear their lines.

If I stop playback, restart, and resume at the same point in the show, sync is again perfect for a while.

This is a really irritating problem.  I cannot even get halfway through a half-hour TV show (really more like 22-26 minutes) without stopping & restarting.

As I stated, it's hard to point to a specific time when the problem started, but it could be connected to the upgrade to VLC 1.1.10.

Here's why I'm pretty sure this is not a problem with my files:
1) They are straight *.iso images of DVDs.  No extra conversion/compression/processing so fewer opportunities for errors in the files.
2) The same files play back perfectly in Windows under all circumstances.

Anyone else have this problem?  How did you fix it?  Will we just have to wait for VLC 1.1.11, or is there a fairly easy way I can downgrade to version 1.1.9?

---

### Post by marin123 on 2011-07-08
i'm using 1.1.9 which is in ubuntu repos.
so, you should remove vlc ppa, remove it and then install it again. you should have older version.

EDIT: i dont have that problem, but lately, the audio is off by 400 ms. when i correct it, it works all the way. and thats with fair amount of files. i dont know what is the problem. i tried alsa, oss, pulseaudio but its all the same. well, at least i know how to fix it. (in totem, the videos are in sync)

---

### Post by Objekt on 2011-07-08
I actually didn't have a "VLC" ppa, unless you mean lucid-bleed (this is the one used on VLC's page on how to get 1.1.10 in Ubuntu 10.04).

The "Software Center" only offers VLC 1.0.6.  So it looks like I'm stuck with either 1.0.6 or 1.1.10.

---

### Post by marin123 on 2011-07-08
i guess 1.0.6. is good enough. i mean, if everything was working in that version...

---

### Post by Objekt on 2011-07-08
It works, but lacks some of the features I've grown used to with 1.1.x.   Docked playlist, right-clicking anywhere on the window to add media, volume control with mousewheel no longer works, etc.  Guess I'll have to wait for the new version.

update:
Well, that didn't work either.  I'm having the same audio/video sync problem with VLC 1.0.6.  So it must be something else causing the problem.

---

### Post by chadlongstaff on 2011-07-27
[http://www.st4ck.com/en/post/ubuntu-11-04-vlc-out-of-sync/#Runtime](http://www.st4ck.com/en/post/ubuntu-11-04-vlc-out-of-sync/#Runtime)
<this worked for me, seemingly a pulseaudio "feature" needs disabling.

---

### Post by Objekt on 2011-07-27
I tried the fix you linked, but the problem persisted.  I've upgraded to VLC 1.1.11 in the meantime, so we'll see whether that fixes it for good.

update: Seems OK so far.  Watched an entire hour (well, 46 minutes really) TV show yesterday and didn't notice a sync problem.  Could be the 1.1.11 update was what was needed.

---

