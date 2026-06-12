---
title: "headset jack not working need help please"
date: 2010-10-06
forum: General Help
---

### Post by c2tarun on 2010-10-06
hi friends
i m reposting this thread again
i posted it long time ago but nobody responded
please reply

i m using ubuntu 10.04 lucid 64 bit.
speakers are working fine.
but when i insert any headset in the headset jack speakers stop playing sound as expected but headset is not playing any sound.
please reply folks
thanks

---

### Post by HereInOz on 2010-10-06
The fact that the speakers work until you plug a headphone into the headphone socket indicates that the headphone socket is correctly wired, and is correctly switching the speakers out as required.

It is possible that even though the socket is switching out the speakers, it is not making contact with the headphone plug, and is therefore not connecting to the headphones.  This is the most likely situation.

Either that or the headphones are faulty, but I guess you have already tried a different set of headphones, so that is unlikely.

Most likely a faulty socket.  

Unless there are two outputs in the output section of sound preferences.  If there are two different outputs listed (not likely but possible) try switching between the two.

---

### Post by c2tarun on 2010-10-06
> **HereInOz said:**
> The fact that the speakers work until you plug a headphone into the headphone socket indicates that the headphone socket is correctly wired, and is correctly switching the speakers out as required.

It is possible that even though the socket is switching out the speakers, it is not making contact with the headphone plug, and is therefore not connecting to the headphones.  This is the most likely situation.

Either that or the headphones are faulty, but I guess you have already tried a different set of headphones, so that is unlikely.

Most likely a faulty socket.  

Unless there are two outputs in the output section of sound preferences.  If there are two different outputs listed (not likely but possible) try switching between the two.



i forgot to mention, before ubuntu windows 7 was installed in my system, and headsets were working fine then. now i am completely switchd to ubuntu and facing this problem

---

### Post by Highlordbob on 2010-10-09
> **c2tarun said:**
> i forgot to mention, before ubuntu windows 7 was installed in my system, and headsets were working fine then. now i am completely switchd to ubuntu and facing this problem

I am currently having the same problem on my netbook as well. And I had windows 7 on it before and did not have any problems.

---

### Post by Highlordbob on 2010-10-09
I had found this here [http://ubuntuforums.org/showthread.php?t=1481792&highlight=headphones]("http://ubuntuforums.org/showthread.php?t=1481792&highlight=headphones")

Run this in the terminal
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```

and then add this to the end
```
options snd-hda-intel model=<your computer manufacturer>
```

Where <your computer manufacturer> is put the company that makes system.

Then reboot. Once restarted, go into the sound preference menu. In the output tab select connection and select Analog Headphones and then it should work.

---

