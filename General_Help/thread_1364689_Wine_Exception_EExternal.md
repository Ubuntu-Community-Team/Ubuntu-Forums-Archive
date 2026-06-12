---
title: "Wine: Exception EExternal"
date: 2009-12-26
forum: General Help
---

### Post by MKVCrazy on 2009-12-26
What I did exactly:

I installed Wine using Synaptic Package Manager.
I ran this command in terminal, "winecfg". and I got the following output:
```
root@XXXXX:~# winecfg
Xlib:  extension "Generic Event Extension" missing on display ":1000.0".
Xlib:  extension "Generic Event Extension" missing on display ":1000.0".
ALSA lib ../../../src/seq/seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Xlib:  extension "Generic Event Extension" missing on display ":1000.0".


```A new Windows-like window poped up. I didn't know what I should be configuring.
Then I closed that window without touching any settings.
I just select my .EXE standalone (500KB-ish) file from desktop and run it with Wine.
Then I see the following error:

[IMG]http://i48.tinypic.com/2h37tl4.png[/IMG]

What may be the cause and how can I fix it?

---

### Post by MKVCrazy on 2009-12-26
Solved. I installed Win1.2 instead.

---

