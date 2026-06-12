---
title: "Ubuntu Ping Monitor with email alert"
date: 2011-10-26
forum: General Help
---

### Post by collisionystm on 2011-10-26
I just put this together and wanted to share.

I needed to keep an eye on my servers and I wanted to receive email alerts in case one should become unavailable.

I used some bits I found online and put this together.

You need to install mailutils to make it work

```
sudo apt-get install mailutils
```
> [SIZE=1]

#!/bin/bash
HOSTS="IP ADDRESS OF SERVER"
COUNT=4
for myHost in $HOSTS
do
  count=$(ping -c $COUNT $myHost | grep 'received' | awk -F',' '{ print $2 }' | awk '{ print $1 }')
  if [ $count -eq 0 ]; then
    # 100% failed
        echo "Server failed at $(date)" | mail -s "VPN Server Down" [EMAIL="admin@domain.com"]admin@domain.com[/EMAIL]
        echo "Host : $myHost is down (ping failed) at $(date)"
  fi
done

[/SIZE]I made named it hostping.sh, made it executable and put it into /root
```
chmod +x hostping.sh
``````
sudo cp hostping.sh /root
```Then I added it into my crontab to run every five minutes.

```
sudo crontab -e
```5 * * * * sh /root/hostping.sh




Used here
[http://www.quietearth.us/articles/2006/09/25/Ubuntu-Sending-command-line-mail](http://www.quietearth.us/articles/2006/09/25/Ubuntu-Sending-command-line-mail)

And here
[http://www.cyberciti.biz/tips/simple-linux-and-unix-system-monitoring-with-ping-command-and-scripts.html](http://www.cyberciti.biz/tips/simple-linux-and-unix-system-monitoring-with-ping-command-and-scripts.html)

Hopefully this saves someone a lot of time!!!

In order to monitor multiple servers, just extended your script file with the same code. 

> [SIZE=1]
  
#!/bin/bash
HOSTS="IP ADDRESS OF SERVER"
COUNT=4
for myHost in $HOSTS
do
  count=$(ping -c $COUNT $myHost | grep 'received' | awk -F',' '{ print $2 }' | awk '{ print $1 }')
  if [ $count -eq 0 ]; then
    # 100% failed
        echo "Server failed at $(date)" | mail -s "VPN Server Down" [EMAIL="admin@domain.com"]admin@domain.com[/EMAIL]
        echo "Host : $myHost is down (ping failed) at $(date)"
  fi
done
  

[/SIZE][SIZE=1]
#!/bin/bash
HOSTS="IP ADDRESS OF SERVER"
COUNT=4
for myHost in $HOSTS
do
  count=$(ping -c $COUNT $myHost | grep 'received' | awk -F',' '{ print $2 }' | awk '{ print $1 }')
  if [ $count -eq 0 ]; then
    # 100% failed
        echo "Server failed at $(date)" | mail -s "VPN Server Down" [EMAIL="admin@domain.com"]admin@domain.com[/EMAIL]
        echo "Host : $myHost is down (ping failed) at $(date)"
  fi
done


[/SIZE][SIZE=1]
#!/bin/bash
HOSTS="IP ADDRESS OF SERVER"
COUNT=4
for myHost in $HOSTS
do
  count=$(ping -c $COUNT $myHost | grep 'received' | awk -F',' '{ print $2 }' | awk '{ print $1 }')
  if [ $count -eq 0 ]; then
    # 100% failed
        echo "Server failed at $(date)" | mail -s "VPN Server Down" [EMAIL="admin@domain.com"]admin@domain.com[/EMAIL]
        echo "Host : $myHost is down (ping failed) at $(date)"
  fi
done


[/SIZE][SIZE=1]
#!/bin/bash
HOSTS="IP ADDRESS OF SERVER"
COUNT=4
for myHost in $HOSTS
do
  count=$(ping -c $COUNT $myHost | grep 'received' | awk -F',' '{ print $2 }' | awk '{ print $1 }')
  if [ $count -eq 0 ]; then
    # 100% failed
        echo "Server failed at $(date)" | mail -s "VPN Server Down" [EMAIL="admin@domain.com"]admin@domain.com[/EMAIL]
        echo "Host : $myHost is down (ping failed) at $(date)"
  fi
done


[/SIZE]Thanks for reading!! :KS

---

### Post by seven01 on 2012-01-18
Nice! I tried it and it works fine.

Is there somehow to add this into the script:


[LIST]
[*]Only send one email when host is down and then send one mail when host is up again?
[/LIST]

[LIST]
[*]When host is down send a ping to another host?
[/LIST]
This function would make it possible to have a server in sleep-mode in wol as a backup and wake it up if the first one goes down. And at the same time get a email notification for what happend.


Anyone knows if and how this could be done?


:popcorn:

---

### Post by dcstar on 2012-01-19
> **collisionystm said:**
> I just put this together and wanted to share.

I needed to keep an eye on my servers and I wanted to receive email alerts in case one should become unavailable.
........

So the **checkservice** package wouldn't do the job?

---

### Post by collisionystm on 2012-01-21
> **dcstar said:**
> So the **checkservice** package wouldn't do the job?


Never even heard of it.

---

### Post by fixed4life on 2013-04-28
This might make your life a little easier...  My script (below) references a list document of hosts to ping, compiles a list of down hosts, and then emails that list.... is a little cleaner than multiple emails..  I named this monitor.sh and put it in /usr/local/bin/monitor/ with another file called hosts.list (the hosts to ping file, 1 per line).  If hosts are down (return 0 for 3 pings) it echos them to a new file it creates called hosts_down then emails the contents of that list and deletes the file for a fresh start next time.  I run this every 10 minutes with cron (there are many, many hosts), but feel free to do whatever..  It should also be noted that you should > /dev/null the output in cron if you plan to use DNS rather than IP's (to keep any messages from building up in local mail if the problem was DNS related).

It still could use some improvement though... I think I would like it to set the number of check cycles before considering a host to be down, but I have not gotten to that yet...

```

#!/bin/bash
# Simple Ping Monitor for hosts v0.3  | Charles Phillips | cphilllips.ia@gmail.com
#
# We parse this file to retrieve Hosts
HOSTS=$(cat /usr/local/bin/monitor/hosts.list)

## Check Hosts and compile a list of ones that may be unreachable
for myHost in $HOSTS;
do
 ping -q -c 3 $myHost > /dev/null
  if [ ! $? -eq 0 ]
   then
    echo "Host: $myHost is unresponsive (ping failed)" >> /usr/local/bin/monitor/down_now
  fi
done

## Email that list and remove the file for next check
# Set email VARS
SUBJECT="[ALERT] Host(s) Unresponsive!"
EMAILID="you@changeme.com"
EMAILFROM="monitor@changeme.com

#Send email and remove list
if [ -e /usr/local/bin/monitor/down_now ];
  then
    echo "$(cat /usr/local/bin/monitor/down_now)" | mail -s "$SUBJECT  $(date)" $EMAILID -- -r $EMAILFROM
    rm -rf /usr/local/bin/monitor/down_now
else
    exit 0
fi

exit 0


```

---

### Post by oldos2er on 2013-04-28
Closed, please don't bump old threads.

---

