---
title: "will this script work?"
date: 2011-04-23
forum: General Help
---

### Post by sr_guy on 2011-04-23
I want to capture a mms stream daily. All works well with that, but I also want to delete any mpg files that are captured from the stream that are more than 7 days old. Will this command work?


```

#!/bin/bash
find /mnt/tera/all_video/thai3 -ctime +7 -name "*.mpg" -exec rm -f {} \; -ls > /var/log/thai3.log 2>&1
cd /mnt/tera/all_video/thai3
mplayer -dumpstream -dumpfile "thai_chan3-`date +%B.%d.%Y_%H:%M`.mpg" mms://iptv.psru.ac.th/E27101

```

---

### Post by Habeouscorpus on 2011-04-23
One suggestion: The first line could be run as a cron job, and it looks like that last command would run continuously. You need to build in a time out where it could write to file, then continue. 

Good idea with the logs; it's a pretty clever idea. But you might want to add a verbose arguement, else you'll get nothing.

Just my $.02, I may be wrong.

---

### Post by sr_guy on 2011-04-24
I set up a separate cronjob to run:

killall -9 mplayer

to stop the stream capture after 2 hrs.


I see what you mean about this running continuously, I'll make a separate cronjob for that 

find /mnt/tera/all_video/thai3 -ctime +7 -name "*.mpg" -exec rm -f {} \; -ls > /var/log/thai3.log 2>&1

---

