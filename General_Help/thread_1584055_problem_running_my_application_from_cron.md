---
title: "problem running my application from cron"
date: 2010-09-28
forum: General Help
---

### Post by ulrichard on 2010-09-28
When I run my application from the commandline or a script, it works well, but when I try to run it directly or through the same script from cron, it fails with the following message : "critical error : basic_string::_S_construct NULL not valid"

I tried everything that came to my mind and that I found on google, but nothing helped so far. 

/etc/cron.d/flightpred : 
```

SHELL=/bin/sh
MAILTO=richi@paraeasy.ch
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
LD_LIBRARY_PATH=//usr/local/lib:/usr/lib:/lib

#m     h  dom mon dow user  command
# 0    */2  *   *   *  root  /usr/bin/flightpred_train --get-future-weather --forecast --db-maintenance
 0    */2  *   *   *  root  /usr/share/flightpred/flightpred_make_forecast.sh

```

/usr/share/flightpred/flightpred_make_forecast.sh : 
```

#!/bin/sh
# download weather prediction from the GFS and calculate flight forecasts

#/usr/bin/flightpred_train --get-future-weather --forecast --db-maintenance > /tmp/flightpred.log
/usr/bin/flightpred_train --get-future-weather --forecast --db-maintenance

```

What shoudld I look for next?

---

### Post by ulrichard on 2010-09-29
I think I found the problem. 
In the program I used **getenv("USER")** and **getenv("HOME")** which I assumed would always be valid. I run the command as root user in cron. If I type **echo $HOME** or **echo $USER** at the commandline when logged in as root, it shows the proper values. 
But after adding the following two lines to /etc/cron.d/flightpred it works. 
```
HOME=/root
USER=root
```

So I added fallbacks to the respective places in the code as well.
I still don't understand, why the env var were not set when running from cron, but I'm glad it works now.

---

