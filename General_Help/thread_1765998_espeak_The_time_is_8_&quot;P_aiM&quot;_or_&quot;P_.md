---
title: "espeak: The time is 8 &quot;P /ai/M&quot; or &quot;P /i/M?&quot;"
date: 2011-05-23
forum: General Help
---

### Post by GraysonPeddie on 2011-05-23
I need to change how espeak pronounces the "M" in "PM." What I have heard is that espeak speaks like "The time is 8 P aim" as in "spam" or "bam." But I might be thinking that espeak opens its mouth wide open as it says "M" in "PM." What I want espeak to sound is if it speaks "M" as in "slim" with a short "i" sound. Or maybe something like "spring." So how do I modify espeak so that the "PM"-- hmm... I don't think I can describe it in words, but maybe I could make two WAV files with "PM" sounding differently between two files.

Does anyone understand what I'm asking for? Sure, I did break a question with a statement, but I do have trouble being clear what I'm trying to do by changing the way espeak pronounces. I am using Ubuntu Server 10.04 and the time gets spoken every hour by using cron.

crontab -e:

```
0 * * * * /fileserver/shell_scripts/saytime
```

My script (saytime):

```
#!/bin/bash
# Say time
DATE=$(date '+%l %p')
padsp espeak -ven+m3 -a 100 -p 40 -s 140 "The time is -- $DATE";
```

---

