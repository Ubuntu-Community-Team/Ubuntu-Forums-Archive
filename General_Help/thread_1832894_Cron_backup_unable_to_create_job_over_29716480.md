---
title: "Cron backup unable to create job over 29716480"
date: 2011-08-25
forum: General Help
---

### Post by mikeyw on 2011-08-25
Hi,

I've knocked up a very simple script to backup some data using tar, if i run the script from command line using sudo ./script.sh it executes fine creating a size 400537600 tar file

However if i try and run this as a cron job as root user it caps the tar file created to 29716480 and stops. I assume this is some kind of ulimit getting imposed on the cron job but unsure how to fix

Please could you guys offer some advice ?

Regards,
Mike.

---

### Post by blueridgedog on 2011-08-25
If you run the script as root, is the output as expected?

```
sudo su
/path/to/script
```

---

### Post by mikeyw on 2011-08-26
Hi,

Using su and executing as root it runs fine also from the command line.

Regards,
Mike.

---

### Post by dethorpe on 2011-08-26
Cron dosn't get the users profile and environemnt setup by default so when run from cron is the tar file being written to a different location then when run from command line? If different partition maybe less space available there?

---

### Post by mikeyw on 2011-08-26
No the job creates output in exactly the same area, here's the details :-

/confbck# crontab -l
# m h  dom mon dow   command
28 18 * * 1-5 /usr/local/backup.sh


/confbck# more /usr/local/backup.sh
day=`date | cut -c 1-3`
ulimit -f 9186055680
tar -cvf "/confbck/srvc$day".bck /srv/confluence
tar -cvf "/confbck/homec$day".bck /home/confluence


1st file created from command line, 2nd from the cron job

-rw-r--r-- 1 root root 2200166400 2011-08-26 14:22 srvcFri.bck
-rw-r--r-- 1 root root   29716480 2011-08-22 18:28 srvcMon.bck


Weird one this....

---

### Post by blueridgedog on 2011-08-26
Try the cron job without the ulimit.

---

### Post by mikeyw on 2011-08-30
Thanks - i ran it originally without the ulimit and only added it to try and fix the problem....

---

### Post by blueridgedog on 2011-08-30
Is it possible that the job doesn't finish do to something else happening at that time?  How about moving the time significantly to test.  I am just guessing here as it is fairly odd.

As a way of debugging, I would have it echo debugging information to a file, a start marker, then the standard output of the script (the files it is taring) and an end marker.  Finding out when and where it stops may be good information.

---

### Post by mikeyw on 2011-08-30
Thanks - the time is arbitary as i've tried it several times during the day as a cron job.

Not that familiar with debugging - are you able to offer advice ?

---

### Post by dethorpe on 2011-08-30
worth directing the output and stderr of the script run from cron job to a file, may see if its throwing any error messages:
 
cron entry:
 
```
 
28 18 * * 1-5 /usr/local/backup.sh > /confbck/backup.log 2>&1
 

```

---

### Post by blueridgedog on 2011-08-30
Something like...(untested)

```
#!/bin/bash 
#I notice you did not specify a shell in the first...you may get results by specifying one.
day=`date | cut -c 1-3`
logfile=/confbck/$day
echo "starting backup" >> $logfile
'date' >> $logfile
ulimit -f 9186055680
tar -cvf "/confbck/srvc$day".bck /srv/confluence 1>>$logfile 2>>$logfile
tar -cvf "/confbck/homec$day".bck /home/confluence 1>>$logfile 2>>$logfile
echo "finished backup" >> $logfile
'date' >> $logfile
```


(will need testing!!)

---

### Post by mikeyw on 2011-08-31
Incredible !

Your suggestion yielded no clues but it DID fix the problem.

Bizarrely by simply trapping the output the job completed, take the output capture away and it fails again....what on earth is causing this ?

Not a problem trapping the log file but shouldn't be needed to allow it work.

Thanks for your help

Mike.

---

### Post by dethorpe on 2011-08-31
Wierd,
 
By default cron emails standard out to the user, redirecting it to a file will mean theres no output to send, so maybe theres some problem in the email system that causes cron to bomb out when it tries to pass some output to it.

---

