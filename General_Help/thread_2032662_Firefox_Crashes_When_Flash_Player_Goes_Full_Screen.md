---
title: "Firefox Crashes When Flash Player Goes Full Screen"
date: 2012-07-24
forum: General Help
---

### Post by SillySod on 2012-07-24
I don't think this is a new problem, but I haven't seen anything addressing the issue recently, and it has only just started happening to me in the last couple of weeks.

I am using Ubuntu 11.04 and have been keeping it up to date with all the updates which come through.

When browsing a web page with flash video, if I go full-screen, the page crashes just at the point where the message "press ESCAPE to exit full screen" is about to fade away. Eventually I get a message saying the flash plug-in has crashed, but this takes a few minutes.  To get out more quickly, I have to switch to another workspace with the keyboard and then start the System monitor and kill the Plug-in container.

I have put the line

```
export LD_PRELOAD=/usr/lib/libGL.so.1
```

in my firefox.sh file in usr/lib/firefox, near the beginning, as recommended by several sites, but this hasn't made any difference.

What else could I try please?

---

### Post by dino99 on 2012-07-24
to use full screen your graphic card needs some power and ram

---

### Post by SillySod on 2012-07-24
Is there some way to allocate more RAM to the graphics card?

I can't really understand why it has worked fine for 18 months and then this fault has developed in the last couple of weeks.

---

### Post by pqwoerituytrueiwoq on 2012-07-24
what is your hardware?

---

### Post by SillySod on 2012-07-24
The problem machine in question is my little Notebook, according to the label next to the pad it's 1GB DDR3 Memory, Intel R Atom TM N455, Intel R Graphics Media Accelerator 3150.

Hope this helps!

---

