---
title: "Adjusted input sound volume and Maverick lost the plot..."
date: 2011-05-10
forum: General Help
---

### Post by marlinman on 2011-05-10
Hi friends

I'm running Maverick on an HP dv6 laptop. I tried recording a video via VLC with the machine's 'TrueVision' webcam. The result seemed to lack audio, so I had a look in preferences > sound. The input tab had the mute button ticked, so I unticked it and tried adjusting the level (while realising I was probably just configuring the mic port and not the webcam's inbuilt mics).

Then things turned bad: pointer became sluggish, and changes I made to the level slider took ages to be reflected visually on screen. I queued up a pile of clicks on the 'close' button and went away for a while. On return, I was met with a box inviting me to stop a script with some screen-width-long incomprehensible name, which of course I did.

Now the system's in a state which sees windows missing title bars (tho' not menu bars) and (more problematically) the upper and lower bars on the desktop absent. I issued a hibernate command from the terminal in the hope that on waking the system would be 'fixed', but nothing changed. I tried alt-tabbing to access my open applications and close them gracefully but this command is ignored. I have 'zillions' of apps going with unsaved data and am not sure what to try next. I'd be happy just to be able to task switch to each open prog and exit it gracefully then restart. But my knowledge of the command line is such that your help is required =) .

---

### Post by TheNerdAL on 2011-05-10
I'm assuming you mean a desktop recorder instead of webcam. Try using GTKrecordmydesktop it can record both video and audio from your desktop.

---

### Post by marlinman on 2011-05-10
:confused:

Wow, I clearly need to proofread my posts here more fully; I couldn't care less about the webcam and merely mentioned it for the sake of background info. My problem revolves around my inability to switch tasks thanks to the disappearance of the upper and lower desktop bars. I'd like to restart the system but not before saving vital work!

---

### Post by TheNerdAL on 2011-05-10
Ahhh, then in that case, this link might help you: [http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html](http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html)

---

### Post by marlinman on 2011-05-10
Cheers - nothing whatsoever appeared to happen though :( . (I tried both gconftool and gconftool-2 but did not dare try the --shutdown option...) Interestingly(?), ALT+(FN+)F2 fails to bring up the "Run Application" dialog. Session seems poked but I can't end it before saving open files!

---

### Post by TheNerdAL on 2011-05-11
I'm stuck then, the run application dialog box doesn't open?

---

### Post by marlinman on 2011-05-11
No, it doesn't. But I discovered a way to invoke the system monitor, and was able to use this prog to end the session relatively gracefully. Then tried to reproduce this aberrent behaviour but couldn't... anyway thanks for your help TheNerdAL!

---

