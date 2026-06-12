---
title: "HDMI + adobe flash = nothing;"
date: 2012-02-24
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2012-02-24
after much pain stacking work i managed to get hdmi sound working and got my sounds playing on analog and hdmi (music, sound effects)
now for that evil #$&^# adobe flash
it will not play over the hdmi i even disabled the analog audio in the bios and it would not play over hdmi...
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=213207&stc=1&d=1330124939[/IMG]
so my working audio cards are 
hwplug:0,0  (speaker-test -Dplughw:0,0 -c2)
hwplug:1,9  (speaker-test -Dplughw:1,9 -c2)

---

### Post by pqwoerituytrueiwoq on 2012-02-24
figured it out [credit](http://ubuntuforums.org/showpost.php?p=9426758&postcount=17)
```
~$ cat /etc/asound.conf
pcm.pulse {
type pulse
}
ctl.pulse {
type pulse
}
pcm.!default {
type pulse
}
ctl.!default {
type pulse
}
```

---

