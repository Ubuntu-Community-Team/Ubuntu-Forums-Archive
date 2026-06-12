---
title: "crontab not working"
date: 2012-06-26
forum: General Help
---

### Post by jerodev on 2012-06-26
I have added a new line to my crontab file, but this line won't work. This is the code of my crontab file:

```
# Music scrobbler
# Every 5 minutes
*/5 * * * * php -f /var/www/Music/scrobble/index.php


# Radio scrobbler
# Every Minute
*/1 * * * * php -f /var/www/fmstats/Scrobble/cron/scrobble.php > /fmstats.log
```
The first line works perfectly, but the second does nothing. It should output a list of radio stations but fmstats.log is always empty. It should also add a row to a database wich doesn't happen either.

If I execute the file manualy using the console or via the browser, it works just fine.

---

### Post by sudodus on 2012-06-26
> **jerodev said:**
> I have added a new line to my crontab file, but this line won't work. This is the code of my crontab file:

```
# Music scrobbler
# Every 5 minutes
*/5 * * * * php -f /var/www/Music/scrobble/index.php


# Radio scrobbler
# Every Minute
*/1 * * * * php -f /var/www/fmstats/Scrobble/cron/scrobble.php > /fmstats.log
```
The first line works perfectly, but the second does nothing. It should output a list of radio stations but fmstats.log is always empty. It should also add a row to a database wich doesn't happen either.

If I execute the file manualy using the console or via the browser, it works just fine.

1. If you want the output every minute, use '*' not '*/1', but maybe that syntax is working.

2. I think that you are not allowed to write to the root directory '/'. Maybe it will work better if you write to your home directory ```
... > /home/jerodev/fmstats.log
```

(use your user account name if different from jerodev)

An alternative is to run crontab as root instead of as user, because then you are allowed to write anywhere. It is more risky, but if you know that you will not overwrite something important it is OK ;-)

---

### Post by jerodev on 2012-06-26
> **sudodus said:**
> An alternative is to run crontab as root instead of as user, because then you are allowed to write anywhere. It is more risky, but if you know that you will not overwrite something important it is OK ;-)

The crontab runs as root, that is why i think it's so weird.

---

### Post by hwttdz on 2012-06-26
Cron spawns a sh shell, not a bash shell, so file piping works a little different.  It's balking at the ">".

---

### Post by uylug on 2012-06-26
A tip that might save you a couple hours:

Never assume cron knows what "php" is, use instead full names, like:

```
/usr/bin/php
```Jobs run under cron can behave in a different way than if run from the command line. This is because of a different environment where environment variables might have different values or even be nonexistant.

Therefore your best bet is to tell the script to redirect stderr to a file, as well as stdout, so you can detect any errors that are currently going unnoticed.

```
* * * * * /usr/bin/php -f /var/www/fmstats/Scrobble/cron/scrobble.php 2>&1 > /fmstats.log
```

Sidenote: It's always better to keep crontab cleaner and simply call a script that will do the rest of the hard work, such as calling other scripts or logging events.

---

### Post by sudodus on 2012-06-26
> **jerodev said:**
> The crontab runs as root, that is why i think it's so weird.

Maybe you also need the full path to php

Check the path with ```
which php
``` and enter that path to the command in crontab.

Try this:

```
# Every Minute
* * * * * /the-correct-path/php -f /var/www/fmstats/Scrobble/cron/scrobble.php > /root/fmstats.log

```
and if you want the log to accumulate, change '>' to '>>' (append)

---

### Post by uylug on 2012-06-26
Lol. Easy questions always get all the answers.

Also, just like sudodus said, use full paths. This is because you really don't know what the $PATH variable will be set to under a cron environment, therefore it is better to avoid relying on it and using full paths

Just thought I'd mention why he said that.

---

