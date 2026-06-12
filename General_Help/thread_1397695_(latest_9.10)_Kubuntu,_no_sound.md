---
title: "(latest 9.10) Kubuntu, no sound"
date: 2010-02-03
forum: General Help
---

### Post by banquo on 2010-02-03
hi!
I recently installed Kubuntu 9.10 (i think, the latest anyway) on my 
gf's computer. Everything works great, except for the sound output.
The volume control works, (both the buttons on the computer and inside Kubuntu)
but there is no sound output whatsoever (not in vlc, system sound etc). Ive googled a little, and ive seen some tips about get it, rightclickin on soundsettings in the panel, and choosing preferences, i dont seem to have that tab, however ive got a "show mixer window" where i the can adjust volume. Ive got 2 tabs here ; 'HDA ATI SB' and 'HDA ATI HDMI' i guess the first one is the one that is the ordinary output, the other if i connect a tv or something. Ive also read something about 'alsa' and 'alsamix' i dont seem to have that one, and ive tried sudo apt-
but i've havent been able to find it. 
I dont know if it is of any importance, but it is the 64bit version of Kubuntu.
I'm not sure about exactly what soundcard and driver ive got, but the computer (laptop) is a pretty new HP, and wgen i run ```
cat /proc/asound/card0/codec#*| grep Codec
``` i get the answer ```
Codec : IDT 92HD75B3X5
```I hope any1 out there can help me fix this:)  thanks in advance

---

### Post by mörgæs on 2010-02-04
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats)
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

---

### Post by banquo on 2010-02-06
thanks alot =) works great now

---

