---
title: "Xorg help"
date: 2011-11-26
forum: General Help
---

### Post by armaskywalker on 2011-11-26
Hi guys, today i have installed ati drivers from: [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)
After install it i have problem to run X, this because i have 2 card Intel/Ati.
I tried to use vgaswitcheroo for power off intel card, but vga switcheroo say: No such file or directory
Then i have run Xorg -configure from terminal and have create a xorg.conf.new.

utils:
```
arma ~ $  lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5000 Series]
```

xorg.conf.new is this:
[http://pastebin.com/gt0Mm4nV](http://pastebin.com/gt0Mm4nV)
Is too long, how i use it? or how to use intel card where i run (in older xorg.conf) sauerbraten and other game perfectly?
p.s i have lost my older conf..
Thanks guys and sorry for my bad english

---

