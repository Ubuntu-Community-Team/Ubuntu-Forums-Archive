---
title: "Printer and sound problem!!!"
date: 2010-07-24
forum: General Help
---

### Post by Mr_Abdul on 2010-07-24
Hello everyone. Recently I downloaded and installed Ubuntu 10.04.

My printer and sound card are detected but my printer does not print anything out until i switch it off then on again, and my sound card does not play any sound as well, even though I have downloaded Alsamixergui and Gnome Alsa Mixer.

My printer is a Epson SX100 and my sound card is VIA Technologys VIA1618. 

Please help.

Thank you

---

### Post by lidex on 2010-07-24
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

