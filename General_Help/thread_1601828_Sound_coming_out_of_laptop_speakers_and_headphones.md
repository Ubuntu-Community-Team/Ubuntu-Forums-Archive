---
title: "Sound coming out of laptop speakers and headphones"
date: 2010-10-20
forum: General Help
---

### Post by jgsamuel on 2010-10-20
after i upgraded from ubuntu 10.04 to 10.10 i started noticing sound was coming out of my laptop speakers when my headphones were plugged in..thanks for all the help in advance

---

### Post by alexandari on 2010-10-20
check your mixer's settings. I've had this problem,and I just...unplugged the headphones and pluged them in again,and...problem solved.

---

### Post by jgsamuel on 2010-10-20
> **alexandari said:**
> check your mixer's settings. I've had this problem,and I just...unplugged the headphones and pluged them in again,and...problem solved.
what should the mixer settings look like..it didnt help

---

### Post by AgentZ86 on 2010-10-20
> **jgsamuel said:**
> what should the mixer settings look like..it didnt help

Output Tab = Analog output perhaps ? should be default I believe

Hardware tap = Analog Stereo ?

And try muting the volume and see if everything turns off and then unmute to see if it either all comes back on or returns to normal

---

### Post by jgsamuel on 2010-10-20
> **AgentZ86 said:**
> Output Tab = Analog output perhaps ? should be default I believe

Hardware tap = Analog Stereo ?

And try muting the volume and see if everything turns off and then unmute to see if it either all comes back on or returns to normal
Ok Idk if this is part of the problem the hardware tab is on analog stereo duplex...and when i mute they both are muted.

---

### Post by munthe on 2010-10-20
Hi, 

What laptop are you on?

I had the same problem on a Lenovo IdeaPad u350 and ubuntu 10.04
Found a solution here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/477226](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/477226)

I put the fellowing line in /etc/modprobe.d/alsa-base.conf
options snd-hda-intel model="olpc-xo-1_5"

Hope you get it solved.

---

### Post by jgsamuel on 2010-10-21
> **munthe said:**
> Hi, 

What laptop are you on?

I had the same problem on a Lenovo IdeaPad u350 and ubuntu 10.04
Found a solution here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/477226](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/477226)

I put the fellowing line in /etc/modprobe.d/alsa-base.conf
options snd-hda-intel model="olpc-xo-1_5"

Hope you get it solved.
yeah im on a lenovo y550 is it a problem with lenovos?

---

### Post by munthe on 2010-10-21
I know at least the s10 and the u150 have had the same problem.

You could also try this solution:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/477226/comments/60]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/477226/comments/60")
from the previous mentioned bug.

I haven't tried this my self but according to the thread that is the best solution for the u350. So it might work for you as well.

---

