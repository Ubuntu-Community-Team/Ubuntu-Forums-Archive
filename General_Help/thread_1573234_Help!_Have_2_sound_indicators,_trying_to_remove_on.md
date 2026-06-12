---
title: "Help! Have 2 sound indicators, trying to remove one!"
date: 2010-09-12
forum: General Help
---

### Post by The Bright Side on 2010-09-12
This is a bit of an odd problem, I hope you can help me. When I installed Lucid a couple months ago, I removed the sound/messages indicator from my panel and *somehow* installed a single sound indicator in my panel.

Now, I want to revert that. I put the message/sound indicator back, but for the life of me, I can't remember how to get rid of the single sound indicator anymore...

The one I want to remove is highlighted red in the attached screenshot. I don't remember how I got it there in the first place (I found some tutorial online and did it), and now I can't get rid of it no matter what I do :-(

Hope you can help me!!

Thanks,
M.

---

### Post by mirchichamu on 2010-09-12
Right click on the applet and select remove.

---

### Post by The Bright Side on 2010-09-12
That would be the obvious choice, and it's what I tried first. Doesn't work. All I get is "Mute" and "Sound Preferences"...

---

### Post by mirchichamu on 2010-09-12
Then you delete the upper panel and then paste the following command in terminal and restart the system. It will bring the original panel again. Once I deleted my panel and brought it back by this command.

code:     gconftool-2 --recursive-unset /apps/panel

---

### Post by The Bright Side on 2010-09-12
Got it! It was in the Startup Applications... I really don't know why I didn't think of that right away. Thanks for your help, and for the command, it's a good one to remember.

---

