---
title: "Script not working properly with cron"
date: 2006-04-24
forum: General Help
---

### Post by LactosetheIntolerant on 2006-04-24
I'm fairly new to the whole linux administration bit, I've used the systems before but never ran it myself.  Anyway, I've written a script that will read auth.log and find any brute force attempts to get into the machine, then adds these IPs to iptables INPUT and drops the connections.  It works fine when called manually, but only partially works when on a scheduled run with cron.  It goes through the script and outputs the message at the end, but iptables is unchanged.  Is there something cron does different than when I run the script manually?

script is setup to run with sudo crontab -e, so it has permissions to add to iptables.
```

#!/bin/bash
#this script will read contents of auth.log and ban any ip which fails access
# more than 10 times.
#clear the current contents of iptables INPUT chain
#iptables -F INPUT

#get all the unique ip's and how many times they appear from auth.log
cat /var/log/auth.log |
grep Failed |
grep -o '[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}' |
uniq -d -c |
while read count ip
do
  if [[ $count -gt 10 ]]
    #add any IPs with more than 10 failed attempts iptables for dropping
    then iptables -A INPUT -s $ip -j DROP
  fi
done

echo "IP's have been blocked: $(date)" >> /home/simon/blockingscript.log

exit 0

```
And on a very related note, is there a better/more secure way to do this?  Like I said, I'm fairly new.

---

### Post by cgjones on 2006-04-24
Just a thought. su, and I suppose sudo, can confuse cron. Try specifying root when you run crontab.

---

### Post by LactosetheIntolerant on 2006-04-25
[QUOTE=cgjones]Just a thought. su, and I suppose sudo, can confuse cron. Try specifying root when you run crontab.[/QUOTE]
specifying root doesn't change anything.  Still modifying the same crontab.  I've tried just using a straight iptables append as a single task for cron, but that doesn't do anything either.  I guess iptables doesn't work from cron...

Is there a better way to block these ssh attacks?  They're not really hurting anyone, but I'd like to block the ip's from future attacks.

---

### Post by John Atkinson on 2006-06-20
Had the same problem - substituting an absolute call to iptables fixed the problem.  On Debian that was "/sbin/iptables" instead of just "iptables".

---

