---
title: "Strange things"
date: 2011-01-20
forum: General Help
---

### Post by Spyderkid on 2011-01-20
I installed a DVD ripper and I found a executable file with its name in my home directory I just wondered if there was anything unusual in it (I removed the program but this still remained) also I shredded the file because I didn't need it. here are the contents of the file:

```

#!/bin/sh
echo "***********************************************************"
echo "Automated script created by AcidRip - http://acidrip.sf.net"
echo "***********************************************************"
unlink frameno.avi 2> /dev/null
mencoder dvd://1 -dvd-device /dev/dvd  -alang English   -info srcform="DVD ripped by acidrip.sf.net" -oac mp3lame -lameopts abr:br=128  -ovc lavc -lavcopts vcodec=mpeg4:vhq:v4mv:vqmin=2:vbitrate=5000 -vf pp=de,crop=0:0:0:0,scale=480:-2    -o "/home/bob/bbcdvd1281.avi"

```

---

### Post by ysangkok on 2011-05-19
Nothing unusual.

---

