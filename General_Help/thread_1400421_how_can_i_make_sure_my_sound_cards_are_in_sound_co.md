---
title: "how can i make sure my sound cards are in sound configuration file? karmic 9.10"
date: 2010-02-06
forum: General Help
---

### Post by kronictokr on 2010-02-06
i got this far

darthkronic@darthkronic-laptop:~$ head -n 1 /proc/asound/card0/codec*
Codec: IDT 92HD75B3X5
darthkronic@darthkronic-laptop:~$ head -n 1 /proc/asound/card1/codec*
Codec: ATI RS690/780 HDMI
darthkronic@darthkronic-laptop:~$ head -n 1 /proc/asound/card2/codec*
head: cannot open `/proc/asound/card2/codec*' for reading: No such file or directory
darthkronic@darthkronic-laptop:~$ 

any help would be great , please let me know if you need more info and the commands i need to get it if required, thank you in advance

---

