---
title: "sound problems in ubuntu 10.4 LTS"
date: 2010-05-05
forum: General Help
---

### Post by ecatodarcus on 2010-05-05
i have just upgraded to UBUNTU 10.4 LTS and i have no sound. I didn't have this problem before with 9.10. Does anyone knows what i have to do in order to fix this?

thank you in advance

my system is 64bit

sorry if i posted in a wrong section.

---

### Post by dremation on 2010-05-05
Have you tried reinstalling the kernel-headers?

---

### Post by ecatodarcus on 2010-05-05
no
could you please inform me how i can do that?
thank you for your quick answer

---

### Post by lidex on 2010-05-05
Check your levels in alsamixer.
```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default.

Do 'Part A' here:
[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")

Report results.

---

### Post by blackfox-bt on 2010-05-05
see: [http://ubuntuforums.org/showthread.php?t=1473652](http://ubuntuforums.org/showthread.php?t=1473652)

---

### Post by ecatodarcus on 2010-05-06
> **lidex said:**
> Check your levels in alsamixer.
```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default.

Do 'Part A' here:
[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")

Report results.


i tried it and my problem is solved!! thank you very much for your quick answer

---

### Post by lidex on 2010-05-06
Spectacular! One down, 300 to go. Would you be so kind as to mark the thread as solved using 'Thread Tools' up top? ;)

---

### Post by ecatodarcus on 2010-05-06
yes of course!
thank you very much again!

---

