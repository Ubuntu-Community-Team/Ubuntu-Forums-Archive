---
title: "start script when machine boots up"
date: 2012-04-11
forum: General Help
---

### Post by winzip on 2012-04-11
I start jboss server from command line with commands.
$jboss_init.sh start.

This works fine. However i want this start script to run when machine boots up.
I have gone through that this can be achieved by copying scripts to init.d folder ?
I would like to know what are the steps involved to run a start up script when machine booys up ?
System: ununtu 10.04 server os

---

### Post by Toz on 2012-04-11
Try adding the command to the end of /etc/rc.local before the "exit 0" command. Also make sure you indicate the complete path to the jboss_init.sh file. For example, something like:
```
/path/to/jboss_init.sh start
```

---

### Post by winzip on 2012-04-15
Thanks. You are very much helpful. I,ll test your suggestion in a machine where presently jboss is not installed. Is there any executable script availanle using which i could test your suggestion ? I am stuck at this part and so i cant test your comment. Could you please suggest a workaround here ?
Thanks.

---

### Post by Toz on 2012-04-15
Are you wishing to test whether a script executed in this location will work? It will as long as X (gui) is not required. I've never used jboss so I'm not sure. But if its a service you're trying to start - it should work.

You could try something like this:
```

echo "Here I am" > /tmp/test
```
...then after you've booted, check the contents of the file /tmp/test

EDIT: Just googled about jboss and came across this link ([http://www.caseyfulton.com/installing-jboss-as-6-0-final-on-ubuntu-server-11-04-for-mere-mortals/]("http://www.caseyfulton.com/installing-jboss-as-6-0-final-on-ubuntu-server-11-04-for-mere-mortals/")) that shows how to do it using init scripts. 

Either method should work.

---

### Post by winzip on 2012-04-16
> **Toz said:**
> 

You could try something like this:
```

echo "Here I am" > /tmp/test
```...then after you've booted, check the contents of the file /tmp/test




This does not work.

I have tested it.

Here is what I have ...


[B]etc/rc.local
----------------[/B]
[I]
/root/onlytestscript.sh
exit 0[/I]


[B]onlytestscript.sh
----------------------[/B]
[I]#!/bin/sh
echo "Here I am" > /tmp/test[/I]



I rebooted the system . but there was no test  file   in   /tmp  dir.

Could you please check in your system  if this  approach works?

---

### Post by Toz on 2012-04-16
It worked fine here. Did you make the script executable?

```

$ cat /etc/rc.local
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
/root/onlytestscript.sh
exit 0

```
```

$ sudo cat /root/onlytestscript.sh
[sudo] password for toz: 
#!/bin/sh
echo "Here I am" > /tmp/test

```
```

$ cat /tmp/test 
Here I am

```
```

$ sudo ls -l /root
total 4
-rwxr-xr-x 1 root root 39 Apr 16 11:13 onlytestscript.sh

```

---

### Post by perspectoff on 2012-04-16
Any program (or script) can be made to Autostart at bootup by creating a symbolic link to that program (or script) in the ~/.config/autostart folder.

For example, to start Firefox at bootup, create a symbolic link:

sudo ln -s /usr/bin/firefox ~/.config/autostart

Presumably you could do this with a script that has executable permissions assigned to it, as well.

---

