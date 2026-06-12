---
title: "Kernel spamming logs full &quot;display port opened&quot; and &quot;display port closed&quot;"
date: 2011-04-04
forum: General Help
---

### Post by ult_avatar on 2011-04-04
Hi,

I have the following problem:

syslog is constantly writing to disk, because the kernel spams these messages
```

Apr  4 14:14:56 aspire kernel: [138498.252610] display port opened
Apr  4 14:14:56 aspire kernel: [138498.299755] display port closed
Apr  4 14:14:57 aspire kernel: [138499.328206] display port opened
Apr  4 14:14:57 aspire kernel: [138499.371835] display port closed
Apr  4 14:14:58 aspire kernel: [138500.452671] display port opened
Apr  4 14:14:58 aspire kernel: [138500.499906] display port closed
Apr  4 14:14:59 aspire kernel: [138501.528276] display port opened
Apr  4 14:14:59 aspire kernel: [138501.571988] display port closed

```

As you can see, it's writing two messages per second, so my logfiles are rather large ( over 200MB if added together).

It hasn't bothered me much in the past, other than constantly "grepping it out" if I wanted to read either syslog, messages or kern.log.
However, since I recently exchanged my 3,5" HDD to a 2,5" HDD I'm trying to minimize 'unnecessary' writes-to-disk to improve I/O performance.

Just to be clear, I do not have a DisplayPort as described here [http://en.wikipedia.org/wiki/DisplayPort]("http://en.wikipedia.org/wiki/DisplayPort"). 
I'm using a built-in HDMI port. I don't know if that even matters.


Specs are:
Core 2 Quad Q8300 4x 2.50GH
8 GB RAM
2,5" Toshiba MK7559GSXP 
Mainboard is Acer Aspire X3800 Series (X3812 I believe)

Ubuntu 9.10 Karmic 
Linux aspire 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux

I'm mainly using the Linux Box for playback via LIRC(VLC, rhythmbox) but also for torrents (torrentflux-b4rt) and extracting large files. Also installed but not frequently used: mythtv, mytv and gallery3

Hope you have some insights as I can't figure out what is causing this...

---

### Post by ult_avatar on 2011-04-09
bump

---

