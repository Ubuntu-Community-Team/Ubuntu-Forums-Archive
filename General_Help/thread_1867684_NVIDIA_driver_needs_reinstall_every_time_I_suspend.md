---
title: "NVIDIA driver needs reinstall every time I suspend"
date: 2011-10-23
forum: General Help
---

### Post by J V on 2011-10-23
[SOLVED]: Was caused by noexec /tmp, I thought that was supposed to be noexec? :O

Custom alternate install with driver direct from nvidia.

All opengl applications segfault (xscreensaver, wine etc) after a pm-suspend, after which I have to reinstall my nvidia driver to regain 3d rendering.

This is really annoying. Please help.

```
Lucid lynx
Linux *** 2.6.38-11-generic #50~lucid1-Ubuntu SMP Tue Sep 13 21:53:24 UTC 2011 x86_64 GNU/Linux
NVIDIA-Linux-x86_64-285.05.09
``````
Backtrace:
=>0 0x7ad913e5 in libnvidia-glcore.so.285.05.09 (+0x10d53e5) (0x7c9b88d0)
  1 0x7c9dbbf8 (0x7c9dbbf8)

```

---

