---
title: "crontab + python"
date: 2011-09-21
forum: General Help
---

### Post by clos80 on 2011-09-21
Hi All,

I'm want to run a python script using crontab.
In order to do this I first edit the crontab file "sudo crontab -e". I then make sure that it is in the list of jobs to perform using "sudo crontab -l", hereafter the output (there is an empty line after the job):
sudo crontab -l
# Edit this file to introduce tasks to be run by cron.
# 
# Each task to run has to be defined through a single line
# indicating with different fields when the task will be run
# and what command to run for the task
# 
# To define the time you can provide concrete values for
# minute (m), hour (h), day of month (dom), month (mon),
# and day of week (dow) or use '*' in these fields (for 'any').# 
# Notice that tasks will be started based on the cron's system
# daemon's notion of time and timezones.
# 
# Output of the crontab jobs (including errors) is sent through
# email to the user the crontab file belongs to (unless redirected).
# 
# For example, you can run a backup of all your user accounts
# at 5 a.m every week with:
# 0 5 * * 1 tar -zcf /var/backups/home.tgz /home/
# 
# For more information see the manual pages of crontab(5) and cron(8 )
# 
# m h  dom mon dow   command
26 11   * * *  usr/bin/python /home/csalmin/Documents/scripts/s-ripa/test.py

This script should run every day at 11h26. Hereafter the content of the script test.py:
#!/usr/bin/python
import time

def main():
    file = open('/home/csalmin/Documents/scripts/s-ripa/test.txt','a')
    file.write('\n\nRun at: '+str(time.time())+' !!!\n\n')

if __name__ == "__main__":
    main()

The crond is running:
ps -el | grep cron
5 S     0  2833     1  0  80   0 -  4732 hrtime ?        00:00:00 cron

The problem is that the script is never runs, or at least it never update the test.txt file.
Of course if I manually run the script from the terminal the file is correctly created/updated
Can you please help me out?

Thx.

---

### Post by drmrgd on 2011-09-21
> **clos80 said:**
> Hi All,

I'm want to run a python script using crontab.
In order to do this I first edit the crontab file "sudo crontab -e". I then make sure that it is in the list of jobs to perform using "sudo crontab -l", hereafter the output (there is an empty line after the job):
sudo crontab -l
# Edit this file to introduce tasks to be run by cron.
# 
# Each task to run has to be defined through a single line
# indicating with different fields when the task will be run
# and what command to run for the task
# 
# To define the time you can provide concrete values for
# minute (m), hour (h), day of month (dom), month (mon),
# and day of week (dow) or use '*' in these fields (for 'any').# 
# Notice that tasks will be started based on the cron's system
# daemon's notion of time and timezones.
# 
# Output of the crontab jobs (including errors) is sent through
# email to the user the crontab file belongs to (unless redirected).
# 
# For example, you can run a backup of all your user accounts
# at 5 a.m every week with:
# 0 5 * * 1 tar -zcf /var/backups/home.tgz /home/
# 
# For more information see the manual pages of crontab(5) and cron(8 )
# 
# m h  dom mon dow   command
26 11   * * *  usr/bin/python /home/csalmin/Documents/scripts/s-ripa/test.py

This script should run every day at 11h26. Hereafter the content of the script test.py:
#!/usr/bin/python
import time

def main():
    file = open('/home/csalmin/Documents/scripts/s-ripa/test.txt','a')
    file.write('\n\nRun at: '+str(time.time())+' !!!\n\n')

if __name__ == "__main__":
    main()

The crond is running:
ps -el | grep cron
5 S     0  2833     1  0  80   0 -  4732 hrtime ?        00:00:00 cron

The problem is that the script is never runs, or at least it never update the test.txt file.
Of course if I manually run the script from the terminal the file is correctly created/updated
Can you please help me out?

Thx.

I might be wrong here, but I don't think you need the "usr/bin/python" bit in the crontab.  Delete that and see if it works.

---

### Post by Dave_L on 2011-09-21
Try capturing the output. There may be error messages:

```
... /home/csalmin/Documents/scripts/s-ripa/test.py >>/home/csalmin/cron.log 2>&1
```

---

### Post by diesch on 2011-09-21
> **clos80 said:**
> Hi All,
26 11   * * *  usr/bin/python /home/csalmin/Documents/scripts/s-ripa/test.py


There's a */* missing in front a of *usr/bin/python *. 

If you make your program executable you don't need to call */usr/bin/python* here.

---

### Post by Cheesehead on 2011-09-24
Since all the files you are working with are user-level (not root), you don't need to edit the root crontab. Use 'crontab -e' without the sudo.

---

