---
title: "How to detect hardware mixing in soundcard"
date: 2006-06-08
forum: General Help
---

### Post by mk1970 on 2006-06-08
Is there any reliable method to detect (by using only command-line tools like grep) if a soundcard supports hardware mixing? I see there are few files in /proc/asound but I really can't tell if my card support HW mixing or not. I'm really guessing here but does IMIX mean "input mixing" and 0 means "no"?

```

# grep -ri mix /proc/asound
/proc/asound/ICH5/oss_mixer:IMIX "" 0
/proc/asound/ICH5/codec97#0/ac97#0-0:Mono output      : MIX
/proc/asound/card0/oss_mixer:IMIX "" 0
/proc/asound/card0/codec97#0/ac97#0-0:Mono output      : MIX
/proc/asound/oss/sndstat:Mixers:
/proc/asound/oss/devices:  0: [0- 0]: mixer

```

Could someone with a soundcard which is known to support hardware mixing run the same grep command and show the result here...

---

