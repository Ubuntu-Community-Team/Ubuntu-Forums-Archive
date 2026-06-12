---
title: "Executing a PHP script with Crontab"
date: 2012-04-09
forum: General Help
---

### Post by jhaywood on 2012-04-09
Hi guys,

I know there are a lot of posts about this all over the internet but this is really driving me crazy and I can't see what the problem is. I had this working before but I've just installed a new LAMP set-up and everything is fine except for this one issue. I've been using crontab to run a daily hit counter but it's not working on the new set-up so I've done the following tests:

I've put a PHP script at MYWEBSITE/ltg/test.php
This file adds 1 to a value in my database using:

mysql_query("UPDATE ltg_test SET manual = manual + 1 WHERE manual > 0");

If I run that PHP script in my browser it works fine and the database value increases by one.

**Conclusion: The PHP script is working.**

Next I've put a blank text file in the same directory: MYWEBSITE/ltg/text.txt

In crontab I've put:

* * * * * php /var/www/ltg/test.php
* * * * * echo "test" > /var/www/ltg/test.txt

I've set the permissions of the PHP file to 755 both manually with fireFTP and using "chmod 755 /var/www/ltg/test.php".

After a minute or so crontab edits the text file so it is no longer blank but includes the word "test".

**Conclusion: Crontab is working.**

But! The PHP script has not been run. The value in the database does not increase. I have also tried the following lines in crontab individually:

* * * * * /var/www/ltg/test.php
* * * * * /usr/bin/php /var/www/ltg/test.php
* * * * * /usr/bin/php -q /var/www/ltg/test.php
* * * * * /usr/bin/wget /var/www/ltg/test.php
* * * * * /usr/bin/wget -q /var/www/ltg/test.php

The locations of the PHP interpreter and wGet are correct as checked with "which php" and "which wget", but none of them are working...

I just don't get it, the PHP script is working as I can run it directly from the browser, crontab is working and the file path is correct as it ammends the text file in the same directory, but crontab is not running the PHP file (permission is definitely 755).

Any suggestions would be greatly appreciated!

---

### Post by ianhaycox on 2012-04-09
Have you looked in root's mailbox (or maybe your own if forwarded in /etc/aliases) ?

Also check /var/log/cron, /var/log/messages and /var/log/syslog

Try appending

* * * * * /usr/bin/php /var/www/ltg/test.php > /tmp/test.log 2>&1

---

### Post by jhaywood on 2012-04-11
Hi,

Thanks for help and sorry for the delay in getting back to you. I left the crontab running with:

* * * * * wget -q /var/www/ltg/test.php
* * * * * /usr/bin/wget /var/www/ltg/daily_hits.php
* * * * * /urs/bin/php -q /var/www/ltg/test.php
* * * * * echo "test: > /var/www/ltg/test.txt

(the daily_hits.php is the file I used before that I actually want to use crontab with, the others are just the test files I mentioned before)

Since then the syslog is showing this every minute:

Apr  9 18:40:01 li239-170 CRON[4837]: (root) CMD (echo "test" > /var/www/ltg/test.txt)
Apr  9 18:40:01 li239-170 CRON[4838]: (root) CMD (/usr/bin/wget /var/www/ltg/daily_hits.php)
Apr  9 18:40:01 li239-170 CRON[4839]: (root) CMD (/usr/bin/php -q /var/www/ltg/test.php)
Apr  9 18:40:01 li239-170 CRON[4840]: (root) CMD (wget -q /var/www/ltg/test.php)

As before, the echo into the text file is working, the PHP files are all set to 755 permissions but don't seem to be being executed.

The messages log just seems to be logging the server's memory usage, and I couldn't find any cron file in /var/log/. Does that help identify the problem at all?

---

### Post by SeijiSensei on 2012-04-11
Add a line at the top of the PHP scripts to write a log entry to the filesystem:

```

$fp=fopen("/var/www/ltg/php_log.txt","a+");
fwrite($fp,"Writing a new log entry at ".date("r"));
fclose($fp);

```

---

### Post by jhaywood on 2012-04-11
That worked!

Writing a new log entry at Wed, 11 Apr 2012 15:12:01 -0400

Sorry but I forgot to mention that the PHP file "includes" another PHP file. So your test shows that the PHP file is executed by crontab, however, the include statement does not work when executed by crontab (but it does work when the PHP file is run from the web).

The include statement is:

include '../../ltg_source/test.php';

So can execution by crontab change the relative file path somehow? Thanks for all the help so far, learning to test files with logs will really help me in the future!

---

### Post by SeijiSensei on 2012-04-11
You're always better off using absolute paths.

If you don't want to write the path every time, set a PHP variable to it and then write includes like this:

```

$includes='/path/to/my/includes/';
include($includes.'include_file.php');

```

I always put the trailing slash on the include directory so I don't have to put it at the beginning of the included file.

---

### Post by jhaywood on 2012-04-13
It's all working! Thanks so much for the help, I learnt a lot too :)

---

