---
title: "cron.weekly runs on wednesday instead of sunday"
date: 2012-08-06
forum: General Help
---

### Post by mikebus on 2012-08-06
Hi all,

this is a question for my understanding. 

I run Ubuntu 12.04 and my /etc/crontab contains the following line:
47 6    * * 7    root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )

This is default  and I didn't change it. I placed a script in the /etc/cron.weekly folder and the script even runs correctly once per week. However, according to the crontab the script should run every Sunday. Since I have a date >> log.text in my script I can see that apparently the script runs every Wednesday. The log.text reads:
Wed Jul 25 08:17:21 CEST 2012
Wed Aug  1 08:08:26 CEST 2012

I really would like to understand why this is the case. My system time is correctly set. Any hints?

Thanks a lot.

Regards,
Mike

---

### Post by Grenage on 2012-08-06
The days of the week are 0-6, you have 7.

0 = Sunday
6 = Saturday

---

### Post by codemaniac on 2012-08-06
> **mikebus said:**
> Hi all,

this is a question for my understanding. 

I run Ubuntu 12.04 and my /etc/crontab contains the following line:
47 6    * * 7    root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )

This is default  and I didn't change it. I placed a script in the /etc/cron.weekly folder and the script even runs correctly once per week. However, according to the crontab the script should run every Sunday. Since I have a date >> log.text in my script I can see that apparently the script runs every Wednesday. The log.text reads:
Wed Jul 25 08:17:21 CEST 2012
Wed Aug  1 08:08:26 CEST 2012

I really would like to understand why this is the case. My system time is correctly set. Any hints?

Thanks a lot.

Regards,
Mike

The fifth field numeric denotes "day of the week" the script gets fired .
I think it supports 0-6 with 0=Sunday .
But in your case i can see it is 7 .

---

### Post by codemaniac on 2012-08-06
In your crontab files you can use the below comment to memorize the fields better .
```

# minute (0-59),
# |      hour (0-23),
# |      |       day of the month (1-31),
# |      |       |       month of the year (1-12),
# |      |       |       |       day of the week (0-6 with 0=Sunday).
# |      |       |       |       |       commands

```

---

### Post by ajgreeny on 2012-08-06
According to my information, and I can't remember where I got it from, but it was a long time ago, 0 and 7 both represent Sunday.

However, cron now appears to use only 0 - 6 as others here suggest, so perhaps things have changed over the 7 years I have been using Ubuntu, or more likely, I had picked up erroneous information.

I have just found the references; [http://unixhelp.ed.ac.uk/CGI/man-cgi?crontab+5/](http://unixhelp.ed.ac.uk/CGI/man-cgi?crontab+5/) and
[http://www.unix.com/answers-frequently-asked-questions/13527-cron-crontab.html](http://www.unix.com/answers-frequently-asked-questions/13527-cron-crontab.html)
which as you can see are talking partly, at least about unix, not just Linux, so that may be where the difference lies.  I have also found [http://ubuntu-for-humans.blogspot.co.uk/2009/12/using-crontab-in-ubuntu.html](http://ubuntu-for-humans.blogspot.co.uk/2009/12/using-crontab-in-ubuntu.html) which suggests that both should work in ubuntu, so I'm confused.

I have not used the "day of week" entry in crontab entries, so I do not know if the 7 works or not.

---

### Post by mikebus on 2012-08-06
Thank you all for replying. I did see that day of the week is set to 7 but I was convinced that bith, 0 and 7, indicate sunday. Especially since this is the default value and I did not change the crontab file.

In any case I will try with 0 and I'll see whether anything changes.

Thanks again.

---

### Post by Dave_L on 2012-08-06
According to "man 5 crontab", either 0 or 7 represent Sunday.

anacron may be overriding the cron table setting.

anacron uses the files in /var/spool/anacron/ to keep track of when it last ran the tasks.  You might be able to manually adjust /var/spool/anacron/cron.weekly to get the result you want.

---

### Post by mikebus on 2012-08-06
I see. I manually changed the time  /var/spool/anacron/cron.weekly to last sunday. So in theory it should run again next sunday since the period in the /etc/anacrontab is set to 7.

I'll see whether it works. Thanks!!

---

