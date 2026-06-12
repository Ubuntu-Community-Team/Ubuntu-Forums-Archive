---
title: "Is there some way a script can tell if a program is running?"
date: 2011-01-14
forum: General Help
---

### Post by canam101 on 2011-01-14
Is there a file that can be opened and a program name searched for? If it is there, the program is running, else it is not.

Something like that?

I have a program that stops periodically. If I could run a script every 30 minutes or so to check the hypothetical file, it could re-start the program if the program had stopped running.

---

### Post by hwttdz on 2011-01-14
perl-ish pseudocode, make it executable and drop it in a cronjob? 

#!/usr/bin/perl

$program_running = `top -b -n 1 -u username|grep programname`;
chomp($program_running);

if($program_running == "")
{
    system("programname");
}

---

### Post by tgm4883 on 2011-01-14
Something like this should work

From [http://www.anyexample.com/linux_bsd/bash/check_if_program_is_running_with_bash_shell_script.xml](http://www.anyexample.com/linux_bsd/bash/check_if_program_is_running_with_bash_shell_script.xml)
```
#!/bin/sh
SERVICE='httpd'
 
if ps ax | grep -v grep | grep $SERVICE > /dev/null
then
    echo "$SERVICE service running, everything is fine"
else
    echo "$SERVICE is not running"
    echo "$SERVICE is not running!" | mail -s "$SERVICE down" root
fi
```

---

### Post by sisco311 on 2011-01-14
Try something like:
```
pgrep **application_name** &> /dev/null
if [ $? -eq 0 ]; then
  echo "application is running..." 
else
  echo "restart application..."
fi

```

For details, see:
```
man pgrep
```

---

### Post by hawkmage on 2011-01-14
Is this is something that could be started using an upstart script?

If so you could use the "respawn" directive so that th einit process will watch and restart it if the process dies.

---

