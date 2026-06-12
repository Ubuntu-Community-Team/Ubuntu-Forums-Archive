---
title: "i need a program to schedule audio recordings"
date: 2009-09-16
forum: General Help
---

### Post by kg4tah on 2009-09-16
I want to hook up a radio to my line in jack to record a radio program at a set time everyday. Is there any program that will auto record at set times everyday?

---

### Post by Girya on 2009-09-16
install lame if it isn't. and create a script file with this command in it with the obvious things changed. (numberofseconds and out.mp3) and create a cron job to run when your radio program plays. 

> arecord -f cd -d numberofseconds -t raw | lame -x -r – out.mp3 

disclaimer: I haven't done this myself but it seems fairly straightforward. If it doesn't work at least this should point you in the right direction. 

kevin

---

### Post by tgalati4 on 2009-09-17
If the radio program is streamed on the internet, then you can use streamripper to record it.

man crontab

You can use crontab to run a recording script at the same time every day or every week.  Search the forums for crontab, there are numerous examples.

---

### Post by kg4tah on 2009-09-17
Thanks for all your help guys!

---

### Post by -=hazard=- on 2009-09-17
you can use arecord or mplayer. Create this script

```
#!/bin/bash
cd folder_whereto_save
mplayer stream_url -dumpstream -dumpfile namefile.mp3 &
sleep 1h
kill $!
```

Where sleep 1h (1 hour) is the time that mplayer or arecord will capture the stream, after that it will stop. You can schedule the start with cron and with this little script you can schedule the end too.
Cheers.

---

### Post by andrew.46 on 2009-09-17
Hi -=hazard=-,

> **-=hazard=- said:**
> 
```

mplayer stream_url -dumpstream -dumpfile namefile.mp3 &

```


This will work nicely if the stream is *actually* an mp3 stream. If it is not dumpstream/dumpfile will not convert it to mp3 but simply label it as mp3. An alternative is to use *-ao pcm* and subsequently convert to mp3 or to simply use dumstream/dumpfile to save the stream with its *native* format.

All the best,

Andrew

---

### Post by -=hazard=- on 2009-09-18
Hello andrew. 
Yes you are totally right. But I'm used to listen always mp3 streams and I just did copy/paste the script from mine :) I guess for original format it would be:

```
#!/bin/bash
cd folder_wehreto_save
mplayer stream_url -dumpstream &
sleep 1h
kill $!
```

---

