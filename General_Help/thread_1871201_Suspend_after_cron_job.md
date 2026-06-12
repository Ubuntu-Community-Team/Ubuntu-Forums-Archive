---
title: "Suspend after cron job"
date: 2011-10-28
forum: General Help
---

### Post by mybrain87 on 2011-10-28
I'm in need of some help.

I'm running the following script from cron.

#!/bin/bash

login=**
pass=**
host=**
remote_dir=./private/rtorrent/data/
local_dir=../media/BitTorrent/Feral/


trap "rm -f /tmp/synctorrent.lock" SIGINT SIGTERM

if [ -e /tmp/synctorrent.lock ]
then
 echo "Synctorrent is running already."
 exit 1
else

 touch /tmp/synctorrent.lock

 lftp -u $login,$pass $host << EOF
 set ftp:ssl-allow no
 set mirror:use-pget-n 5
 mirror -c --parallel=5 --log=synctorrents.log $remote_dir $local_dir
 quit
EOF

 rm -f /tmp/synctorrent.lock
 exit 0

fi


In cron if got the following line:

10 * * * * /home/xbmc/synctorrents.sh >> /home/xbmc/sync_cron.log 2>&1



What I'd like to have now, is that my machine automatically suspends for 2 hours after the cron job is done, which can differ in its length, and then wake up and run the cron job again and then go to sleep again for 2 hours and so on.

what do i have to add to the cron or the script to make this happen?

---

