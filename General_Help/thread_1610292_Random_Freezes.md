---
title: "Random Freezes?"
date: 2010-10-31
forum: General Help
---

### Post by thebarisaxkid on 2010-10-31
Hi Ubuntu friends,

I am having a very annoying problem with my laptop.  I am experiencing many freezes.  When my laptop freezes, it shows the caps lock and scroll lock lights blinking.  At first I thought it was a problem with flash (here is original thread: [http://ubuntuforums.org/showthread.php?t=1608972](http://ubuntuforums.org/showthread.php?t=1608972) )

In the original thread, I thought the freeze's were being caused by the flashplayer, but it apparently isn't the case.  The last time I experienced the freeze, I was playing around with the compiz desktop effects.  Now I am thinking that it is a problem with the graphics.  

Can anyone help me? This problem has been plaguing me for days!

---

### Post by uRock on 2010-10-31
Next time you think a freeze may be coming, open System Monitor or install and run htop in a terminal. I think your RAM is overloading while streaming in your browser. I have noticed that if I am surfing through youtube and watching different videos, that each video is stored in the RAM and not dumped until the Firefox(or other browsers) session is closed. If it completely fills the RAM and goes to swap, it will start to slow down, then it locks up.

htop is a CLI system monitor with color and when run with sudo the sudo command, you can use it to kill processes.

---

### Post by P4man on 2010-10-31
Flashing keyboard leds is a kernel panic, that doesnt happen even if you completely run out of memory. 

First thing I would do is check  the log files in system > administration > log file viewer. Most logs have timestamps, if your machine ever freezes up again, make a note of the time, then browse through your logs and see what happened at that exact time.

---

### Post by thebarisaxkid on 2010-10-31
> **P4man said:**
> Flashing keyboard leds is a kernel panic, that doesnt happen even if you completely run out of memory. 

First thing I would do is check  the log files in system > administration > log file viewer. Most logs have timestamps, if your machine ever freezes up again, make a note of the time, then browse through your logs and see what happened at that exact time.

Should I look at all the logs or just the kernel log?

---

### Post by neomchiang on 2010-11-09
how can i think the freeze would be coming?
my laptop have freeze when it running Transmissin (downloading) and i just sit in front of the laptop having my lunch (KFC+Cola).
but it just happen
 
i am really don't know how to THINK the freeze would be coming.
cus' the KFC or the Cola.

---

