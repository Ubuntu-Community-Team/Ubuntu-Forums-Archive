---
title: "Mplayer error"
date: 2010-04-29
forum: General Help
---

### Post by sunnyengineeer on 2010-04-29
Hello,  

        Im getting a wierd error whenever I try to play a file be it audio or video.
It shows 

[COLOR=Red]"[AO-ALSA] Unable to find simple control 'PSM',0"

[COLOR=Black]I have a Nvidia(alsa Mixer sound card)[/COLOR]
[/COLOR]
Can somebody plz tell e how to resolve it?

Thanks
Sunny Sharma

---

### Post by sisco311 on 2010-05-01
Try to use a different mixer channel:
```
mplayer -mixer-channel Master path/to/file
```

If it works append the ~/.mplayer/config file with **mixer-channel=Master**.

---

