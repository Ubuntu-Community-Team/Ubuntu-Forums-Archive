---
title: "Launcher Help Please - IDJC - Internet DJ Console"
date: 2010-05-29
forum: General Help
---

### Post by cryptotheslow on 2010-05-29
Hi,

I'm sure this can be done, but I'm too stupid to work out how.

I use IDJC (Internet DJ Console) to stream to a Shoutcast server.

IDJC relies on having a jackd process to connect to.

So at the moment this is how I have to proceed..

1. Open 2 Terminal windows
2. In Terminal 1 I startup a jackd instance with ->  jackd -n foridjc -d alsa -r 44100
3. In Terminal 2 I then startup IDJC referencing the above jackd instance with -> idjc -j foridjc


This all works fine, but just feels a bit clunky.

I'd like a launcher script that can start the jackd instance and kick it into the background then start idjc using the already started jackd.

Would also be nice if when exiting IDJC, the related jackd process got terminated too :D

I've tried getting this to work using a shell script but it always seems to get tied up with jackd running in the foreground.

Any ideas would be appreciated.

Many thanks
~crypto~

:guitar:

---

### Post by Ichido on 2010-05-29
Try this:
Right Click in Top Panel and choose ADD TO PANEL.
Click on "custom Application Launcher" and click the ADD Button.
Type: "Application in Terminal"
Name: Type in the applications Name.
Command: Type in the Terminal Command needed to start the App.
( I don't know if you can put Both Commands in the one "Command" window, but try it)

---

### Post by cryptotheslow on 2010-05-30
Unfortunately that doesn't seem to like 2 commands.

I have now created 2 tiny scripts:

1.
```
jackd -n foridjc -d alsa -r 44100 &
idjc -j foridjc
```2.
```
#!/bin/sh
jackd -n foridjc -d alsa -r 44100 &
idjc -j foridjc
```They both do exactly the same thing.

It does work in that running either will start jackd then idjc and it all works fine.

However, when I then exit idjc the jackd process is left running.

I have managed to get around this though - luckily idjc has a configurable "Command to run on exit" setting. So in there I have put:

```
killall jackd
```So I have ended up with a custom launcher on the panel that points to my little script to start the two things, and idjc takes care of killing jackd as it exits.

---

