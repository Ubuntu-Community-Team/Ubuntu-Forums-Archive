---
title: "Simplify Media on Ubuntu Server"
date: 2009-08-28
forum: General Help
---

### Post by mocka on 2009-08-28
I have now struggled for some time trying to install and use Simplify Media on a box with Ubuntu Server. Though no success. Is there anyone who has succeeded to do this? If so; please tell me how you did it.

---

### Post by Sean Whitney on 2009-11-01
I installed simplifymedia in /usr/local/bin/simplifymedia.  The following script works great out of cron.  I run it every 5 minutes.

#!/bin/sh

PID=$(/bin/ps ax | grep Simplify | grep -v grep | awk {'print $1'} | head -n 1)
if [ "$PID" ];
then
#  echo "Simplify is running"
  exit
else
   cd /usr/local/bin/simplifymedia/

  ./simplifyserver.sh -n <user.name> -l <servername> -p <password> -s /path.to.music.files
fi

---

