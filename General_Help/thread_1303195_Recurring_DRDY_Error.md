---
title: "Recurring DRDY Error"
date: 2009-10-28
forum: General Help
---

### Post by bluedrgn on 2009-10-28
Hello all, just recently I installed Ubuntu Server on an older machine just to play around with a variety of server applications and to get familiar with Unix command line. 

Everything goes smoothly with the install and it is entirely functional, however I periodically experience freezing (about 30 seconds) and then an error is spit out on the terminal:

[ 80.040090 ] ata1.00: exception Emask 0x0 SAct 0x0 Serr 0x0 action 0x6 frozen
[ 80.040203 ] ata1.00: cmd ca/00:08:ff:02:94/00:00:00:00:00/e3 tag 0 dma 4096 out
[ 80.040209 ] res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[ 80.040410 ] ata1.00: status: { DRDY }

I've scoured the internet for similar problems and turned up a lot of posts saying these errors are indicative of a bad hard drive. I ran badblocks on both of the hard drives and got no badblocks, but a couple of read/write errors which it recovers from. I'm assuming that these triggered when the DRDY popped up and made the system spin for a bit before returning to the scan.

I have tried booting from both drives separately, and I still get the same recurring error.

Switched to a basic Ubuntu install, still get the error. X sessions will freeze up temporarily and if I have the terminal open I can see the same error.

Anyway, I'm at a loss here. I guess the only thing left is the mobo. The whole computer is old, but I have taken decent care of it and it runs XP fine. 

Hoping someone has seen this before, any help is appreciated!

---

