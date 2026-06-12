---
title: "RSYNC and CRON --- WON'T they Work together?"
date: 2010-08-12
forum: General Help
---

### Post by ivikas on 2010-08-12
Hello all,

       I have an offline IBM Ubuntu Server in a LAN for Web Development.Iam planning a backup,the backup Files is to be put in a remote Windows Machine.
So, i have mounted these windows shares onto this Linux Machine.So all i mean to convey is that iam NOT using rsync with ssh but like from a Local Linux Machine to Remote Windows MOUNTED Share.


When i run rsync on terminal,it works fine but when i use it with cron, it is not working nor the custom log file is showing anything.

```


#!/bin/bash
/usr/bin/rsync -a  --delete IBMServer:/var/www/ /root/Desktop/WWWBACKUP_ON_254/ >> /root/vikas.log


```

and my crontab looks like this

```


0 17 * * *  /scripts/wwwroot-backup-script.sh

I have tried every combination like
0 17 * * * /usr/bin/rsync -a  --delete IBMServer:/var/www/ /root/Desktop/WWWBACKUP_ON_254/ >> /root/vikas.log

0 17 * * *  /bin/bash /scripts/wwwroot-backup-script.sh


```

where 
      IBMServer is the Source IBM Server Running Ubuntu Server 10.04 LTS
      WWWBACKUP_ON_254 is the windows share on machine 192.168.1.254,which is mounted onto Linux in /etc/fstab and IAM NOT USING 
SSH WITH RSYNC



So,It will be a great Help If anyone could help me with a working solution
or web link.

Thanks in Advance,
Vikas

---

### Post by surfer on 2010-08-12
check [this thread]("http://ubuntuforums.org/showthread.php?t=497474"). the naming of the script is crucial, as far as i remember.

---

### Post by DaithiF on 2010-08-12
the naming of the script is only relevant for cronjobs run by the run-parts mechanism, ie. the cron.daily|weekly|monthly files.

For a job defined in a particular users crontab (ie. via crontab -e), the script can be called anything.

some suggestions:
1. whose crontab are you running this under -- your own user or root?  From the location of the target mount (/root/Desktop), its likely only root will have access to the target so try sudo crontab -e if you haven't already.
2. i would suggest you also capture stderr output to your log, so add 2>&1 
3. if this server doesn't have a mail MTA, then put MAILTO="" at the top of the crontab, as a workaround for the cron bug mentioned here: [http://ubuntuforums.org/showthread.php?t=1537161](http://ubuntuforums.org/showthread.php?t=1537161)

---

### Post by ivikas on 2010-08-12
Hello DaithiF,

Iam running cron as root  and has added MAILTO="" at the top of My Cron.Please have 
a look.Please tell me as where to find system level logs for cron.

```

# m h  dom mon dow   command
MAILTO=""
# This is for wwwroot folder backup at 5.00 PM Every day.
0 17 * * *  /bin/bash /scripts/wwwrootbackupscript.sh

```

This is the content of script /scripts/wwwrootbackupscript.sh

```

#!/bin/bash
/usr/bin/rsync -a  --delete /var/www/ /root/Desktop/WWWBACKUP_ON_254/ >> /root/vikas.txt

```

This is not working.Please help a way out,i have been on this for past 48 hours.

regards,
Vikas Mohan

---

### Post by NIT006.5 on 2010-08-12
Do you not need to specify which user the command should run as? i.e.

```
0 17 * * *  root /bin/bash /scripts/wwwrootbackupscript.sh
```

---

### Post by DaithiF on 2010-08-12
> **NIT006.5 said:**
> Do you not need to specify which user the command should run as? i.e.

```
0 17 * * *  root /bin/bash /scripts/wwwrootbackupscript.sh
```
No, not for individual users or roots crontabs, ie. one edited via crontab -e or sudo crontab -e.

For system-level crontabs though, yes you need the user name.

Vikas,
I would suggest the following edits to your bash script to throw more light on whats happening (or not happening):
```
#!/bin/bash
logfile=/root/vikas.txt
echo "$(date) Starting script, about to run rysnc" > $logfile
/usr/bin/rsync -a  --delete /var/www/ /root/Desktop/WWWBACKUP_ON_254/ >> $logfile 2>&1
echo "$(date) returned from rsync call" >> $logfile

```no need for the /bin/bash in your crontab entry, just:
```
0 17 * * *  /scripts/wwwrootbackupscript.sh
```will be fine.

what turns up in the /root/vikas.txt file?

---

### Post by ivikas on 2010-08-12
Hello DaithiF,

           Your script has worked.Thankyou very much
Vikas

---

