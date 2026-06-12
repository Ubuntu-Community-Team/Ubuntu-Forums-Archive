---
title: "Activating Nouveau - Disabling NVIDIA manual binary"
date: 2011-06-20
forum: General Help
---

### Post by Tach on 2011-06-20
Hi, I couldn't find a similar thread on this, so I'll just ask this here.

I was having slowdown freezes with the NVIDIA proprietary drivers for Ubuntu 11.04 (additional drivers), so I decided to try the latest binary from nvidia that I had to install manually. I purged the system of the nvidia drivers and then installed the manual nvidia driver (sudo apt-get --purge remove nvidia-*).

But I got the same slowdown freeze (just took a lot longer to happen now) and when I uninstalled the manual nvidia driver, X would fail to initialize (no nvidia modules).

Is there a package or configuration utility I could use to install the nouveau driver after removing the manual nvidia drivers or am I screwed?

Cause the Nouveau driver works fine, I just wanted to see if I could switch to Linux since all the games I play work fine through Wine. *Doh*

---

### Post by Tach on 2011-06-20
Nevermind, instead of messing with the xorg file, I remembered that the base install didn't use one, so I deleted it and now everything works again. :)

---

