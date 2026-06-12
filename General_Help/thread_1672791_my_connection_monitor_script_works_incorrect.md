---
title: "my connection monitor script works incorrect"
date: 2011-01-21
forum: General Help
---

### Post by greg7385 on 2011-01-21
My promlem is that i wrote a few simple script to monitor the network connection as follows:

script 1 "netmonitor.sh"

> #!/bin/bash
# /usr/local/bin/netmonitor.sh

HOST=www.google.hu

ping -c 1 "$HOST" > /dev/null 2>&1
if [ $? = 0 ]; then
        echo "`date` Network is ready!" |
        cat >> /var/log/net/netmonitor.log
else
        echo "`date` Network seems down, rechecking..." |
        cat >> /var/log/net/netmonitor.log
        sh /usr/local/bin/rescan.sh
fi


script 2. "rescan.sh"
> #!/bin/bash
# /usr/local/bin/rescan.sh

HOST=www.google.com
INTERFACE=br0

ping -c 1 "$HOST" > /dev/null 2>&1
if [ $? = 0 ]; then
        echo "`date` Rechecked! Network is ready!" |
        cat >> /var/log/net/netmonitor.log
else
        echo "`date` Network is down, restarting interface $INTERFACE! " |
        cat >> /var/log/net/netmonitor.log
        sh /usr/local/bin/job.sh
fi


script 3 "job.sh"
> #!/bin/bash
# /usr/local/bin/job.sh

INTERFACE=br0

/sbin/ifdown "$INTERFACE"
/sbin/ifup "$INTERFACE"


/usr/local/bin/restart.sh


and script 4 "restart.sh"
> #!/bin/bash
# /usr/local/bin/restart.sh

HOST=www.google.com
INTERFACE=br0

ping -c 1 "$HOST" > /dev/null 2>&1
if [ $? = 0 ]; then
        echo "`date` Network is ready after interface $INTERFACE restart!" |
        cat >> /var/log/net/netmonitor.log

else
        echo "`date` Network is down, could not recover! " |
        cat >> /var/log/net/netmonitor.log
fi


Also, I added a root cron entry as follows:
> */5 * * * * /usr/local/bin/netmonitor.sh &> /dev/null

so it's run every 5 minutes,

and it works well, when it sees host is down, it restart the connection, BUT as the log shows below, about a half an hour after using  the connection (for example the ssh through the internet or the vpn clients disconnected) , br0 (probably) goes down or something and the script needs always restarting the connection...

the log:
> Fri Jan 21 14:45:01 CET 2011 Network is ready!
Fri Jan 21 14:50:01 CET 2011 Network is ready!
Fri Jan 21 14:55:01 CET 2011 Network is ready!
Fri Jan 21 15:00:01 CET 2011 Network is ready!
Fri Jan 21 15:05:01 CET 2011 Network is ready!
Fri Jan 21 15:10:01 CET 2011 Network is ready!
Fri Jan 21 15:15:01 CET 2011 Network is ready!
Fri Jan 21 15:20:01 CET 2011 Network is ready!
Fri Jan 21 15:25:01 CET 2011 Network is ready!
Fri Jan 21 15:30:01 CET 2011 Network is ready!
Fri Jan 21 15:35:01 CET 2011 Network is ready!
Fri Jan 21 15:40:01 CET 2011 Network is ready!
Fri Jan 21 15:45:01 CET 2011 Network is ready!
Fri Jan 21 15:50:02 CET 2011 Network is ready!
Fri Jan 21 15:55:41 CET 2011 Network seems down, rechecking...
Fri Jan 21 15:56:21 CET 2011 Network is down, restarting interface br0!
Fri Jan 21 15:56:48 CET 2011 Network is ready after interface br0 restart!
Fri Jan 21 16:00:41 CET 2011 Network seems down, rechecking...
Fri Jan 21 16:01:21 CET 2011 Network is down, restarting interface br0!
Fri Jan 21 16:01:48 CET 2011 Network is ready after interface br0 restart!
Fri Jan 21 16:05:41 CET 2011 Network seems down, rechecking...
Fri Jan 21 16:10:41 CET 2011 Network seems down, rechecking...
Fri Jan 21 16:11:21 CET 2011 Network is down, restarting interface br0!
Fri Jan 21 16:11:49 CET 2011 Network is ready after interface br0 restart!
Fri Jan 21 16:15:42 CET 2011 Network seems down, rechecking...
Fri Jan 21 16:16:22 CET 2011 Network is down, restarting interface br0!
Fri Jan 21 16:16:48 CET 2011 Network is ready after interface br0 restart!
Fri Jan 21 16:20:01 CET 2011 Network is ready!
Fri Jan 21 16:25:01 CET 2011 Network is ready!
Fri Jan 21 16:30:01 CET 2011 Network is ready!
Fri Jan 21 16:35:01 CET 2011 Network is ready!
Fri Jan 21 16:40:01 CET 2011 Network is ready!
Fri Jan 21 16:45:01 CET 2011 Network is ready!
Fri Jan 21 16:50:01 CET 2011 Network is ready!


then if i use again , its ready...

