---
title: "Play CD audio in XFCE?"
date: 2010-01-04
forum: General Help
---

### Post by lykwydchykyn on 2010-01-04
I was wondering what most xubuntu users use to play audio CDs in XFCE.  My wife's laptop runs XFCE, and I had a time this last weekend getting it to actually play a CD correctly.

It had been configured to load CDs in "listen" audio player, but as far as I can tell listen doesn't even play CD audio.  There was nothing in the menu that allowed loading a disc.

I tried setting it to Totem, which worked ok until the first track ended.  It then stopped, and there was no way to make it continue and play the second track, or get a track listing.  Odd, since it has an option for audio CD in the menu.

Next I tried mplayer, which worked for a while, but had to be started from the command line since I couldn't get a disc to load from the GUI.  After a couple of attempts at this, mplayer locked up the whole desktop.

Next I tried VLC, since it usually sweeps in and saves the day when all else fails.  Aside from the annoyance of having to make about six to eight clicks to get an audio CD playing, it did work... except that the audio skipped badly and after a few minutes it just died and wouldn't play any more.

I finally found a program that worked: KSCD.  It's a KDE application designed solely for the purpose of playing audio CDs, and it worked flawlessly.

I don't have a problem running KDE apps on XFCE if I have to, but I just think it's odd I had so much trouble getting a program that would reliably do something so straightforward and standard, and wondered if I'd missed something obvious that would have been a better solution.

---

### Post by mkoehler on 2010-01-04
Personally I use Rhythmbox for playing audio files on my local computer.  It's pretty basic and the default player for gnome (and since XFCE is already using the basic gnome libraries, you might as well use a gnome media player as opposed to a player based in the KDE libraries).  Give it a shot.

---

### Post by andrew.46 on 2010-01-04
Hi lykwydchykyn,

> **lykwydchykyn said:**
> Next I tried mplayer, which worked for a while, but had to be started from the command line since I couldn't get a disc to load from the GUI.  After a couple of attempts at this, mplayer locked up the whole desktop.

Rather than use the default gui that is installed with the MPlayer package have another try with a better front-end called SMPlayer:

```
sudo apt-get install smplayer
```

and you might have a better MPlayer experience :).

Andrew

---

### Post by lykwydchykyn on 2010-01-04
> **mkoehler said:**
> Personally I use Rhythmbox for playing audio files on my local computer.  It's pretty basic and the default player for gnome (and since XFCE is already using the basic gnome libraries, you might as well use a gnome media player as opposed to a player based in the KDE libraries).  Give it a shot.

But does it play CDs?  That's the problem I'm having.  There are a bazillion and one apps that will play ogg/mp3/aac, but nearly everything seems to fail in some unique way when trying to play a good old-fashioned redbook CD.

---

