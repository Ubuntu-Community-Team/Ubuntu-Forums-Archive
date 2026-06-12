---
title: "Processes started by cron or init.d get wrong locale"
date: 2010-04-23
forum: General Help
---

### Post by DDenlinger on 2010-04-23
I set the default locale:
me@myserver:~$ cat /etc/default/locale
LANG="en_US.UTF-8"

In a login shell (whether root or some other user) I see the expected locale:
me@myserver:~$ locale
LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
. . .

But any process started by cron or init.d sees this:
LANG=
LC_CTYPE="POSIX"
LC_NUMERIC="POSIX"
. . .

This happens even if I sudo -u myuser

This causes problems down the line, for example a java process running under tomcat will use the wrong default charset.  Does anyone know how to get this to use the correct locale?

---

### Post by DDenlinger on 2010-04-24
Adding this to /etc/environment seems to do the trick for cron (but not for init)
LANG=en_US.UTF-8

---

### Post by dcstar on 2010-04-25
> **DDenlinger said:**
> Adding this to /etc/environment seems to do the trick
LANG=en_US.UTF-8

So it's solved then?

---

### Post by DDenlinger on 2010-04-27
Actually this only solves the problem for processes launched by cron.  Processes launched at init time still have the wrong environment.

---

### Post by rnerwein on 2010-04-27
hi
the best will be to set all the stuff you need by yourself in your script.
here a little example of cron's environment handling. 
i start a cron job: /home/gonzo/tmp/x
wich looks like:
#!/bin/bash
env > /home/gonzo/tmp/env.txt
set > /home/gonzo/tmp/set.txt

in /etc/environm the following is given:
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
SET_IN_ENVIRONMENT="BUT_PATH_WAS_MANIPULATED"

the output of env.txt is:
SHELL=/bin/sh
PATH=/usr/bin:/bin
PWD=/home/gonzo
SHLVL=1
HOME=/home/gonzo
LOGNAME=gonzo
SET_IN_ENVIRONMENT=[COLOR=Red]BUT_PATH_WAS_MANIPULATED[/COLOR]
_=/usr/bin/env

the PATH is gone

cron works as designed but you have to follow the rules.
ciao

---

