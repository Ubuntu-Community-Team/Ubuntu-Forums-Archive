---
title: "WIFI dongle =&gt; Ubuntu won't start up"
date: 2010-05-18
forum: General Help
---

### Post by Artiom.Fiodorov on 2010-05-18
I got myself LM Technologies WIFI dongle, which worked out of box. (it shows as zydas usb 2.0 wlan device)
But my Ubuntu won't load with it - it will die after showing splash screen. Whereas without it Ubuntu loads just fine.
How do I identify the problem? Any possible solutions?

---

### Post by dvlchd3 on 2010-05-18
Two things to try.

With the dongle in, boot up.  As soon as the splash screen shows, press Ctrl+Alt+F1 this will bring up the text mode, which may provide some diagnostic information.

Otherwise, cause Ubuntu to crash on startup (with the dongle in).  Then remove the dongle, start up, and run:
```

dmesg

```

This will probably be rather long, but you should be able to scroll through it and find some diagnostic information close to the bottom.

p.s. - you could also write the output to a file and view that:
```

dmesg > ~/dmesg.log
gedit ~/dmesg.log &

```
This may make it a little more readable for you.

---

### Post by Artiom.Fiodorov on 2010-05-18
I did as you told and I am trying to identify what caused Ubuntu to crash now, but I am not very experienced. May be someone more experienced could tell me what went wrong and when?
Log is attached.

---

### Post by Artiom.Fiodorov on 2010-05-19
turned out to be a known bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/359197](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/359197)

---

### Post by philinux on 2010-05-19
@artiom, are you using 9.04 or a later version of Ubuntu.

---

### Post by Artiom.Fiodorov on 2010-05-19
I am using Lucid 10.04: 2.6.32-22-generic #33-Ubuntu SMP (x86_64)
I just added my [dmesg.log.tar.gz]("http://ubuntuforums.org/attachment.php?attachmentid=157372&d=1274184309") to [https://bugs.launchpad.net/ubuntu/+s...ux/+bug/359197]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/359197")

---

