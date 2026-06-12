---
title: "Low Memory Server restart script"
date: 2012-02-19
forum: General Help
---

### Post by steveodeevo on 2012-02-19
Hi,

I have been working on a recycle script for my server which will restart the box when the memory drops below 10%, my script writing skills suck, so I thought I would ask for some help, you can see my effort so far below, the COMMAND string there will when entered in SSH show the remaining free memory in kb, howevery in my shell script it just complains that "No Such File or directory", so I must be doing something wrong!

Any help would be appreciated! 

```

#!/bin/bash

COMMAND="cat /proc/meminfo|grep \"MemFree*\"|grep -oE \"[[:digit:]]{1,}\"| awk '{print $1}'"

FREEMEM=$COMMAND

echo $FREEMEM

if [ $FREEMEM <= 200000 ] # if mysql not running
then
                echo "Memory lower then 10%, so we kill and restart"
        else
                echo "Memory is fine"

fi

```I got apache, mysql, and courier restarting when it is not in the process list, so I managed something, and before you mention "monit" I installed and tried that but it fails to start on my box just saying "starting monit daemon ...." so I figured stick to shell scripts in crontab for now.

Below are the apache, mysql, and courier scripts if anyone is interested.

**Apache**
```

#!/bin/bash
RESTART="/etc/init.d/apache2 restart"

#path to pgrep command
PGREP="/usr/bin/pgrep"

# Httpd daemon name,
# Under Debian 4.x it is apache2
#HTTPD="httpd"
HTTPD="apache2"

# find httpd pid
$PGREP ${HTTPD}

if [ $? -ne 0 ] # if apache not running
then
 # restart apache
 $RESTART
fi

```**MySQL**

```

#!/bin/bash

RESTART="/etc/init.d/mysql restart"

#path to pgrep command
PGREP="/usr/bin/pgrep"

# mysql daemon name,
# Under Debian 4.x it is mysqld
PROCESS="mysqld"

# find mysql pid
$PGREP ${PROCESS}

if [ $? -ne 0 ] # if mysql not running
then
 # restart mysql
 $RESTART
fi

```**Courier**

```

#!/bin/bash

RESTART="/etc/init.d/courier-imap restart"

#path to pgrep command
PGREP="/usr/bin/pgrep"

# courier daemon name,
PROCESS="couriertcpd"

# find courier pid
$PGREP ${PROCESS}

if [ $? -ne 0 ] # if courier not running
then
 # restart courier
 $RESTART
fi

```

---

### Post by Khayyam on 2012-02-19
> **steveodeevo said:**
> I have been working on a recycle script for my server which will restart the box when the memory drops below 10%, my script writing skills suck, so I thought I would ask for some help, you can see my effort so far below, the COMMAND string there will when entered in SSH show the remaining free memory in kb, howevery in my shell script it just complains that "No Such File or directory", so I must be doing something wrong!

Your variable didn't have the substitution of the command, "$( )", but the string, your also missing a ";" from the 'if .. then'

The following should work (untested):

```
#!/bin/bash

FREEMEM=$(cat /proc/meminfo|grep \"MemFree*\"|grep -oE \"[[:digit:]]{1,}\"| awk '{print $1}')

if [[ $FREEMEM <= 200000 ]]; then
                echo "Memory lower then 10%, so we kill and restart"
        else
                echo "Memory is fine"
fi
```

I have to ask though, why? Linux has very good memory management, there is absolutely no reason to restart/reboot to free up memory. You should read a little of the [Linux Memory Management Wiki](http://linux-mm.org/) as I think you are mistaken about what you might achieve by doing this.

HTH ... khay

---

### Post by steveodeevo on 2012-02-19
Hi,
Its a short term fix really, from about 2 weeks ago my web server has been suddenly switching off for no reason, support said it was memory, although I find it hard to believe that the half a dozen simple websites use more than 2gigs of ram, but anyway, so after it went offline leaving customers without a website again this morning, I got up and decided to throw some scripts on the server to restart the services if they fail , and if it consumes too much memory to reboot the thing rather than let it crash out, and hopefully as a short term fix that will stop me having to manually throw the switch like 3 times everyday!

I am moving everything to new servers at the end of next month so hopefully the problem will go away!

Will try the script and let you know.

---

### Post by Dangertux on 2012-02-19
Have you considered watchdog instead. It uses a much better metric for determining out lf memory status. At very least you should write your script in such a way that does takes into account the fact that a lot lf things are cached

---

### Post by steveodeevo on 2012-02-20
Thank you, I will look into it, to be fair as I am leaving this hosting company in a month, and its only started recently too, I opted for a quick fix approach and will set-up properly on the new server.

---

### Post by Khayyam on 2012-02-20
> **steveodeevo said:**
> Hi,
Its a short term fix really, from about 2 weeks ago my web server has been suddenly switching off for no reason, support said it was memory, although I find it hard to believe that the half a dozen simple websites use more than 2gigs of ram [...]

I see, have you monitored apache for ram usage? If it is a problem your side its more likely an application than the kernel's MM. You might also look at specific sites your hosting for badly coded php, etc.

> **steveodeevo said:**
> Will try the script and let you know.

It should work as is, but I would optomize the FREEMEM variable to the following:

```
FREEMEM=$(cat /proc/meminfo | egrep "^MemFree" |awk '{print $2}')
```

awk can 'print' any field and so the second grep is unnecessary.

HTH ... khay

---

