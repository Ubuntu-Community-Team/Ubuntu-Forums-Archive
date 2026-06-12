---
title: "Screen freezes/locks up periodically"
date: 2010-11-23
forum: General Help
---

### Post by Martin_sensei on 2010-11-23
Hello,

I am not sure exactly what is going on, but my ASUS UL30a (X32a) keeps locking up until I press a key, then it seems to resume for a while.

At first I thought it was just the mouse, but I noticed that the screen stops refreshing also. Hitting the space key (or any other key) brings the systme back to life (until it happens again).

Any ideas?
It is a fresh install of Ubuntu 10.10, not much seems to be going on in the top list (compiz 1%, xorg 0.5%)

I am looking for ways to try and diagnose the problem (if not fix it ;))

Cheers,

Martin

---

### Post by TeoBigusGeekus on 2010-11-23
Could it be [this?]("http://www.art.ubuntuforums.org/showthread.php?t=1592741")

---

### Post by Martin_sensei on 2010-11-23
Well, my symptoms are slightly different,

When it freezes, the mouse also stops moving, its like the whole system has just paused (until I hit a key on the keyboard)

---

### Post by Martin_sensei on 2010-11-23
Also, my CPU usage doesn't seem to spike during a freeze...

---

### Post by Martin_sensei on 2010-11-23
Hello again,

I seem to have found something of relevance in the syslog.

The freezes seem to coincide with the following messages in the log:

```
Asus rtkit-daemon[1311]: The canary thread is apparently starving. Taking Action.
Asus rtkit-daemon[1311]: Demonting known real-time threads
```

Does anyone know what this means and what to do about it?

---

### Post by Martin_sensei on 2010-11-24
Hello again,

I have now discovered that the process causing the starving canary thread is the PulseAudio process.

My problem, therefore seems to be related to PulseAudio, or my sound hardware maybe.  I have only found one other post which looks similar: [http://ubuntuforums.org/showthread.php?t=1542075&page=2]("http://ubuntuforums.org/showthread.php?t=1542075&page=2"), but I do not have any power saving settings in my BIOS, so I can not do the fix suggested.

Does anyone have any ideas on how to diagnose any PulseAudio problems, or any issues with my sound hardware?

---

### Post by SecretCode on 2010-11-24
There should be hundreds of threads on pulseaudio problems - going back to Karmic at least. My sound is currently OK and I'm not even going to think about touching it, but there are or were lots of issues around recognising and setting up for various types of hardware.

---

### Post by Martin_sensei on 2010-11-24
There are indeed lots of threads discussing lots of pulseaudio issues.  I was hoping for some specific help with my starving canary thread though.

Can anyone at least explain what a canary thread is?

Cheers,

Martin

---

### Post by SecretCode on 2010-11-24
Sorry ... I can only guess that a canary thread is a thread used to detect adverse conditions, like the canaries they used to take into mines to detect oxygen shortage.

If you look at optimising how pulseaudio is configured on your system [SIZE="1"]or removing it altogether[/SIZE] you might be addressing the root cause.

---

### Post by Martin_sensei on 2010-11-24
Interesting theory :)

Well I seem to have fixed the issue, as I have been running my laptoip for about an hour now with out a single freeze.

I did the following:

1. Upgraded the BIOS to ASUS v212
2. Updated the kernel (though normal updates) to 2.6.35-23
3. Added tsched=0 to the load-module-udev-detect line in /etc/pulse/default.pa

one or more of these actions seems to have helped.  Fingers crossed... (I'll mark this thread as solved if my laptop works without freezing for a few days)

---

