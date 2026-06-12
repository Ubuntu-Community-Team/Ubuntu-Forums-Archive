---
title: "help with ffmpeg"
date: 2006-05-13
forum: General Help
---

### Post by Bleppe on 2006-05-13
I'm trying to convert a 45 minute raw dv file to svcd using ffmpeg, it looks nice but i think it could look even better using 2 pass or dc-10 variables. only problem is, that i can't seem to put these flags in the right place.. also the maximum bitrate for svcd is 2500, the target only uses 2040. could i modify the target profile somehow?

> ffmpeg -i 1.dv -target svcd  /tmp/vcd.mpg works fine and looks good to, but then i tried adding -2 pass or -hq it got mad :-k anyone got a sample script i could look at?

---

