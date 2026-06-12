---
title: "No Sound Again..."
date: 2010-01-07
forum: General Help
---

### Post by Liso22 on 2010-01-07
Some days ago I stopped having sound, I followed an inmense number of tutorials here and after restarting the computer I got it back, today I turn on my PC and I have no sound again, I didn't do anything, when I turned it off everything was working perfectly I don't know what's happening, I'm starting to get really annoyed, I literally use my computer only to chat and listen to music so it would be the same if it didn't turn on at all. I'm willing to kill a man for a permanent solution of this, thanks.

---

### Post by Wisp558 on 2010-01-07
Check to make sure nothing is muted.

Check by running pavucontrol in a terminal and by using the speaker icon in the corner of the screen.

---

### Post by Liso22 on 2010-01-07
ok this may be weird but I solved the problem so I'll close the thread and write the solution, I don't know if this will help anyone but I translate it from spanish:

**1.** To make a back up and then delete the old config files:

mkdir ~/pulse-backup && cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/


 sudo rm -r ~/.pulse ~/.asound* /etc/asound.conf


 Note: don't worry if some aren't in your pc


 **2.** To make sure that you have the needed libraries of PulseAudio and the config utilities:


 sudo apt-get install libasound2-plugins padevchooser libsdl1.2debian-pulseaudio


 **3.** Make sure &#8220;libflashsupport&#8221; isn't installed (it's evil @=). 

sudo apt-get remove --purge libflashsupport flashplugin-nonfree-extrasound
[FONT=monospace]
That solved it for me. Hope it's useful
[/FONT]

---

