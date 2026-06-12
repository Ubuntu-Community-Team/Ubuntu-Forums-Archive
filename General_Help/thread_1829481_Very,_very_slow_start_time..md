---
title: "Very, very slow start time."
date: 2011-08-20
forum: General Help
---

### Post by northflux2 on 2011-08-20
Hi all,

First time poster, but long time linux user.  I have a really slow startup time.  I am on 11.04 64 bit:

Linux bob 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:07:17 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

dmesg shows a long wait at this point:

[   22.315906] fb0: VESA VGA frame buffer device
[ 1053.794030] device fsid 742d9971faa7511-eb4fda3a96388b8e devid 1 transid 288600 /dev/sda3

I have tried the same trick to 60-persistent-storage.rules as mentioned here:

[http://ubuntuforums.org/showthread.php?t=1749924&page=2](http://ubuntuforums.org/showthread.php?t=1749924&page=2)

But no luck, any ideas as to what next?

Thanks

nf

---

### Post by raja.genupula on 2011-08-20
make a look at your startup apps list , uncheck the useless one . :popcorn:

---

### Post by northflux2 on 2011-08-20
Thanks for your reply, I only have the standard startup apps activated, as I said new to posting != linux. 

Even if i was running a very heavy app stack would i expect ubuntu to take 17 minutes to acknowledge a single fs?

ta

nf

---

