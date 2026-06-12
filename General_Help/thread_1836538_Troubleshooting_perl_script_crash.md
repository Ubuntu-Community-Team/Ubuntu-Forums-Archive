---
title: "Troubleshooting perl script crash"
date: 2011-08-31
forum: General Help
---

### Post by jmumby on 2011-08-31
I have a perl script that starts at boot time. I have added it to the startup ...

```
/usr/bin/xterm -e perl /home/user/email2sms.pl
```

Boots perfectly and I leave this running 24/7. Lately I have found the script has stopped/crashed. The terminal is missing and the email to sms has obviously stopped. 

How would I go about fault finding as to why this is happening. i.e what logs should I look at? The script used to display a '.' every time it did a mail check. Perhaps this has filled up some buffer and shut down the script? I have removed this now. 

Thx

---

### Post by dethorpe on 2011-08-31
Try redirecting the script output and stderr to a log file, may catch any errors that are logged when it crashes.
 
 
```
 
/usr/bin/xterm -e perl /home/user/email2sms.pl > /path/to/somelogfile.log 2>&1

```
 
Can also then add some diagnostic debug print statements to the script and they will appear in the log so you can tell what the script was doing when it crashed.

---

