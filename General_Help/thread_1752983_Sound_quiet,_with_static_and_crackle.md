---
title: "Sound quiet, with static and crackle"
date: 2011-05-08
forum: General Help
---

### Post by Chonnawonga on 2011-05-08
I have a problem with my sound that just cropped up today. Any and all sound from any program is quieter than usual and generates a lot of static. It sounds like there's a bad connection somewhere. It's not a hardware problem, since I can boot into Windows on the same system and the sound is fine.

The only changes I've made to the system today are to run the regular updates and to update Wine.

Anyone else having this problem? Any suggestions?

---

### Post by Chonnawonga on 2011-06-24
Problem solved. Somehow a mic channel was on, and I couldn't turn it off through the Pulse volume controls. So, I ran this:
```
$ alsamixer -Dhw
```
and turned the "Front Mic" channel down to 0. Seems to be fine now.

---

