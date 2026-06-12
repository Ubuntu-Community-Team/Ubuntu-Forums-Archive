---
title: "kubuntu 11.10-no sound in external speakers"
date: 2011-10-16
forum: General Help
---

### Post by getanshub4u on 2011-10-16
Hii.I am a newbie to linux.
just installed kubuntu 11.10 yesterday  and although i can hear sound from my laptop speakers i m unable to get  any sound output when connecting to my ext speakers.
I have also installed backtrack 5 kde (which is also based on kubuntu) and have sound output from both internal and external speakers.
in backtrack,going to system settings->multimedia i have hda-intel-conexant as my sound device with xine as backend.
but in kubuntu i have a different sound device(internal analog stereo) with gstreamer backend.
So where's the problem?Can't i just copy some files from backtrack and paste them in kubuntu to get some sound?
And  one more thing,i have packages downloaded in my backtrack partition and  to install a software in kubuntu, i have to individually install all the dependencies.Is there  any other way(automated) i can install the softwares directly offline without going  through all the fuss

---

### Post by mips on 2011-10-17
Play around with your mixer setting (alsa/pulse) and see if all channels are unmuted & the volume up.

---

### Post by sffvba[e0rt on 2011-10-17
*Thread moved to **General Help**.*


404

---

### Post by linux_nub on 2011-10-24
[http://ubuntuforums.org/showthread.php?t=1845555]("http://ubuntuforums.org/showthread.php?t=1845555")

Post 8 solved it for me :D

---

### Post by getanshub4u on 2011-10-29
Well, the above post did not help or maybe i did something wrong.
Well the problem is  my sound card (thinkpad-conexant) is well identified in backtrack but not in my kubuntu.
alsa force-reload and reboot doest not solve.
I had faced similar problems earlier and eventually changed my distro.
thinking of doing it again
kubuntu ~ ubuntu :(

---

### Post by chandra on 2011-10-29
As linux_nub said, this post:

[http://ubuntuforums.org/showpost.php?p=11296617&postcount=8](http://ubuntuforums.org/showpost.php?p=11296617&postcount=8)

and this suggestion:

```
rm -rvf ~/.pulse/
```

solved it for me. vlc is no more silent.

Thanks to all.

---

### Post by getanshub4u on 2011-10-30
```
rm -rvf ~/.pulse/
```

didn't work for me.
well my sound card isn't identified  properly.and the mentioned post was for when the sound card is properly  identified.hope i have made myself clear this time.
kubuntu sucks :(

---

