---
title: "Cron php program with argument"
date: 2011-07-02
forum: General Help
---

### Post by ELMIT on 2011-07-02
I have a simple program that should run in cron:

cd '/my/path/' ; /usr/bin/php -q TwR.php 1 > /dev/null ;

It runs fine from the command line, but not with cron! The argument "1" or whatever I need, is ignored.

Any idea how to solve it?


bye

Ronald

---

### Post by SeijiSensei on 2011-07-03
You're saying the passed parameter doesn't appear as $argv[0] when run from cron?  Strange.

You could use an environment variable instead:

```
cd '/my/path/' ; export MYVAR="1"; /usr/bin/php -q TwR.php > /dev/null
```

In your script, $_ENV['MYVAR'] should contain the passed parameter.

---

### Post by ELMIT on 2011-07-04
I put into the php script these lines:

$user = $argv[1];
echo "user = $user<br>";
$user = $_ENV['CURENT_USER'];
echo "CURRENT_USER = $user<br>";


I changed to another directory and I call the script for testing in a terminal only:

cd '/my/path/TwRon/' ; export CURRENT_USER="1"; /usr/bin/php -q TwR.php 4

and see on the screen:

> PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626/imap.so' - /usr/lib/php5/20090626/imap.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626/imap.so' - /usr/lib/php5/20090626/imap.so: cannot open shared object file: No such file or directory in Unknown on line 0

Deprecated: Directive 'register_long_arrays' is deprecated in PHP 5.3 and greater in Unknown on line 0

Deprecated: Directive 'magic_quotes_gpc' is deprecated in PHP 5.3 and greater in Unknown on line 0
user = 4<br>CURRENT_USER = <br>


1. what are these warnings? How to get rid of them? Could they influence the reason why it does not work?

2. the submitted argument is going into the script, but not as environment variable.

Any idea?

---

### Post by pqwoerituytrueiwoq on 2011-07-04
is this on a web server?
you could use curl to run the script
curl [http://127.0.0.1/path/to/myscript.php?variable=value&message=hello%20world](http://127.0.0.1/path/to/myscript.php?variable=value&message=hello%20world)

---

### Post by ELMIT on 2011-07-05
Thanks for your solution, ... it works perfect at the command line, but not in cron !!!!

My cron line:

55 11 * * * ronald	/usr/bin/curl [http://localhost/websites/TwRon/TwR.php?user=3](http://localhost/websites/TwRon/TwR.php?user=3) >/dev/null;


Any idea?

---

### Post by SeijiSensei on 2011-07-05
> **ELMIT said:**
> 
1. what are these warnings? How to get rid of them? Could they influence the reason why it does not work?

The PHP module is apparently compiled to expect the PHP IMAP libraries.  You can solve that problem by running "sudo apt-get install php5-imap".

It's also possible that there's a versioning difference between the web server PHP binary and the one you run from the command line.

Reinstall PHP like this:

```
sudo apt-get install php5 php5-cli
```

so you'll insure everything is compatible.

> $user = $argv[1];

PHP counts arguments starting from zero.  The first passed argument is stored as $argv[0].

I don't know why this won't work from cron, but if curl won't work either, there's something more profound at work.  Whose crontab is this stored in?  Are you running the program from the command line with the same user and permissions as it's running with from cron?

---

### Post by ELMIT on 2011-07-05
After no try resulted in a execution, I tried a very simple cron line:

56 6 * * *	ronald cd '/home/ronald' ; touch cron-check;

The file is not created!
So, cron does not work at all!!!

How to fix that?

---

### Post by SeijiSensei on 2011-07-05
Let's start with the basics.  Is cron actually running?  Try "ps ax | grep cron" and see.

Next, where did you put the entry to "touch cron-check"?  By editing /etc/crontab, or by using the crontab command?  If you used "crontab -e" then you should not include the username in the entry; you only do that in /etc/crontab.

---

### Post by ELMIT on 2011-07-05
ps ax |grep cron gives me:
 1223 ?        Ss     0:00 cron

... it is running

The line:
56 6 * * * ronald cd '/home/ronald' ; touch cron-check;

I put into /etc/cron.d/ronald


This cron is running on my desktop. It worked for years so. I upgraded from 8.04 LTS in steps to 11.04 and somewhere here it must have stopped working.

---

### Post by ELMIT on 2011-07-05
... after many hours I found the answer with:

grep cron /var/log/syslog

> Jul  6 09:01:01 ronald-desktop cron[1223]: (*system*ronald) ERROR (Syntax error, this crontab file will be ignored)


Looking all the hours in the crontab file, I found, that I had in a completely different place the hour 43 (should have been minutes, ...)

That was a learning experience!!!!

---

