---
title: "How to kill process on Ubuntu 10.04 event"
date: 2012-04-04
forum: General Help
---

### Post by mgblake7 on 2012-04-04
Hi

I am in the process of setting up an Ubuntu torrent-server using 10.04, and I need to be able to kill the transmission process if my DSL connection ends for whatever reason.

The reason for this is that I have 2 DSL accounts, one is being used on the router and is capped (unshaped during the day), and the other is uncapped (shaped during the day). So obviously if the DSL connection on Ubuntu was lost and the internet connection on the router was used for Transmission, it would finish my cap fairly quickly.

On a related note, as a fairly inexperienced Ubuntu user I noticed that when I connect to DSL my eth0 is seemingly disabled, meaning that I cannot connect to my Ubuntu machine over the LAN using VNC or RDP.

Any help would be greatly appreciated.

---

### Post by Bill Z on 2012-04-04
There are a number of ways to kill a process if you know the name of the process. Here&#8217;s a couple different ways you can accomplish this. We are going to assume that the process we are trying to kill is named irssi

kill $(pgrep irssi)

killall -v irssi

pkill irssi

kill `ps -ef | grep irssi | grep -v grep | awk &#8216;{print $2}&#8217;`

These techniques can be useful in shell scripts, where you wouldn&#8217;t know the process ID and would need to restart or kill a process.

[http://www.howtogeek.com/howto/ubuntu/kill-a-process-by-process-name-from-ubuntu-command-line/](http://www.howtogeek.com/howto/ubuntu/kill-a-process-by-process-name-from-ubuntu-command-line/)

---

### Post by mgblake7 on 2012-04-04
Thanks for the response Bill

is it possible for a shell script to detect when the DSL connection is dropped? if so how would i go about achieving this?

So Basically:

When event_id(DSL connection dropped) do:
pkill transmission

thanks again for the help.

---

### Post by mgblake7 on 2012-04-05
Bump

---

### Post by mgblake7 on 2012-04-05
Ok so it seems like the cron daemon does something similar to this, but it is based on a specific time rather than the occurrence of a specific system event (dsl disconnection in this case).

Ideas?

---

### Post by mgblake7 on 2012-04-05
Ok so I have made some progess.

I have managed to write a pretty basic script that checks to see whether there is a PPPOE connection active:

```
 #!/bin/bash         

result=`ifconfig ppp`
NOW=$(date)

if [ -z "$result" ] 
then
  pkill transmission
  echo "PPPOE Down, sending kill signal to Transmission Client"
  echo $NOW + ": failed;" > /var/log/dsl
  #send notification mail
else
  echo "PPPOE is UP"
  echo $NOW + ": up;" >> /var/log/dsl
fi
```

The script works exactly as I want it to when I run it in Terminal, however it fails when run using cron.

I added the task to cron using gnome's scheduled tasks.

I came across someone else had an issue with scripts running in cron, and there solution was to remove the password for their keypair, which I have no idea how to do, or what the implications of this are. 

Would appreciate any other ideas!!

---

