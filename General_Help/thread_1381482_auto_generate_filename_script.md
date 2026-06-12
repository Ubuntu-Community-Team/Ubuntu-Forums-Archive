---
title: "auto generate filename script?"
date: 2010-01-14
forum: General Help
---

### Post by snares on 2010-01-14
I am attempting to create a script that will auto convert multiple dvds to ISOs. I got the ripping part done. But I don't want to keep changing the output file name. Surely there is a way to make the script find the name of the cd and put that in as the iso name? Any links on scripting for bash would help. Or you could just tell me. That would be even better. I have limited scripting knowledge.Though I have used many scripts none very much.

cheers

---

### Post by diesch on 2010-01-14
```
lsdvd| awk -F: '/^Disc Title:/ {print $2}'
``` should give you the DVD title

---

