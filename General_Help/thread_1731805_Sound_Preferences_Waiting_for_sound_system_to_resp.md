---
title: "Sound Preferences: Waiting for sound system to respond; cannot change volume"
date: 2011-04-17
forum: General Help
---

### Post by trebi on 2011-04-17
Hi,

somehow (I mean, I didn't play with sound settings etc.) *Sound Preferences* have stopped working. When I click on the *Speaker Icon* in the tray, there is only inactive *Mute* option, *Rhytmbox* and *Sound Preferences* option, but it will only give me information window *Waiting for sound system to respond* when I click on it. Sound is working normally, I just can't change volume (that really sux) and also it's not working inside VirtualBox.

I have tried both methods mentioned [in this topic]("http://ubuntuforums.org/showthread.php?t=1495061"), but none worked for me.

---

### Post by trebi on 2011-04-18
bump

---

### Post by trebi on 2011-04-19
Problem solved: the reason was that I moved */home* on NTFS partition, which doesn't support linux file access options (chmod, chown...). Really not good idea in Ubuntu, rather use ext3 and access it from win7 via ext2fsd

---

