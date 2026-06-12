---
title: "Limiting size of mkisofs output?"
date: 2011-12-21
forum: General Help
---

### Post by Curse on 2011-12-21
I have a video that is in the VIDEO_TS format that I want to make into an ISO. I used the mkisofs command (specifically: mkisofs -dvd-video -o ./Videos/Hangover\ 2.iso ./Downloads/THE_HANGOVER_2/

The problem is the output file is 4.9 GB. Is there a way to limit it to 4.37 GB so I can actually burn it? :p

---

### Post by mcduck on 2011-12-21
You need to decrease the size of the video file itself. There's nothing else you could possibly do to reduce the size of the resulting image.

...and of course make sure you aren't just running into the difference between GiB and GB. ;) (4,9 GB = 4,56 GiB)

---

### Post by andrew.46 on 2011-12-21
Or perhaps invest in some dual layer dvd disks, the Verbatim ones work well for me...

---

