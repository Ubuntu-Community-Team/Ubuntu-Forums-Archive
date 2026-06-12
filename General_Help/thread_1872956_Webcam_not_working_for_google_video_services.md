---
title: "Webcam not working for google video services"
date: 2011-10-31
forum: General Help
---

### Post by xtracool_protik on 2011-10-31
I've Ubuntu 11.10 64 bit and have installed google video chat plugin. However webcam doesn't seem to work (black screen -- no video at all though webcam led is ON). For cheese it works but shows really bad (black and white kinda) image. Following some link I installed guvcview if I start it then image looks neat.

Any suggestions on how can it be fixed?

Thanks

---

### Post by xtracool_protik on 2011-11-01
bump...

---

### Post by linuxwin2 on 2011-11-03
```
$sudo mv /opt/google/talkplugin/GoogleTalkPlugin /opt/goog/talkplugin/GoogleTalkPlugin.old
$sudo gedit /opt/google/talkplugin/GoogleTalkPlugin
put in



#!/bin/sh
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /opt/google/talkplugin/GoogleTalkPlugin.old
 $ chmod +x /opt/google/talkplugin/GoogleTalkPlugin.old

```

---

### Post by xtracool_protik on 2011-11-03
Thanks, 
 But last time I tried that method, unrealistic CPU usage occured [http://askubuntu.com/questions/73639/what-are-kswapd0-kworker-numnum-ksoftirqd-num/](http://askubuntu.com/questions/73639/what-are-kswapd0-kworker-numnum-ksoftirqd-num/)
 I'll try it again though, as last time I tried quite a few methods to get google video working so maybe something else as well.

---

### Post by xtracool_protik on 2011-11-03
Anyways tried again and no help and no this was not the reason for unrealistic CPU I guess :confused:

---

