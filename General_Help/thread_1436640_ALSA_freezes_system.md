---
title: "ALSA freezes system"
date: 2010-03-22
forum: General Help
---

### Post by brainscauseminds on 2010-03-22
Hi everybody!

I tried to get my Tascam 144 soundcard working under Ubuntu. I got a snapshot of the ALSA driver from [http://www.kernel.org/pub/linux/kernel/people/tiwai/snapshot/](http://www.kernel.org/pub/linux/kernel/people/tiwai/snapshot/) and then compiled it and installed it using following commands:
./configure
make
make install
./snddevices
I'm not sure why I ran the last script as it seemed suspicious, because it seemed to create quite a lot of files under /proc/, probably because I built the alsa driver with all supported sound cards.
The problem is that now system freezes when I'm at login screen or just a few secs after the desktop is loaded.
I've tried reinstalling most alsa base, tools, firmware packages, but the problem is still there.
Fortunately with 2.6.31-19-generic kernel everything works and I can type this message. But booting with 2.6.31-20-generic eventualy freezes the system.
I'm sorry if this problem is trivial as I'm rather new Ubuntu user. But any suggestions how I could solve this issue?

Thanks in Advance!

---

### Post by brainscauseminds on 2010-03-24
I'm not still sure how to fix the problem I described above, but I think I try Fedora 12 (or 13 alpha) that I think works with newer kernel versions than current Ubuntu as I still try to get my Tascam 144 working.

---

