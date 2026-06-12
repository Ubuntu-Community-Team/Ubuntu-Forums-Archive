---
title: "Sometimes arrow keys don't work in console"
date: 2009-09-18
forum: General Help
---

### Post by wrb302 on 2009-09-18
This has bother me for a long time. Normally everything is ok, but in SOME console environment, press arrow key will not correctly move the cursor, but instead display some strange charactors, e.g.  "^[[A" for left arrow key, "^[[B" for right arrow key.

The easiest way to reproduce this is to test it in scala interactive environment.("sudo apt-get install scala & scala".)

I am using Jaunty on a Dell D630 laptop.

Can anyone give me some clue on this? Thanks!

---

### Post by lloyd_b on 2009-09-19
> **wrb302 said:**
> This has bother me for a long time. Normally everything is ok, but in SOME console environment, press arrow key will not correctly move the cursor, but instead display some strange charactors, e.g.  "^[[A" for left arrow key, "^[[B" for right arrow key.

The easiest way to reproduce this is to test it in scala interactive environment.("sudo apt-get install scala & scala".)

I am using Jaunty on a Dell D630 laptop.

Can anyone give me some clue on this? Thanks!

The most likely possibility is that when scala spawns the terminal emulator, it it not setting the TERM environment variable correctly.  When this happens, the terminal emulator no longer understands that it's supposed to translate that "^]]A" to "left arrow", etc.

Try "echo $TERM" in a normal console window, and again in a window opened within scala, and see if it is being set the same both ways.

Lloyd B.

---

### Post by wrb302 on 2009-09-20
sounds reasonable. But I don't know how to test $TERM in scala interactive environment.

---

