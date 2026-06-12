---
title: "Dell Studio 1535 Audio Help"
date: 2011-07-03
forum: General Help
---

### Post by VoidStalkerZero on 2011-07-03
Im trying to get the audio output to 5.1 surround.
Originally on windows I had to use IDT HD sound drivers. this allowed me to use the two 3.5mm headphone jacks and the one Mic (mic,audio,audio) jacks as if they were the (front, rear, sub) for surround speakers. sound comes out alright, but not in 5.1.   pls help, i'd like to watch my movies in 5.1

---

### Post by lidex on 2011-07-03
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

