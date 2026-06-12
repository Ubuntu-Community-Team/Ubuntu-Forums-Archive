---
title: "ubuntu/linux from scratch"
date: 2010-11-07
forum: General Help
---

### Post by smoke_banshee on 2010-11-07
Ive become very interested in the "linux from scratch" concept, and I am currently running ubuntu 10.04 LTS and have made a separate partition with the intention of creating a linux from scratch OS on the other partition while continuing to use this Ubuntu partition.
1) has anyone done this and have a story or advice to share about it?
2)Is there any possible issues i may have?

---

### Post by smoke_banshee on 2010-11-07
No one's got any ideas?

---

### Post by dino99 on 2010-11-07
i often install from scratch following this howto:

[http://translate.google.com/translate?js=n&prev=_t&hl=fr&ie=UTF-8&layout=2&eotf=1&sl=fr&tl=en&u=http%3A%2F%2Fwww.jellykernel.org%2Fgeek%2Finstaller-ubuntu-sans-cd-ni-cle-usb-ubuntu-netinstall%2F](http://translate.google.com/translate?js=n&prev=_t&hl=fr&ie=UTF-8&layout=2&eotf=1&sl=fr&tl=en&u=http%3A%2F%2Fwww.jellykernel.org%2Fgeek%2Finstaller-ubuntu-sans-cd-ni-cle-usb-ubuntu-netinstall%2F)

its fast and dont need to burn anything, but need an other linux already installed.

---

### Post by CharlesA on 2010-11-07
Please wait at least 24 hours before bumping yer thread. Premature bumping can lead to the thread being closed.

@dino99: Linux from scratch isn't related to installing Ubuntu.

[http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)

---

### Post by smoke_banshee on 2010-11-07
Charles A.

Perhaps you misunderstood me...

I am asking if anyone has installed a custom made OS MULTIBOOTED with a DISTRO (Ubuntu in this case, which is why I am in ubuntu forums)


EDIT:
didn't notice that the last comment was relayed to Dino

---

### Post by CharlesA on 2010-11-07
You'd run into the same problems that anyone dualbooting would run into. As long as Grub knows where the other OS is, you'll be fine.

If you are just messing around, I'd suggest testing in a Virtual Machine first to avoid any problems with getting into Ubuntu.

---

### Post by smoke_banshee on 2010-11-07
Yes... Good point... Grub2 will be much more difficult to deal with while building the OS.

the reason I thought it would be a feasible project is that linuxfromscratch site say's that you will need a "Host" OS to acquire the packages to build the system on.

Maybe since this is my first attempt at Building, I will stick to the instructions verbatim.

---

