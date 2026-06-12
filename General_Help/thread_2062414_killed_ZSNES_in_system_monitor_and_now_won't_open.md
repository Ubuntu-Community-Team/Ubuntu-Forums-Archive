---
title: "killed ZSNES in system monitor and now won't open"
date: 2012-09-24
forum: General Help
---

### Post by 777funk on 2012-09-24
I have restarted and no avail. I removed it through Terminal and reinstalled. Every time I click the ZSNES icon it opens full screen (or at least something happens) screen goes black for a split second then nothing more and it's as if I never clicked anything. I don't see it running in System Monitor either.

Any ideas?

Here's what I get when I open in Terminal:
> Starting Mouse detection.
Unable to poll /dev/input/event11. Make sure you have read permissions to it.
Unable to poll /dev/input/event10. Make sure you have read permissions to it.
Unable to poll /dev/input/event9. Make sure you have read permissions to it.
Unable to poll /dev/input/event8. Make sure you have read permissions to it.
Unable to poll /dev/input/event7. Make sure you have read permissions to it.
Unable to poll /dev/input/event6. Make sure you have read permissions to it.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.
Segmentation fault (core dumped)


---

### Post by Caltac on 2012-09-24
Well it says that you don't have permission to read it, so did you try running it as root?

---

### Post by 777funk on 2012-09-25
I opened as root and it worked once but now does what it does if I don't open the program as root. Flickers the screen to black once and that's it.

---

### Post by pudlonious on 2012-09-25
I have the same problem above. I am using Ubuntu 12.04 64bit. Could that be the problem?

---

### Post by 777funk on 2012-09-25
UPDATE: went to Home Folder and clicked the show hidden folders option. Deleted .ZSNES folder and started ZSNES. Works!

AND I FIGURED OUT THE PROBLEM. Do NOT hit the Maximize button in ZSNES. I always just go to options/video in ZSNES and size the non full screen (Windowed) to fit my monitor. This has been working well. No crashes since.

---

### Post by pudlonious on 2012-09-25
Thanks 777funk for the advice. It works perfectly.

---

