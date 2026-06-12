---
title: "crontab command requires root?"
date: 2011-02-03
forum: General Help
---

### Post by ianc1 on 2011-02-03
I tried scheduling a task using crontab -e and added the line:
```
58 23 3 2 4 /usr/bin/freshclam --verbose --log=/home/EXISTING DIR where I have permissions
```The timing was simply a test run.  My syslog gives the following error:
```
(CRON) error (grandchild #4309 failed with exit status 62).
```I also tried to add to root crontab as below, but got the same error.
```
sudo crontab -u root -e a
```Anybody got any ideas?

Cheers

---

### Post by Habitual on 2011-02-03
```
sudo crontab -e -u root
```
works for me.

---

### Post by ianc1 on 2011-02-04
Will that work for freshclam as I've just found out that the error code (62) is a freshclam error code which corresponds to "can't initialize logger".

I've tried without the -log=... option and I still get the same error.

---

### Post by ianc1 on 2011-02-05
Solved the actual problem as I have realized that freshclam is already checking for updates hourly so a forced check on reboot seems a little unnecessary.

Still confused as to why it didn't work with crontab;' I assume its a root issue or a freshclam permissions issue but unsure.

For the benefit of anyone else who has this issue - freshclam updates are controlled in the freshclam.conf file in /etc/clamav.  Look for the lines:

# Check for new database 24 times a day
Checks 24

---

### Post by SeijiSensei on 2011-02-05
Cron checks the file /etc/crontab as well.  Entries you place in this file need the username that will execute the task, e.g, 

```
1 * * * * root /usr/bin/freshclam >> /var/log/freshclam 2>&1
```

will run freshclam with root privileges once each hour.  It will write any output to /var/log/freshclam, including errors ("2>&1").  If you don't trap output, it will be mailed to the user, root in this case.

You can run the same job from /var/spool/cron/root by omitting the "root" entry above.  You can use the crontab command to create this, but I just manually edit (as root) /var/spool/cron/root.

---

### Post by ianc1 on 2011-02-06
Thanks SeijiSensei.  I thought using crontab -e put all the commands into /etc/crontab; clearly I was mistaken.  I assume the edit you suggested will not require the sudo password everytime the command runs.

Final query what is the 2>&1 doing at the end?

Thanks

---

### Post by SeijiSensei on 2011-02-07
> **ianc1 said:**
> Thanks SeijiSensei.  I thought using crontab -e put all the commands into /etc/crontab; clearly I was mistaken.  I assume the edit you suggested will not require the sudo password everytime the command runs.

Final query what is the 2>&1 doing at the end?

Thanks

crontab manages files in /var/spool/cron.  It's designed to anable ordinary users to schedule cron jobs.  Unlike entries in /etc/crontab there's no username included in the entries in these files. Instead, jobs to be run by user "harry" would be stored in /var/spool/cron/harry which harry owns with 0600 permissions. 

While /etc/crontab runs as root, you must include the user that is supposed to run the job in each entry, e.g., "1 * * * * harry [some command]".  That's true even if the user running the job is root.

The "2>&1" [redirects]("http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-3.html") any error output (stderr) to standard output (stdout).  Adding that ensure all the possible output ends up in the log file.

Nothing here will require the sudo password once you've edited the files.  The cron daemon runs as root and requires no additional permissions.

---

### Post by Jordy_224 on 2011-02-10
I'm stuck with the following...
 my cron tab code is written to restart a firewall at reboot. 
According to the log the firewall restarts. Yet, when I check the firewall status it did not restart. 

```
sudo crontab -e 
```

```

#
# m h  dom mon dow   command
SHELL=/bin/bash
PATH=/sbin:/bin:/usr/sbin:/usr/bin
MAILTO=root
HOME=/

@reboot root    /etc/init.d/ubuntu_ce_firewall restart >/tmp/mylog.log
```

by if I use the terminal, the code functions correctly. 

```
sudo /etc/init.d/ubuntu_ce_firewall restart 
```


Not sure, as what's next...Is it that the job is not running correctly

---

### Post by ianc1 on 2011-02-10
Thanks SeijiSensei.  That's an excellent link for a learner and will come in handy no doubt.

Jordy_224 I don't know that firewall, but when firestarter is running I can do```
sudo services firestarter status
``` to be find out whether it is up and running.  I get nothing returned ie no positive or negative result if I omit the sudo command.

I don't know if you can do this with your firewall.  The other possibility is```
services --status-all
``` which will indicate + for up and running and - for not working if I understand it correctly.   Again I have to execute this as a superuser to see if the firewall is working otherwise I get a negative result.

---

### Post by Jordy_224 on 2011-02-11
ianc1 > thanks for the info. Yes, Im certain the firewall is status is active. The services command support this...

```

sudo service ubuntu_ce_firewall status

```

Result: 
[PHP]Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination[/PHP]

2.
```

services --status-all

```

Result:
[PHP]
[ ? ]  tinyproxy
[ + ]  ubuntu_ce_firewall
[/PHP]

The issue is the the firewall is not transparent. Yet, the transparent option is active if I restart the firewall after boot. 

So my goal is to restart the firewall after boot and re-gain transparent status on firewall.

--

So my goal is to restart the firewall after boot and re-gain transparent status on firewall.

Problem solved! 

I was able to restart the firewall by linking to a script within a cronjob and using the **sleep** function to delay restarting the firewall. For example: 

```
Sleep 20 
/etc/init.d/ubuntu_ce_firewall restart >/tmp/mylog.log
```


I didn't think that the sleep function could be so handy...

---

### Post by Jordy_224 on 2011-02-12
So my goal is to restart the firewall after boot and re-gain transparent status on firewall.

Problem solved! 

I was able to restart the firewall by linking to a script within a cronjob and using the **sleep** function to delay restarting the firewall. For example: 

```
Sleep 20 
/etc/init.d/ubuntu_ce_firewall restart >/tmp/mylog.log
```


I didn't think that the sleep function could be so handy...

---

### Post by Jordy_224 on 2011-02-12
So my goal is to restart the firewall after boot and re-gain transparent status on firewall.

Problem solved! 

I was able to restart the firewall by linking to a script within a cronjob and using the **sleep** function to delay restarting the firewall. For example: 

```
Sleep 20 
/etc/init.d/ubuntu_ce_firewall restart >/tmp/mylog.log
```


I didn't think that the sleep function could be so handy...

---

### Post by Jordy_224 on 2011-02-12
So my goal is to restart the firewall after boot and re-gain transparent status on firewall.

Problem solved! 

I was able to restart the firewall by linking to a script within a cronjob and using the **sleep** function to delay restarting the firewall. For example: 

```
Sleep 20 
/etc/init.d/ubuntu_ce_firewall restart >/tmp/mylog.log
```


I didn't think that the sleep function could be so handy...

---

### Post by Jordy_224 on 2011-02-12
So my goal is to restart the firewall after boot and re-gain transparent status on firewall.

Problem solved! 

I was able to restart the firewall by linking to a script within a cronjob and using the **sleep** function to delay restarting the firewall. For example: 

```
Sleep 20 
/etc/init.d/ubuntu_ce_firewall restart >/tmp/mylog.log
```


I didn't think that the sleep function could be so handy...

---

