---
title: "finding a .php process"
date: 2011-05-07
forum: General Help
---

### Post by berryboy on 2011-05-07
im trying to write a script that will look for a plugin and check that its running and if not start it 

```
ps ax | grep -v grep | grep aseco.php
```

the above should list the process, if i put it into terminal 
this is incorrect? :/

---

### Post by SeijiSensei on 2011-05-07
That should work if "aseco.php" appears in the "ps ax" output when the script is running.  If you run "ps ax" manually, do you see it?  

Some programs don't display all their command-line parameters by default to ps.  I presume you're running this script using the php binary with a command like "/usr/bin/php /path/to/aseco.php".  Do you see the /usr/bin/php command in the output from "ps ax"?

---

### Post by berryboy on 2011-05-07
thank you for your reply 

no it is not listed in ps ax, i start the plug in by typing 

./path/to/aseco.php

that is all, should i use your method?

---

### Post by berryboy on 2011-05-07
does it have a pid file? and carnt i use that to look and see if its running, heh how do i find this pid file

---

### Post by SeijiSensei on 2011-05-07
PHP scripts don't run natively from the command prompt because they're not written in an appropriate shell language like bash.  You can run a PHP script using the command-line binary like this:

```
/usr/bin/php /path/to/aseco.php
```

You'll need to install the "php5-cli" package if you haven't already done so.

Scripts that run with ./ start with a "hash-bang" at the top of the file telling the operating system what interpreter to use.  For instance, 

```
#!/bin/bash
```

at the top of a script tells the OS to use the bash interpreter.  I believe you can have a PHP script that follows the same procedure like this:

```
#!/usr/bin/php

<?
PHP code
?>

```

but don't hold me to that.  If you can write the script this way, you can run it from the command prompt directly.  I usually just run PHP scripts with the php binary or wrap them in a shell script that invokes the binary along the way:

```
#!/bin/bash

DO SOME STUFF

/usr/bin/php /path/to/script.php

MAYBE DO SOME MORE STUFF

exit 0

```

---

### Post by Habitual on 2011-05-07
lsof +D /path/to/aseco.php

but lsof +D only takes directories, so 
```
lsof +D /path/to | grep aseco\.php
```
"This option causes lsof to search for all open instances of directory D and all the  files  and directories it contains to its complete depth."


You know who owns the file?

lsof -u $user | grep aseco.php
left column is what started the process.

lsof -c p will show you all commands running that start with the letter 'p'

full usage [here]("http://www.manpagez.com/man/8/lsof/")...

---

### Post by berryboy on 2011-05-08
thanks everyone for helping me with this!

i have tried the above, and found it while searching for 'php'

 ```
lsof -c php
```

i'v found it but im unsure how this helps me.
how could i get a script to check for it, using crontab to check every 5mins

```
php     5245 mick  cwd    DIR        3,2    4096 23773203 /home/mick/TMUF/xaseco
```

it has the same .PID number as the other php content

[SIZE="1"]just a snippet for example [/SIZE]
```
php     5245 mick  rtd    DIR        3,1    4096        2 /
php     5245 mick  txt    REG        3,1 5318916   179699 /usr/bin/php5
php     5245 mick  mem    REG        3,1   38412  1208073 /lib/tls/i686/cmov/libnss_files-2.7.so
php     5245 mick  mem    REG        3,1   81728   278912 /usr/lib/php5/20060613+lfs/pdo.so
php     5245 mick  mem    REG        3,1   98180   278468 /usr/lib/php5/20060613+lfs/mysqli.so
php     5245 mick  mem    REG        3,1 1957204   188188 /usr/lib/libmysqlclient.so.15.0.0
```

---

### Post by berryboy on 2011-05-08
I have found a script made for this. but im unsure how to set it up 

```
#!/bin/sh
#
# Starts aseco script
#
# chkconfig: 345 94 06
# description: aseco is the TMN server controller.

MYDESC="aseco"
MYPATH=/home/mick/TMUF/xaseco
MYNAME=aseco
MYLOCK=$MYNAME
DAEMON=$MYPATH/Aseco.sh
MYPIDF=/var/run/$MYNAME.pid
MYCMND="$MYPATH/Aseco.sh"

# Source function library.
. /etc/rc.d/init.d/functions

# Make sure the daemon directory is in the front of the path list
PATH=$MYPATH:$PATH

# See how we were called.
case "$1" in
  start)
        # Change to package directory so config paths can be relative
        cd $MYPATH || \
          { echo "$0: Can't cd to $MYPATH" ; exit 1 ; }
        # Make sure the daemon exists
        [ -f $DAEMON ] || \
          { echo "$0: Daemon not found: $DAEMON" ; exit 1 ; }
        # See if we are already running
        # Note: kill -0 _PID_
        #       returns true if process _PID_ is alive and accepting signals.
        [ -f $MYPIDF ] && kill -0 `cat $MYPIDF` 2>/dev/null && \
          { echo "$0: $MYPIDF exists and process is running" ; exit 1 ; }
        echo -n "Starting $MYDESC: "
        echo -n "$MYNAME "
        su -l -c "$MYCMND &" tmn > $MYPIDF
        chown tmn.tm $MYPIDF
        echo
        touch /var/lock/subsys/$MYLOCK
        ;;
  stop)
        echo -n "Shutting down $MYDESC: "
        echo -n "$MYNAME "
        killproc $MYNAME
        rm -f $MYPIDF
        echo
        rm -f /var/lock/subsys/$MYLOCK
        ;;
  status)
        status $MYNAME
        ;;
  restart)
        $0 stop
        sleep 1
        $0 start
        ;;
  *)
        echo "Usage: $0 {start|stop|status|restart}"
        exit 1
esac

exit 0
```

i'v looked in MYPIDF=/var/run/$MYNAME.pid and cant find a 'aseco.PID'

im really lost on this any ideas at all?

would i just save this as a .sh and start it './check.sh'

---

### Post by berryboy on 2011-05-08
what if i started aseco.php as a daemon would that give me a unique .PID which i could then use?

---

