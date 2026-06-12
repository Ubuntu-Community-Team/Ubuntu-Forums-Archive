---
title: "What is /dev/sequencer?"
date: 2006-01-28
forum: General Help
---

### Post by vayu on 2006-01-28
Tuxpaint stopped working on my childrens computer.  It loads up, plays a sound then shuts down when you click on it.  It was working fine before.

I tried running it in a terminal to see what error messages it gave:

```
ziah@ZiahNKavi:~$ tuxpaint
open /dev/sequencer: No such file or directory
Fatal signal: Segmentation Fault (SDL Parachute Deployed)
ziah@ZiahNKavi:~$

```

How do I go about tracing this problem?

I'm not sure that the /dev/sequencer is the problem because it gives that message first and then the program comes up and plays a sound.  After you click in the window then it quits and gives the seg fault error.

---

### Post by pdaoust on 2006-02-24
hmmmmm... that was my first inclination too; that the missing sequencer is what's causing the crash. In fact, that's how I found your thread; by searching for tuxracer /dev/sequencer "sdl parachute deployed". However, I tried it out on another computer, and it doesn't crash at all, although it still mentions that it couldn't find /dev/sequencer. So I think it's more of a warning message than an indicator of a crash.

Incidentally,  /dev/sequencer is the MIDI sequencer. I don't know why, but no Linux computer I've ever used has /dev/sequencer, although every card has a MIDI sequencer on it. Anyway, that's neither here nor there!

Running strace, a program that helps track down the source of a crash, doesn't give me much useful information:

```
open("/usr/local/share/tuxpaint/starters/jetplane.png", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/local/share/tuxpaint/starters/jetplane-back.jpeg", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/local/share/tuxpaint/starters/jetplane-back.png", O_RDONLY) = -1 ENOENT (No such file or directory)
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
rt_sigaction(SIGSEGV, {SIG_DFL}, {0xb7ec7ebc, [], 0}, 8) = 0
write(2, "Fatal signal: ", 14Fatal signal: )          = 14
write(2, "Segmentation Fault", 18Segmentation Fault)      = 18
write(2, " (SDL Parachute Deployed)\n", 26 (SDL Parachute Deployed)
) = 26

```

It seems to crash as it's loading sample images (or somewhere afterwards). Not terriffically helpful.l.. But be assured that this is driving me nuts, as I administer a school network of about fifteen computers or so, and the kids want to run Tuxpaint! So I'm working on it.

Any other people with ideas?

---

### Post by pdaoust on 2006-02-24
Aha! I found it! Sometimes Tuxpaint creates bad files (I don't use it myself, but I imagine sometimes it crashes, which would explain the bad files). What you want to do is fire up your file browser,  go into the folder ~/.tuxpaint/saved (a quick way is to go Control-L, then type in the aforementioned folder) and delete any pictures whose thumbnails look unusual (maybe backup all the images first) and all the .dat files whose names are the same as the pictures you deleted. That worked for me!

hope this helps!
Paul

---

### Post by vayu on 2006-02-24
[QUOTE=pdaoust]
It seems to crash as it's loading sample images (or somewhere afterwards). Not terriffically helpful.l.. But be assured that this is driving me nuts, as I administer a school network of about fifteen computers or so, and the kids want to run Tuxpaint! So I'm working on it.

Any other people with ideas?[/QUOTE]


My kids bork windows all the time with the only way back is a reinstall (they're 2 and 5 years old and they love to experiment with dragging and dropping).

One day I questioned myself how could they have done anything to the program, the only thing Linux let's them write to is their home directory.  Bingo!  I went to their home directory, found the tuxpaint folder, deleted it and we have Tuxpaint working again!

As you've said, it had nothing to do with /dev/sequencer.

---

### Post by pdaoust on 2006-02-27
good to hear you got it working again!

yeah, when I feel bad for installing Linux on this school network (the kids can't play Reader Rabbit et al), I should remind myself of what you just said... the kids borked Windows even worse. I remeber that from my own experience, actually, last year when I still had Windows on these 'puters.

I just discovered something else today: If you delete just the .dat files in the ~/.tuxpaint/saved folder, it works just as well as deleting random images. So obviously it's not the images that are the problem; it's the .dat files!

---

### Post by vayu on 2006-02-27
There's a few programs that they really like in windows.  There's a series from a company named Davidson named jumpstart that they really like.  My wife finds them at thrift stores.  I just don't have the time to figure out and reinstall windows as often as they break it.  The only thing they've done to Ubuntu so far is that Tuxpaint issue, which we now know is an easy fix.

---

