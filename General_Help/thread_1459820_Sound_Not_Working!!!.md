---
title: "Sound Not Working!!!"
date: 2010-04-21
forum: General Help
---

### Post by Cubhicbu on 2010-04-21
I installed Ubuntu Karmic Koala and it worked fine for a little while. Then, the sound went out. The sound only works when I have my headphones in, but not when I try to play it from my speakers. It's not the speakers, because Windows can play sounds. Not even the log in sound works in Ubuntu. I have Ubuntu Resticted Formats installed, I've updated my computer, tried the fix broken packages, I've updated my kernel. I've tried everything! Nothing works!

Can someone please help me!!?~?

Matt

---

### Post by lidex on 2010-04-22
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

Go here and work through this page:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")

Check your levels in alsamixer. ```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels.
Go to "System>Preferences>Sound" and make sure the correct soundcard is default

---

