---
title: "How to invoke a plug-in at start up?"
date: 2009-12-12
forum: General Help
---

### Post by jotto! on 2009-12-12
After having major issuses with distortion free sound under ubuntu 9.10 and a 5 speaker setup, I have found a work around.

I believe 9.10 uses Pulse for audio. I tried removing it and just using ALSA. Can anyone tell me of a command to type in to terminal or a file to ammend to make ALSA use 6 channels instead of the default 2. Im sure I found this before but can now not find it...

Anyway, back to the work around. I found that under pulse, I had a high pitched distortion in my sound. This disappeared if I opened 2 applications using sound and then muted one.

I then found by accident that whilst browsing, Firefox invoked an ALSA plug-in. This also solved the issue.

**So my main question is, How do I invoke the ALSA plug-in to run at boot?**

---

### Post by jotto! on 2009-12-12
Bump for the gurus out there!

---

### Post by jotto! on 2009-12-13
Failing that, can I set firefox to start at boot?

---

