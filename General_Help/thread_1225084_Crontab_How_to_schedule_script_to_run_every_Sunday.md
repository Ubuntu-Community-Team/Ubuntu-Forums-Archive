---
title: "Crontab: How to schedule script to run every Sunday after 15 day in month?"
date: 2009-07-28
forum: General Help
---

### Post by abcuser on 2009-07-28
Hi,
I have written a script, that should only run ones per month in first Sunday after day 15 in month at 18:00 hours (6 PM).
So script should be run: Aug 16, Sep 20, Oct 18, Nov 22, Dec 20 etc.

How to schedule script using crontab?
Regards

---

### Post by drs305 on 2009-07-28
This isn't an elegant solution, but one way would be to have the crontab run seven days following the 15th, with a script checking to see if it was Sunday. The cron job in this example would run at 1800.

Crontab:
> 
0 18 16-22 * * /path/somescript


somescript:
> 
#!/bin/bash
isitSun=$(date | awk -F" " '{print$1}')
if [ $isitSun = "Sun" ]; then
dosomething
fi
exit


---

### Post by DaithiF on 2009-07-28
similar to drs305 but maybe slightly neater -- test for sunday in the crontab command itself, rather than in the script

```
0 18 16-22 * * test 0 = $(date +%w) && /path/to/somescript

```

%w gives day of week , 0 - 6, with 0 being sunday.
path/to/somescript will run only if the test command evaluates to true

---

### Post by abcuser on 2009-07-29
DaithiF,
I tried you code, but it just doesn't work. It looks there is some kind of problem executing "test" command from crontab.

I simplified crontab (just for test purpose) and wrote:
```

* * * * * echo "ok" > ~/from_crontab.txt

```
So every minute write 'ok' text to file from_crontab.txt to my home folder. This works fine!

Then I have changed the code to:
```

* * * * * test 3 = $(date +%w) && echo "ok" > ~/from_crontab.txt

```
Note: I know at production version there should be "test 0" instead of "test 3", but today is Wednesday so 3.

I have tried to execute above command from terminal and it works fine, it writes file to my home folder. But the *same* command does not work from crontab. Any idea why not?

My System: Ubuntu 9.04 (fully updated).
Regards

---

### Post by drs305 on 2009-07-29
I couldn't get it to run either for some reason. However, the method I presented seems to work ok.

Depending on who you are running the script as, try putting the complete path in your entry:
> * * * * * test 3 = $(date +%w) && echo "ok" > [COLOR="DarkRed"]**/home/yourusername**[/COLOR]/from_crontab.txt

---

### Post by abcuser on 2009-07-29
Hi,
I have tried above code, and also tried this one:
```

test $(date +%w) -eq 3 && echo ok > /home/martin/from_crontab.txt || echo not_ok > /home/martin/from_crontab.txt

```
Above code is running fine if executed from terminal, but it is just not working running from crontab.

I have also read: [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto) tutorial. It looks like crontab is running in sh shell, but SHELL variable can be set. There are also PATH and HOME variables, so now my crontab looks like:
```

SHELL=/bin/bash
PATH=/usr/sbin:/usr/bin:/sbin:/bin
HOME=/home/martin
* * * * * test $(date +%w) -eq 3 && echo ok > /home/martin/from_crontab.txt || echo not_ok > /home/martin/from_crontab.txt

```

Is there any log file that I could get some message what is wrong?
Regards

---

### Post by DaithiF on 2009-07-29
sorry folks, my bad.  i had forgotten that the '%' character is special to cron and you need to escape it with a backslash if you want to use it, so:

* * * * * test $(date +\%w) -eq 3 && echo "Its wednesday" >> /home/dave/cronout

should work
cheers
d

---

### Post by HereInOz on 2009-07-29
I have found that to run a script with crontab, you need to have the bash command in there first:

0 2 * * 4 bash /home/user/scripts/somescript

Also the files get downloaded into /root if you are scheduling a download

---

### Post by abcuser on 2009-07-30
> **DaithiF said:**
> sorry folks, my bad.  i had forgotten that the '%' character is special to cron and you need to escape it with a backslash if you want to use it
Yes, you are right! This solved the problem. Thanks a lot. Are they any other special characters in cron?

---

### Post by abcuser on 2009-07-30
> **HereInOz said:**
> I have found that to run a script with crontab, you need to have the bash command in there first
I guess you have by default bash shell defined as you default shell. This settings is set per user in there profile (there is .profile file in your home directory where such a settings are defined). You can find which settings is set in current terminal by executing command:
```
echo $SHELL
```
You can change shell in current terminal by executing command:
```
/bin/bash
```
to bash shell or
```
/bin/sh
```
to change it to sh shell etc.
If you would like to permanently change shell then use the following command in .profile file:
```
export SHELL=/bin/bash
```

But cron does not use shell settings defined in your profile but uses sh shell by default. To avoid shells problem you can set SHELL variable in crontab at the top before other commands like
```
SHELL=/bin/bash
0 2 * * 4 /home/user/scripts/somescript

```
in case you would like to have all script to be executed in bash shell instead of sh. But I think there is better practice to use shell definition in bash file like:
```
#!/bin/bash
other-bash-commands
```
The last approach is better practice, because script can also be executed from terminal from user that does not use bash as default shell.

> **HereInOz said:**
> Also the files get downloaded into /root if you are scheduling a download
You are probably running crontab with root user like:
```
sudo crontab -e
```
To avoid this problem just use:
```
crontab -e
```
or set HOME variable like:
```
HOME=/home/your_user
```
Cron is a system that runs by user, so each user has it's own cron settings and each user has it own home directory.

Regards

---

### Post by abcuser on 2009-07-30
Hi,
just wondering what does last (5th parameter) of the cron settings mean, in help there is "day of week, 0-Sunday".

This is probably the simpliest solution for my problem:
```
0 18 16-22 * 0 /path/somescript
```
Notices 0 at 5th place means every Sunday.

Regards

---

### Post by abcuser on 2009-07-30
> **abcuser said:**
> 
This is probably the simplest solution for my problem:
```
0 18 16-22 * 0 /path/somescript
```
Notices 0 at 5th place means every Sunday.
The above code will not work!!! Oh what a strange behavior.

I thought it was bug, but like explained in: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=460070](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=460070) it is not a bug just "bizarre behavior".

From above link:
```
Note: The day of a command's execution can be specified by two fields
 day of month, and day of week. If both fields are restricted (i.e., aren't 
*), the command will be run when either field matches the  current time.  For
 example, 30 4 1,15 * 5 would cause a command to be run at 4:30 am on the 1st
 and 15th of each month, plus every Friday.

```

and then explanation:
```
... the current behaviour is a bit inconsistent. The other fields are
combined with a logical AND (ie: month AND day of month AND hour AND
minute), whereas the day of month and day of week fields are combined
with a logical OR.
```

---

