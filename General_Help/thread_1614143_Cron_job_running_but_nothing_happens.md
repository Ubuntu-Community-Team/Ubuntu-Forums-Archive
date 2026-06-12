---
title: "Cron job running but nothing happens"
date: 2010-11-05
forum: General Help
---

### Post by Ethan McWinston on 2010-11-05
Hello,

I am making a webpage which is to be automatically generated every minute.
I've created a cron job in crontab like this:
```
0-59 * * * * /usr/bin/php /var/www/site/updatestatistics.php > /dev/null
```When I refresh the page 'updatestatistics.php' in my webbrowser it does generate a new page ('statistics.html', which is included in 'statistics.php'). But when I let this cron job do the job, nothing happens.
I looked into the log file, it shows this:
```
(root) CMD (/usr/bin/php /var/www/site/updatestatistics.php > /dev/null)
```Am I doing something wrong here?

---

### Post by Barriehie on 2010-11-06
> **Ethan McWinston said:**
> Hello,

I am making a webpage which is to be automatically generated every minute.
I've created a cron job in crontab like this:
```
0-59 * * * * /usr/bin/php /var/www/site/updatestatistics.php > /dev/null
```When I refresh the page 'updatestatistics.php' in my webbrowser it does generate a new page ('statistics.html', which is included in 'statistics.php'). But when I let this cron job do the job, nothing happens.
I looked into the log file, it shows this:
```
(root) CMD (/usr/bin/php /var/www/site/updatestatistics.php > /dev/null)
```Am I doing something wrong here?

Try running it without the redirect to /dev/null.

---

### Post by Ethan McWinston on 2010-11-06
> **Barriehie said:**
> Try running it without the redirect to /dev/null.

Thanks for replying. 
When I'm trying without "> /dev/null" it still doesn't update the "statistics.html" page. The cron is running and doesn't give an error:
```
(root) CMD (/usr/bin/php /var/www/site/updatestatistics.php)
```I've tried executing the php file by the command line using
```
php /var/www/site/updatestatistics.php
```This also does not change the "statistics.html" file. I do have php5-cli installed.
I've made a simple sample script which inserts some random values in a database. When I run that php file by the command line it works.
Could the problem be the fopen, frwite and fclose functions in php?

---

### Post by Barriehie on 2010-11-06
I too had an issue with crontab while running Ubuntu, but that was years ago! How about this, have crontab run a shell script that runs the php.
Also, are the generated files writable by users outside of your user/group?

```

#!/bin/bash
php5 /var/www/site/updatestatistics.php &>/home/username/Desktop/logfile
exit 0

```

And have the updatestatistics.php file echo out what it's doing so you've got something going into the logfile.

Post the updatestatistics.php file?

Barrie

Edit:
```
0-59 * * * * root some_shell_script
```

---

### Post by Ethan McWinston on 2010-11-06
Thanks Barrie!
I've created the shell script as you said. When executing that script from the shell itself it works.
When creating a cron job for that, it does nothing. This is how it looks:
```
0-59 * * * * root /var/www/site/updatescript.sh
```This is the log file of crontab:
```
CRON[7690]: (root) CMD (root /var/www/site/updatescript.sh)
(CRON) error (grandchild #7690 failed with exit status 127)
CRON[7688]: (CRON) info (No MTA installed, discarding output)
```**EDIT:**
I put 'bash' instead of 'root' and that gives me no error. So I now have the following:
```

0-59 * * * * bash /var/www/site/updatescript.sh
CRON[7931]: (root) CMD (bash /var/www/site/updatescript.sh)
```The updatestatistics.php file has all the necessary privileges. When I  run the shell script form the command line it generates a log file which  has all the right information (I echoed the whole generated page).
The updatestatistics.php file looks like this ("$newstats" contains all the info which is to be saved in "updatestatistics.html"):
```
$fp = fopen("statistics.html", 'w') or die("error while updating statistics page");
fwrite($fp, $newstats);
fclose($fp);
echo $newstats;
```**UPDATE:**
Okay, so I now see that the logfile DOES contain the newly generated page. For some reason the newly generated page is not saved as the "statistics.html" page. So the intermediate solution is letting the "updatescript.sh" give output to the "statistics.html" page. This does the job, but I'm still not happy with this one.

---

### Post by Barriehie on 2010-11-06
In your php script where you're openingthe file for writing try putting the full path to the file:
```

$fp = fopen("[color=red]<some_path>[/color]/statistics.html", 'w') or die("error while updating statistics page");

```
or what I do on my stuff is like this: (if running in the same dir)
```

$fp = fopen("[color=red]./[/color]statistics.html", 'w') or die("error while updating statistics page");

```

Edit: And take out the redirect; we know the file is running since the logfile is getting the data that should be written.  That was a test!

---

### Post by Ethan McWinston on 2010-11-06
Including the complete path did the job! Thanks so much for you help Berrie! :)

---

### Post by Barriehie on 2010-11-06
> **Ethan McWinston said:**
> Including the complete path did the job! Thanks so much for you help Berrie! :)

[img]http://ubuntuforums.org/images/smilies/icon_razz.gif[/img]

---

