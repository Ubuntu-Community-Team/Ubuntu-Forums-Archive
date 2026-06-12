---
title: "Swap won't stay active after reboot"
date: 2012-09-02
forum: General Help
---

### Post by Tintow on 2012-09-02
Hi there,

I've just extended the swap partition size on my Ubuntu system so I can enable hibernation.  Everything looks ok and I can enable 'Swapon' in GParted and in System Monitor it reports the new swap size correctly.

However, as soon as I reboot, the swap is not active and I have to go and set Swapon again.  This obviously stops me using hibernation.

Any ideas what might be causing this?

I'm new to Ubuntu and Linux so forgive me if this is a noob question.

Thanks.

---

### Post by Bashing-om on 2012-09-02
Tintow; 
  Hi ! welcome to the forum. noob <== we were all one at one time!

As to swap...compare uuid's between the output of:
```
sudo blkid
```
(password required)
and what your /etc/fstab contains:
```
cat /etc/fstab
```

You have already indicated the partition is large enough, now if fstab is proper, should "just work".

[INDENT]Look and advise us <==BDQ
[/INDENT]

---

### Post by Tintow on 2012-09-03
Bashing-om - you are a star!  

The problem was that I recreated the Swap partition to make it bigger and it gained a different UUID - using your tip I have changed the fstab to the new UUID and my swap file now survives a reboot.

Sadly, hibernation still doesn't work although I believe it should on this machine - it's a Dell Latitude E6410 with 3.4 GB of reported memory, swap file of 4.8GB and running 12.04 LTS 32bit - I haven't loaded any dedicated graphics drivers if this is relevant - it's running with 'Intel Ironlake Mobile x86/MMX/SSE2'

"sudo pm-hibernate" goes through the hibernate process but when coming out of hibernation, none of the apps are restored (Chrome reports a crash)

Is there a log file somewhere that might point me to the problem?

---

### Post by Bashing-om on 2012-09-03
Tintow;
  You are most welcome.

please at this time close this thread as solved. Open another post for the hibernation problem. ( 1 problem=1 post => people searching for solutions get better results)


your other problem will be addressed in the forthcoming post.

thanks; <==BDQ

---

