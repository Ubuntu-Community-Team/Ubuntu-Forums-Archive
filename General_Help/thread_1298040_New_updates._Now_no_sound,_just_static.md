---
title: "New updates. Now no sound, just static?"
date: 2009-10-22
forum: General Help
---

### Post by MarkStarCrashes on 2009-10-22
So, I woke up this morning and found some updates waiting for 9.04 and I went ahead and installed them and now I have no sound. That is to say my speakers don't work, all I get is a crackling sound when a sound should be playing.

(As a side note this doesn't seem to have affected the annoying shut-down beep.)

What to do, what to do?:(

---

### Post by MarkStarCrashes on 2009-10-22
Anybody?  

Is there a way to learn what the updates were so I can try to uninstall whichever might be audio related?


:(

---

### Post by P4man on 2009-10-22
Run ```
alsamixer
``` from a terminal and verify nothing is muted. especially pcm channel. Seen that happen after an update.

---

### Post by MarkStarCrashes on 2009-10-22
> **P4man said:**
> Run ```
alsamixer
``` from a terminal and verify nothing is muted. especially pcm channel. Seen that happen after an update.

Thanks for the help.

It does seem to my unlearned eye that the PCM channel has become muted. How can I un-mute it?

[IMG]http://img63.imageshack.us/img63/1433/screenshotmarkstarmarks.png[/IMG]

---

### Post by P4man on 2009-10-22
use the arrow keys to navigate left right and up down to adjust volume. M if there is a mute option

alternatively, open the volume control of ubuntu and enable all mixers (inculuding pcm)

---

### Post by MarkStarCrashes on 2009-10-22
> **P4man said:**
> use the arrow keys to navigate left right and up down to adjust volume. M if there is a mute option

alternatively, open the volume control of ubuntu and enable all mixers (inculuding pcm)

Well, that was so easy that I am almost embarrassed.

Thank you kindly for your assistance. :)

---

### Post by P4man on 2009-10-22
No problem. Dont forget to mark the thread solved.

---

### Post by MarkStarCrashes on 2009-10-22
And now I had to reboot and I find that the PCM channel is once again muted.

Why would it keep on being muted every time I reboot?

---

### Post by MarkStarCrashes on 2009-10-23
And now with some new Updates today the problem seems resolved.

Good job, Ubuntu! 

This was the exact reason why I moved away from Windows (bad updates screwing up system) and am glad to see you are on top of things.

---

