---
title: "Ubuntu 10.04"
date: 2011-08-13
forum: General Help
---

### Post by MUHAMMAD KHURRAM on 2011-08-13
I have HP DC5100SFF, P/N PT003AW#ABA desktop PC.

I have installed ubuntu 10.04 successfully.

But there is no sound at all. 

It has AC'97 rev 3, built sound device.

Intel pentium 4 2.8 GHZ HT

915 CHIPSET.

40 GB SATA HDD

512 MB RAM.

---

### Post by JonasPed on 2011-08-13
Are you sure that the sound is not muted? You can check it through the small speaker icon in the upper right corner.

---

### Post by MUHAMMAD KHURRAM on 2011-08-13
No mute.

ALso note that the speaker is also built-in, which worked nicely in windows.

---

### Post by Muskegman on 2011-08-13
open terminal and type in "alsamixer" without the quotes and make sure all the volume sliders are turned up

---

### Post by MUHAMMAD KHURRAM on 2011-08-13
ALL are Ok but still no sound.  See the attachment for more info.

Any further image I can provide?

---

### Post by raja.genupula on 2011-08-13
ok go with this 

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)


[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

---

### Post by MUHAMMAD KHURRAM on 2011-08-14
Resolved by using [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/826081](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/826081)

Thanks your links resolved my problem, I have reported a bug and resolved the problem.

---

