---
title: "A way to have rsync do multip remote host's"
date: 2009-10-09
forum: General Help
---

### Post by Schwyl on 2009-10-09
I have 4 servers. we will call them server1 server2 server3 server4

server1 pushes files to all the other servers it will be the one with the cron jobs scheduled.
server1 has a directory structure of /home/media/
server1 within the /home/media/ directory has sub directories 1-10
server2 only wants directories 1,3,5,7,9
server3 only wants directories 1,2,3,4,5
server4 only wants directories 1,5,10

How can i write a script that cron can run to do this?

I found this script online somewhere

#!/bin/sh

RSYNC=/usr/bin/rsync
SSH=/usr/bin/ssh
KEY=/home/thisuser/cron/thishost-rsync-key
RUSER=remoteuser
RHOST=remotehost
RPATH=/remote/dir
LPATH=/this/dir/

$RSYNC -az -e "$SSH -i $KEY" $RUSER@$RHOST:$RPATH $LPATH 

Could i just specify multiple rpath and lpaths?

Take server2 for example

#!/bin/sh

RSYNC=/usr/bin/rsync
SSH=/usr/bin/ssh
KEY=/home/thisuser/cron/thishost-rsync-key
RUSER=rsync
RHOST=test.com
RPATH=/home/media/1
LPATH=/home/media/1
RPATH=/home/media/3
LPATH=/home/media/3
RPATH=/home/media/5
LPATH=/home/media/5
RPATH=/home/media/7
LPATH=/home/media/7
RPATH=/home/media/9
LPATH=/home/media/9

$RSYNC -az -e "$SSH -i $KEY" $RUSER@$RHOST:$RPATH $LPATH

---

