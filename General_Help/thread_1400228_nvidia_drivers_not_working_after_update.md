---
title: "nvidia drivers not working after update"
date: 2010-02-06
forum: General Help
---

### Post by RedSpade08 on 2010-02-06
I have been using 64-bit Ubuntu (Jaunty) for over a year now with no problems until yesterday.  The update manager popped up with kernel updates (didn't write them down), so I let them download and install.

When they were finished, I was prompted to reboot and did.

I was then presented with an error that Ubuntu was running in low graphics mode (as described by rhm at [http://ubuntuforums.org/showthread.php?t=1143504](http://ubuntuforums.org/showthread.php?t=1143504)

After finally getting to the desktop (at 800 x 600 resolution, normally 1200 x 800) i tried to re-install the nvidia driver through jockey-gtk, which failed.

I decided to upgrade to Karmic and see if that would fix anything. probably not the best decision, but it did fix my screen resolution

However, now no drivers are listed in the Hardware Drivers interface, and i still have no 3D acceleration, needed for some games and (less important, at least to me) desktop effects.

I ran apt-cache search nvidia and found "nvidia-glx-185 - NVIDIA binary Xorg driver" (the version originally recommended to me by both the hardware drivers interface and envyng)

I apt-get installed this and that gave me the output shown in nvidia.txt, (attached) which refers to a make.log file (also attached).  After reading that, i searched for all packages with "libc" in the name.

All of the following are installed on my system:
libc6
libc-dev-bin
linux-libc-dev
libc-bin
libc6-dev
libc6-dev-i386
libc6-i386

I reinstalled gcc with the same results.  I re-compiled emacs just to test gcc and it worked with absolutely no problems, however according to the make.log file, my c compiler "cannot create executables"

Any ideas?

```

q@redspade:~$ lspci | grep GeForce
00:12.0 VGA compatible controller: nVidia Corporation C67 [GeForce 7150M / nForce 630M] (rev a2)
```

---

### Post by wojox on 2010-02-06
Did you install or upgrade nvidia from outside the repo's?

---

### Post by RedSpade08 on 2010-02-06
> **wojox said:**
> Did you install or upgrade nvidia from outside the repo's?

Nope, always installed drivers without opening a browser.

---

### Post by RedSpade08 on 2010-02-07
ugh...just remembered I compiled gcc...probably messed something up in the process...doing a clean install of karmic now

---

