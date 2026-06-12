---
title: "Setting up Sound"
date: 2011-04-25
forum: General Help
---

### Post by tnguyen9175 on 2011-04-25
I just recently downloaded Ubuntu 10.10 for my Dell Inspiron. So far, so good.

i have figured the majority of my problems, but one that is still giving me problems is my sound. I have selected my sound card as my output, but still nothing in the test. If anyone could guide me in a direction, it would be appreciated.

Thanks!

---

### Post by veggen on 2011-04-26
I once fixed a no-sound issue by entering alsamixer (just type it into the terminal) and unmuting all channels and cranking up the volume there.

---

### Post by KegHead on 2011-04-26
Hi!

Have you tried:

system...admin...additional drivers?

KegHead

---

### Post by tnguyen9175 on 2011-04-26
No I haven't. Where can I download them?

---

### Post by KegHead on 2011-04-26
Hi!

At the top of your screen (bar)

GoTo:

system...admin....additional drivers..

KegHead

---

### Post by K_45 on 2011-04-26
What is the output of

```
aplay -l
```

If that spits something out, enter this:

```
lspci -vv | grep *codec*
``` replacing codec with the codec (such as HDA).

---