Is it possible, that if system don't use the connection after getting the DHCP lease, it close the connection automaticly?

Anyway it works ok, but i don't want to owerwrite my router's flash in every 5 seconds with te new lease, my script probably defeat it soon if i don't do anything :)

Any ideas folks? Please help me and also help out router "BOB" :)

---

### Post by greg7385 on 2011-01-21
Anybody any idea?

---

### Post by greg7385 on 2011-01-22
Still nothing, should I moove thist thread to an other section?

---

### Post by greg7385 on 2011-01-24
I think I didn't describe the whole story, sorry for that.
By the way of introduction, I cant set a static route for Server 1, couse router sets the netmask 255.255.255.255, and the vpn traffic don't go trough. 

Here is the structure of the network:

[IMG]http://img560.imageshack.us/img560/5633/imagehs.png[/IMG]

I edited my scripts, the main problem reduced to some intervals without a known reason to associate.

here the scripts and ifconfig are:
> br0       Link encap:Ethernet  HWaddr 00:e0:20:58:5f:75  
          inet addr:192.168.1.6  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:20ff:fe58:5f75/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6488 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10521 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:619624 (619.6 KB)  TX bytes:1730093 (1.7 MB)

eth0      Link encap:Ethernet  HWaddr 00:ea:01:0f:d2:3e  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2ea:1ff:fe0f:d23e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4664291 errors:0 dropped:257 overruns:0 frame:0
          TX packets:6933147 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3575037370 (3.5 GB)  TX bytes:737493741 (737.4 MB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:e0:20:58:5f:75  
          inet6 addr: fe80::2e0:20ff:fe58:5f75/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:160710 errors:1 dropped:0 overruns:0 frame:1
          TX packets:217417 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:22533908 (22.5 MB)  TX bytes:85660162 (85.6 MB)
          Interrupt:21 Memory:febffc00-febffcff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5840 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5840 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3302404 (3.3 MB)  TX bytes:3302404 (3.3 MB)

tap0      Link encap:Ethernet  HWaddr 2a:b5:f8:fd:95:ce  
          inet6 addr: fe80::28b5:f8ff:fefd:95ce/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:80878 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:6687916 (6.6 MB)  TX bytes:888 (888.0 B)

> 
#!/bin/bash
# /usr/local/bin/netmonitor

HOSTS="google.com google.hu"

COUNT=4

for myHost in $HOSTS
do
  count=$(ping -c $COUNT $myHost | grep 'received' | awk -F',' '{ print $2 }' | awk '{ print $1 }')
  if [ $count -gt 0 ]; then
    echo "`date` Network is ready!" |
    cat >> /var/log/net/netmonitor.log
  elif [ $count -eq 0 ]; then
    echo "`date` 100% packet loss, rechecking with different host..." |
    cat >> /var/log/net/netmonitor.log
    sh /usr/local/bin/rescan.sh

  else
    echo "`date` Network seems down, rechecking with different host..." |
    cat >> /var/log/net/netmonitor.log
    sh /usr/local/bin/rescan.sh

fi
done


> #!/bin/bash
# /usr/local/bin/rescan.sh

HOSTS="www.facebook.com"

COUNT=4

for myHost in $HOSTS
do
  count=$(ping -c $COUNT $myHost | grep 'received' | awk -F',' '{ print $2 }' | awk '{ print $1 }')
  if [ $count -gt 0 ]; then
    echo "`date` Network is ready! Successfull packet transfer with secondary host(s)!" |
    cat >> /var/log/net/netmonitor.log
  elif [ $count -eq 0 ]; then
    echo "`date` 100% packet loss. Transfer failed with secondary host(s), restarting interface!" |
    cat >> /var/log/net/netmonitor.log
    sh /usr/local/bin/job.sh

  else
    echo "`date` Network is down. Transfer failed with secondary host(s) restarting interface!" |
    cat >> /var/log/net/netmonitor.log
    sh /usr/local/bin/job.sh

fi
done

> 
#!/bin/bash
# /usr/local/bin

INTERFACE=br0

/sbin/ifdown "$INTERFACE"
/sbin/ifup "$INTERFACE"


/usr/local/bin/restart.sh

> 
#!/bin/bash
# /usr/local/bin/restart.sh

HOSTS="www.google.com www.facebook.com"

COUNT=4

for myHost in $HOSTS
do
  count=$(ping -c $COUNT $myHost | grep 'received' | awk -F',' '{ print $2 }' | awk '{ print $1 }')
  if [ $count -gt 0 ]; then
    echo "`date` Network is ready, after interface restart!" |
    cat >> /var/log/net/netmonitor.log
  elif [ $count -eq 0 ]; then
    echo "`date` 100% packet loss, connection problems still exists!" |
    cat >> /var/log/net/netmonitor.log

  else
    echo "`date` 100% packet loss, connection problems still exists!" |
    cat >> /var/log/net/netmonitor.log

fi
done

---

### Post by greg7385 on 2011-01-24
?

---

### Post by cbowman57 on 2011-04-02
Did you ever find a solution?

I can't write a bash script to save my life but have been looking for one that delays the start of my conkstart.sh until a connection is established.

---

