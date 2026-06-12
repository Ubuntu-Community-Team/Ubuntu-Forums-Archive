---
title: "Totem stops playing music after a few seconds [with screenshot]"
date: 2010-10-11
forum: General Help
---

### Post by imbjr on 2010-10-11
Installed Meerkat and I've discovered that after dropping a directory of MP3s onto Totem in one virtual desktop (from an NFS location), stepping away to another desktop will sometimes cause totem to stop playing the first track after a few seconds.

Odder still is that when I go back to the virtual desktop to look at totem, its play button is disabled and the little arrow that would normally be against the first track is gone (see image attached).

I thought I'd use a different music player, but none other seems to get the track order right and Rythmbox does not seem to support playing a directory of music dropped onto it or by right-clicking and selecting play.

---

### Post by imbjr on 2010-10-12
Looking into this problem reveals that Totem has a bit of history with drag and drop.

Well I can duplicate the problem on a fairly regular basis. I tried valgrind to see if there were any interesting messages, but the process is too slow and since the problem is intermittent it was impossible to catch the problem at such a speed.

Looks like it will be right-click and play with Totem from now on, or add mp3us to the server directories.

---

### Post by imbjr on 2010-10-16
Well the best fix so far is to create a short cut for totem on the desktop, or a panel, and drag and drop a music-containing directory onto that.

---

### Post by imbjr on 2010-10-27
I just dragged a music folder onto Totem and did not change to a different virtual desktop, expecting the problem not to happen because there's no change in desktop.

However ...

Before the music stopped, I noticed that the progress bar was not progressing and neither was the time count, nor was displayed the length of the track. That's the first time, I've managed to catch it doing that.

Yup, looks like Totem has drag and drop problems. Again.

---

