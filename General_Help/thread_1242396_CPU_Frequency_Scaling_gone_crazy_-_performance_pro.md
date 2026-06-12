---
title: "CPU Frequency Scaling gone crazy - performance problems"
date: 2009-08-17
forum: General Help
---

### Post by bagpussnz on 2009-08-17
Hi,
I'm running Ubuntu 9.04 on a Dell E6400 with 4Gb RAM.
If I put this machine under any sort of load (e.g. run a VM, or convert a video to a dvd, or run a large compilation job), I see the following...

- the load average goes up really high
- the cpu's drop from 2.4Ghz to 800Mhz (and I can't stop it doing so)
- hal-system-smbi takes all the cpu
- system response is null

If I kill the process that caused it, I see the load gradually decrease, but can never get the machine to perform (i.e. if, when the load is down, I try running another process - e.g. starting firefox - the load just goes back up and stays there.

When this happens, all I can do is shut the machine off (a nice shutdown at this point can take up to an hour - so I usually just hit the power button).

I have discounted the docking station, gnome-power-manager, pulse.

What else can I try - driving me nuts!

Cheers,
Ian.

---

### Post by capacis on 2009-08-18
Hi,

same for me (Dell Precision M6300, 4G RAM).
[https://bugs.launchpad.net/ubuntu/jaunty/+source/hal/+bug/394663](https://bugs.launchpad.net/ubuntu/jaunty/+source/hal/+bug/394663) helped me:
I have downgraded hal to 0.5.12~rc1+git20090403-0ubuntu1 and rebooted my machine. Everythings fine again

---

