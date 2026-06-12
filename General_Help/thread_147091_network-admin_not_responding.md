---
title: "network-admin not responding"
date: 2006-03-19
forum: General Help
---

### Post by mikelygee on 2006-03-19
I've had network-admin working (for both Ethernet and modem connections), but after a recent crash it now just sits there spinning, never really starting up. I've tried re-installing just about everything, but that doesn't help.

If I start from the live CD, I can run the copy of network-admin from my hard disk, so I know the program itself is OK.

I've tried copying /etc/network and /etc/ppp from the live CD to my hard drive, but that doesn't fix anything.

I used pppconfig to set up an new modem connection, and that works fine (i.e., "pon isp") from the command line.

I ran 'strace' on network-admin, and it looks like network-admin is spending all its time checking 'gettimeofday'.

Any ideas? What files does network-admin use that might be corrupted?

Thanks,
Mike

---

### Post by mikelygee on 2006-03-20
resolv.conf was corrupted (50k of gibberish). Deleting that fixed the problem.

---

