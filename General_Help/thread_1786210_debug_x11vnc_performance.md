---
title: "debug x11vnc performance"
date: 2011-06-19
forum: General Help
---

### Post by michalre on 2011-06-19
Hi,

I would like to be able to get some data from x11vnc process to determine where is the bottleneck for me. Essentially I need to benchmark particular stages the x11vnc and vnc client work - from change detection to display of data on the client screen.

For example: how much screen change is x11vnc seeing, compression ratio of these changes; frame size; latency between change is detected and data is sent over the network; and more, not sure how exactly x11vnc internally works any reading material would be very appreciated 

Thanks,
Michal

---

### Post by krunge on 2011-06-20
This might get you started...

If you run x11vnc with the "-forever" option, then when a viewer disconnects some statistics are printed out:
```

19/06/2011 22:38:27 Client 127.0.0.1 gone
19/06/2011 22:38:27 Statistics             events    Transmit/ RawEquiv ( saved)
19/06/2011 22:38:27  ServerCutText       :      1 |         8/        8 (  0.0%)
19/06/2011 22:38:27  FramebufferUpdate   :     31 |         0/        0 (  0.0%)
19/06/2011 22:38:27  LastRect            :     13 |       156/      156 (  0.0%)
19/06/2011 22:38:27  tight               :    575 |    213514/  3504756 ( 93.9%)
19/06/2011 22:38:27  PointerPos          :      1 |        12/       12 (  0.0%)
19/06/2011 22:38:27  RichCursor          :      1 |       726/      726 (  0.0%)
19/06/2011 22:38:27  TOTALS              :    622 |    214416/  3505658 ( 93.9%)
19/06/2011 22:38:27 Statistics             events    Received/ RawEquiv ( saved)
19/06/2011 22:38:27  PointerEvent        :     21 |       126/      126 (  0.0%)
19/06/2011 22:38:27  FramebufferUpdate   :     32 |       320/      320 (  0.0%)
19/06/2011 22:38:27  SetEncodings        :      1 |        64/       64 (  0.0%)
19/06/2011 22:38:27  SetPixelFormat      :      1 |        20/       20 (  0.0%)
19/06/2011 22:38:27  TOTALS              :     55 |       530/      530 (  0.0%)

```

Also, if you run with the "-debug_tiles" option you will get some strange looking output regarding screen changes, e.g.:
```

============================= TILES: 99  dt: 0.0508  t: 4.9359  3.99 MB/s nap_ok: 0
============================= TILES: 8  dt: 0.0110  t: 4.9895  1.48 MB/s nap_ok: 0
============================= TILES: 0  dt: 0.0072  t: 5.0214  0.00 MB/s nap_ok: 0
============================= TILES: 8  dt: 0.0115  t: 5.0750  1.43 MB/s nap_ok: 0

```
The main thing to remember is that for x11vnc a "tile" is a 32x32 pixel patch on the screen.  So "TILES: 99" means 99 changed tiles were detected and read in from the screen.

If you supply that option twice you will get even more output, including when there are no screen changes... it might look like a big mess.

There may be some more profiling things inside x11vnc but that's all I can remember. It is also possible to turn on XDAMAGE debug output and if willing to recompile turn on ascii print out of the locations of the changed tiles (ask if you are interested in either one)

Please also say what your framebuffer read rate is reported to be. E.g.:
```
19/06/2011 23:54:26 fb read rate: 9 MB/sec
```
A low framebuffer read rate (like the above) can make things laggy because it takes so long just to read changed pixel regions in from the screen (the video RAM)

---

