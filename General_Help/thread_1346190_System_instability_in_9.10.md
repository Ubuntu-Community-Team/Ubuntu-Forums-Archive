---
title: "System instability in 9.10"
date: 2009-12-04
forum: General Help
---

### Post by Druegan on 2009-12-04
I'm hoping someone can fill me in on some info here..

Running 9.04, everything was sweetness. Well, not everything, but close enough.  Then I saw that little "upgrade" option, and much evil befell upon the clicking thereof.

I've got most bits working again.. but it took a fresh install and a whole lot of mucking about to get em going..  but there's one bit that perplexes me, and I'm hoping one of you wise ones might enlighten me from my ignorance.

In the switch from 9.04 to 9.10.. what in the heck happened that hosed up the stability? And what's all this goo that I'm seeing in System Monitor under "Waiting Channel" ?  Does anybody know?

Just about everything says "do_poll".. which it never did before.. some say "do_wait"..  I also get a bunch of "pipe_wait" and "futex_wait"..   Programs hang up and turn zombie on "do_exit" when I try to close them.. stuff locks up a lot more, and gets unresponsive, or lags to all hell..

It's like running Windows ME all over again.. yeesh..  (ok, well, mebbe not.. *nothing* is that bad...)   

So can any kind soul tell me what got hosed here?  This is a fresh install, not an upgrade.. I'd love to know what got borked, and while I may be hoping beyond hope on this one, how to fix it, if possible..

Thanks, 
  Drue

---

### Post by salemboot on 2009-12-07
Seeing the same but running wine serious impedes performance.

[I]Linux xxxxxx 2.6.31-16-generic #52-Ubuntu SMP Thu Dec 3 22:07:16 UTC 2009 x86_64 GNU/Linux
[/I]

Kernel related.  I'd say recompile for your hardware.
1000mhz Timer Interrupts
Voluntary Preemption 
Deadline scheduler for default


I went as far as trying different filesystems.  JFS completely stalls at intervals. Same on ext4 and even reiser3.

---

