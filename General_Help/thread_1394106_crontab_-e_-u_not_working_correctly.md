---
title: "crontab -e -u not working correctly"
date: 2010-01-30
forum: General Help
---

### Post by thom# on 2010-01-30
I am a new user to Ubuntu 9.10 and I am having difficulty scheduling a script through crontab.

The script runs perfectly well from the command line, however it needs to be run as root.

I am able to create the crontab using:
```
crontab -e -u thomas
```The crontab looks like:
```
# m  h  dom mon dow   command
  *  *  *   *   *     sudo ~/scripts/traffic_alert.sh 2>&1 >> ~/scripts/traffic_alert.log
```[I]
Note: when I save this crontab, the default path is: /tmp/[/I]crontab.kgpT6B/crontab 
If I try to alter the path, the crontab does not install.
*Where should I be saving my crontab to?*

If I keep the default path, the crontab is installed. 
```
crontab -l -u thomas
```Confirms that the crontab is installed.

It is set to run every minute. The output file 'traffic_alert.log' is created, however it is blank.

Below is my script. It checks my network traffic and disconnects from the network the quota is reached. It also produces a warning message using zenity. This script runs from the terminal, however it does not seem to do anything when scheduled by the crontab.

```
#!/bin/bash

interface="eth0"
limit="400"
filepath="/var/lib/vnstat"

# d;0; is the current day. fields 4-5 contain the Tx and Rx counts.
traffic=$[`vnstat --dumpdb -i $interface | grep "d;0;" | cut -d\; -f4-5 | sed -e 's/;/+/g'`]

if [ "$traffic" -ge "$limit" ]; then
    if [ ! -f "$filepath/.alert$interface" ]; then
        # Disconnect from interface
        ifconfig $interface down
        zenity --warning --text "Warning, $limit Mb traffic limit reached. \n\nYou have been disconnected from the network."        
        date >"$filepath/.alert$interface"
    fi
else
    if [ -f "$filepath/.alert$interface" ]; then
        rm -f "$filepath/.alert$interface" 2>/dev/null
    fi
fi
```

---

### Post by howlingmadhowie on 2010-01-30
crontab scripts log to /var/log/syslog, so you should be able to read more about the problem there.  i imagine the problem here is 'sudo'. you could try installing the cronjob as root.

---

### Post by thom# on 2010-01-30
Sorry, I forgot to mention that I have tried removing the crontab for 'thomas' and installing the following one for root:

```
# m  h  dom mon dow   command
  *  *  *   *   *     ~/scripts/traffic_alert.sh 2>&1 >> ~/scripts/traffic_alert.log

```

The crontab installs in the /tmp/ directory, however it does not generate the file 'traffic_alert.log', which makes me assume that it is not working.

Neither of the methods generate the file '/var/lib/vnstat/.alerteth0' which the script is supposed to create.

When the script is run from the command line, this file is generated without any issues and the connection becomes disconnected.

---

### Post by howlingmadhowie on 2010-01-30
have you looked in /var/log/syslog?

---

### Post by thom# on 2010-01-30
Every minute it is running:

> Jan 30 17:43:01 [computer_name] CRON[10362]: (root) CMD (~/scripts/traffic_alert.sh 2>&1 >> ~/scripts/traffic_alert.log)

---

### Post by howlingmadhowie on 2010-01-30
no error messages? okay. i'd add a few error checks to your program and see where it's going wrong. 

some things to check:
1/ where is ~ ? if you run the program as root, ~ will be $HOME of root (probably /root).
2/ is the script set to executable?

---

### Post by thom# on 2010-01-30
Thank for your assistance. 
I adjusted the '~' to /home/thomas/ and the script is now being executed.

However the following lines are not producing the desired output.

```
ifconfig eth0 down
zenity --warning --text "Warning message."
```

When the script is run from the terminal:
'ifconfig eth0 down' is executed and the eth0 connected is disconnected.
'zenity' generates a warning message.

*However, *these two outcomes are not occuring when the crontab runs the script.

Any help with this would be greatly appreciated.

---

### Post by howlingmadhowie on 2010-01-30
zenity is a gtk widgit thing, if i remember correcty. if this is the case, the shell crontab forks for this command may not have $DISPLAY set. i'd try adding something like:

export DISPLAY=':0.0'

to the start of the script. then it may work.

you can check to see if $DISPLAY is set by adding something like:

echo DISPLAY: $DISPLAY 

to the script. 

in case you're not using :0 as your X screen, you can set DISPLAY using something like:

export DISPLAY=`ps a | grep -m1 /usr/bin/X | awk '{ print $6 }'`.0

---

### Post by dcstar on 2010-01-30
> **thom# said:**
> I am a new user to Ubuntu 9.10 and I am having difficulty scheduling a script through crontab.

The script runs perfectly well from the command line, however it needs to be run as root.

I am able to create the crontab using:
```
crontab -e -u thomas
```The crontab looks like:
```
# m  h  dom mon dow   command
  *  *  *   *   *     sudo **~**/scripts/traffic_alert.sh 2>&1 >> ~/scripts/traffic_alert.log
```
........

Do not use relative paths in any cron commands, use explicit paths.

Cron environments are totally different to user shell environments.

---

### Post by thom# on 2010-01-30
Thank you,

Adding ```
export DISPLAY=':0.0'
``` to the script allowed the zenity command to produce the desired warning message.

I will try to do some further reading of cron to determine why the following command doesn't work.
```
ifconfig eth0 down
```

---

### Post by thom# on 2010-01-30
I solved the ifconfig problem by using the path '/sbin/ifconfig' in the shell script.

Thank you for all of your assistance and taking time to explain some of the basics to me.

---

