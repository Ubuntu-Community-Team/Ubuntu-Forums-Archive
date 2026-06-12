---
title: "No sound in 10.04"
date: 2011-11-12
forum: General Help
---

### Post by QwertyTSecond on 2011-11-12
I understand several threads similar to this have already been posted, however I can't understand them or how to get this to work.

Problem is as described, no sound whatsoever. I've made limited progress trying to identify exactly what my onboard soundcard is and what the codecs are, and less at finding them on the net or installing them.

My motherboard is an MSI P67A GD53 B3 with, according to bittech, an "Intel HD Audio via Realtek ALC892 with 8-channel support".
I also have a GTX 560 EX OC.

---

### Post by raja.genupula on 2011-11-12
go with this
[http://lkubuntu.wordpress.com/2011/07/20/sound-troubleshooting/](http://lkubuntu.wordpress.com/2011/07/20/sound-troubleshooting/)

---

### Post by QwertyTSecond on 2011-11-12
Thanks for the help.
(sudo) aplay -l produces:
* List of PLAYBACK Hardware Devices ****
without displaying any hardware devices

whereas
lspci -nn | grep '04[80][13]' produces:
00:1b.0 Audio device [0403]: Intel Corporation Cougar Point High Definition Audio Controller [8086:1c20] (rev 05)
01:00.1 Audio device [0403]: nVidia Corporation Device [10de:0e0c] (rev a1)
chris@CyborgOverlord:~$ 

which is what I'd expect, as the mobo is supposed to have onboard sound.
However, I can't spot/find the relevant soundcard on alsa-project or OSS-4.

In addition, the speaker symbol at the top right only shows a dotted line, and sound preferences->hardware has no options.

Is this a case of the onboard sound card not being support under linux?

---

### Post by lkjoel on 2011-11-12
Follow this guide: [https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit](https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit)

---

### Post by QwertyTSecond on 2011-11-13
I got to procedure Ac, entered the large chunk of code, and got this:

Sound cards not recognized by the system:
00:1b.0 Audio device [0403]: Intel Corporation Cougar Point High Definition Audio Controller [8086:1c20] (rev 05)
01:00.1 Audio device [0403]: nVidia Corporation Device [10de:0e0c] (rev a1)
Sound cards recognized by ALSA:
00:1b.0 Audio device [0403]: Intel Corporation Cougar Point High Definition Audio Controller [8086:1c20] (rev 05)
01:00.1 Audio device [0403]: nVidia Corporation Device [10de:0e0c] (rev a1)
Sound cards recognized by ALSA, and activated:
00:1b.0 Audio device [0403]: Intel Corporation Cougar Point High Definition Audio Controller [8086:1c20] (rev 05)
01:00.1 Audio device [0403]: nVidia Corporation Device [10de:0e0c] (rev a1)

Is this telling me that ALSA recognises my sound hardware, but Ubuntu doesn't?

---

### Post by QwertyTSecond on 2011-11-13
Well bugger me, I fixed it.

For anyone who stumbles onto this in the future:
Googling some more, I found this:
[http://scientificlinuxforum.org/m/index.php/t499.html](http://scientificlinuxforum.org/m/index.php/t499.html)

With a reference near the bottom to this driver:
[http://www.userdrivers.com/Sound-Card/Realtek-HD-Audio-Codec-Driver-5-14rc5-for-Linux/](http://www.userdrivers.com/Sound-Card/Realtek-HD-Audio-Codec-Driver-5-14rc5-for-Linux/)

Which I had to download elsewhere, since that site was buggered.

Downloaded, extracted, learnt how to compile and install, and it works!
Ha. Haha. Hahaha! BWAHAHAHAHAHA!

---

### Post by lkjoel on 2011-11-13
Glad to know it works! Could you mark this thread as solved? Thread Tools->Mark this thread as solved.

---

