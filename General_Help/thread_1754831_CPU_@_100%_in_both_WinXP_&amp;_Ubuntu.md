---
title: "CPU @ 100% in both WinXP &amp; Ubuntu"
date: 2011-05-10
forum: General Help
---

### Post by MondaiOyaji on 2011-05-10
Hello everyone,

Absolute Linux newbie here, thanks in advance for any advice.

Here's my story: 10-year-old Dell (originally a Win98 box) running XP SP 3 started running sluggishly several months ago. System Monitor shows CPU pegged at 100%. Solved the problem by buying a new computer, but thought I could give the old Dell some more life by running Ubuntu (besides, I'd always wanted to dip my toes into the Linux waters). Well, it still ran pretty sluggishly. Got HTOP and it's telling me that the CPU is running at 100%, all the time. 

I've googled and searched around, and no one seems to have the CPU @ 100% issue under two different OSs. An extra wrinkle: for the first 10 minutes after start-up (assuming the computer is cold), CPU usage is normal. After 10 minutes, under both XP and Ubuntu, and even with no other programs running, CPU usage goes to 100% and stays there.

Again, thanks for any help.

---

### Post by timZZ on 2011-05-10
Can you tell us about the machine?

Brand
Model

and any upgrades you made that is not factory standard.

This is a good starting point.

Not over-clocking the device etc?

---

### Post by timZZ on 2011-05-10
2 more questions...

1. Does lowering your screen resolution help?
2. Does this occur when the web browser is open only? Or is this consistant I.e. happens regards even if machine is left sitting?

---

### Post by no2498 on 2011-05-10
you can also see what is running and kill it in htop
it should be something on the top of the list
or it may be jumping around
fire fox did it on my computers
i installed opera it helped some
also install the flash aid plug-in for fire fox and run it
flash hits the cpu's hard

---

### Post by MondaiOyaji on 2011-05-10
Thanks for the replies folks. To answer the questions:

Machine is a Dell Optiplex GX240 A05 Bios. Upgraded the bios in order to install more memory; currently 1 GB on board. No other changes that involved touching the motherboard. (There is an extra HD on there, but it's been on there for years w/no problems.)

Not overclocking, no. But it seems to be trying pretty hard on its own!

I never thought to play w/the screen resolution, but I backed it down just now and it doesn't seem to be making any difference.

This is all happening w/out a browser open. All you have to do is log on to the machine, and even if you walk away and touch nothing else, in 10 minutes the CPU will be pegged at 100%. (And if the machine is already warmed up, it will be at 100% as soon as you log on.)

And this is weird: per no2498's suggestion, sorted HTOP by CPU usage w/the intent to kill top processes, but the top processes are only taking 7 or 8% each. Nothing adds up to anything close to 100%. (The top two processes are swapping back and forth between HTOP and /usr/bin/python ... update notifier ...)

---

### Post by demilord on 2011-05-10
if htop doesnt show anything 100% cpu usage I would check out the cooling of the system... and search out the hardware...  could be the cpu runs to hot and the fan starts to blow at full speed but the cool ribs are fulll of dust and the air doesnt reach the cpu

---

### Post by MondaiOyaji on 2011-05-11
Demilord, my hat is off to you. (Not that I normally wear hats.)   I liked your suggestion because it was something I hadn't thought to try, so it was new. And sure enough, when I popped the hood, the cooling fins were chock-full of dust. I vacuumed it all out and plugged everything back in, but to be honest I wasn't all that optimistic. Could it really be that simple? Well, apparently it was. I just spent the last 24 hours trying various things under both OSs, and while I could (relatively easily) get the CPU to spike to 100%, it wouldn't stay there. Once I stopped doing things, it would drop back down.  Apparently, instead of buying a new computer, all I had to do was clean the old one. Ha!   Well, I still like the new compy, and now I can play w/Ubuntu on the old one.  Thanks everyone, and especially demilord!

---

