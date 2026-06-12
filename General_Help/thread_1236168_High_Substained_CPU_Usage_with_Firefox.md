---
title: "High Substained CPU Usage with Firefox"
date: 2009-08-10
forum: General Help
---

### Post by Iteria on 2009-08-10
I'm running Jaunty and I'm having a problem with Firefox eating CPU. I'm used to Firefox spiking my CPU usage for short periods of time while i'm using it, but It's never been this bad. 

It's only happening with Livestream.com streams. Hulu works fine. a couple of other flash-based streaming sites work fine. However, while I'm at livestream, the usage is almost 100% of both my cores. Not only that, but the duration is as long as I'm at the site. The usual spikes are only 50% to 60%. Plus, as I said, they are usually really short, somewhere between 10 and 30 seconds.

Does anyone have any insight?

---

### Post by zkriesse on 2009-08-10
It could you have something running in the background...try this. go to System/Administration/System Monitor.

---

### Post by Iteria on 2009-08-10
I'm running openbox and it has some sort of terminal based system monitor, so I don't know the name of the thing doing this, but here is the command for it.

```

/usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth - nolisten tcp vt7

```

I'm assuming that that is something with X server? whatever it is, it's tying up a whole core by itself.

---

### Post by zitstif on 2009-08-10
You should check out adblock for firefox and block flash based ads. Flash is what seems to make CPU usage spike when I'm using firefox. It's quite annoying.

---

### Post by Iteria on 2009-08-10
funny thing is, I have ad block plus turned on and it's still doing it. I don't think that's the problem.

---

### Post by Commander_Keen on 2009-08-10
I think its normal.
I just installed 9.4, w/firefox 3.Xx and I get the same result.
I'm on foxnews, Dice, Monster.com and the CPU is very high

---

### Post by Iteria on 2009-08-10
Thanks for letting me know. That really sucks though. It makes it so you can't do anything. I guess it's a valid assumption to assume that you're probably not going to be doing a lot while you watch a video, but some people like me like to watch videos and do other stuff.

I'm going to see if I can report it as a bug with Mozilla.

---

### Post by martinbaselier on 2009-08-10
Just tested and works fine here, pretty high cpu, about 80% on 1,9 Ghz centrino. But not 100% constantly. 

[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

This thread might help and I personally had some troubles with flash and alsa. So I don't use alsa anymore.

If you're running openbox, you won't use compiz. Pulse might be a problem too.

---

### Post by Iteria on 2009-08-10
that thread made it a little bit better. at least it's not maxing my CPU now, but it's still really high (80% - 90%). I guess that's the best I can hope for since the site (livestream) is all flash.

---

