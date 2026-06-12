---
title: "Cron job for Cisco VPN client"
date: 2009-09-15
forum: General Help
---

### Post by danylo1321 on 2009-09-15
Hi,

I want to check if my Cisco VPN client is down and if it is down I want to restart it. I do this by running a script in cron every 30 minutes:

vpn.sh
```
#!/bin/bash
CNAME=`ps -A | grep vpnclient`
NOW=`date`
if [ "$CNAME" = "" ]
then
echo "vpnclient started -" $NOW >> /home/user/scripts/vpn.log
vpnclient connect myvpn
fi

```If I run this script from the command line it works (the VPN is re-started) but from the cron job it does not work. If the VPN is down I see that something is written in the log file but the VPN is never re-started.
Any suggestions?
Thanks.

---

### Post by jonobr on 2009-09-16
Are you running the script as root manually?

Are there any reports of cron errors in the log

```
 sudo grep CRON /var/log/syslog
```

Could you post the entry in cron

---

### Post by danylo1321 on 2009-09-16
The script is being run as root. At the command line, I wrote 'crontab -e' and entered the following in the crontab file:

```

# m     h       dom     mon     dow     command
10,40   *       *         *          *         /home/user/scripts/vpn.sh

```

In the syslog file I do not see any errors. I know that crontab is working because I see something being written in vpn.log every time the script runs.

---

### Post by DaithiF on 2009-09-16
what is the path to the vpn client?  try an explicit path if its not in one of /usr/bin or /bin, which are the only 2 dirs in the path by default for jobs run by your crontab.

---

### Post by danylo1321 on 2009-09-17
Yep, that fixed my problem - writing the full path of vpnclient.

Thanks!

---

