---
title: "just a dumb question"
date: 2011-06-28
forum: General Help
---

### Post by NERDMAN! on 2011-06-28
my laptop has 2 headphone ports and a mic port on the front of it, before i reformatted and got rid of windows, the audio software seemed to be able to output 5.1 channel audio, outputting through both headphone ports and the mic port, but ive never been able to find a linux equivalent, i'd love to be able to have multichannel output again, is there such a beast as a linux multichannel surround mixer for intel HDA audio chipsets?

---

### Post by wolfen69 on 2011-06-28
You need to go into sound preferences and enable surround.

---

### Post by NERDMAN! on 2011-06-28
under sound prefferences the only thing that even mentions surround is the option for 4.0 + analog input.
i'm looking for full 5.1 :(

---

### Post by wolfen69 on 2011-06-28
```
gksu gedit /etc/pulse/daemon.conf
```
scroll down to find the line ; **default-sample-channels = 2**. Remove the semicolon at the start of the line and change the line according to your surround sound configuration:

For 5.1 channel sound: **default-sample-channels = 6**
reboot

---

