---
title: "moblock/blockcontrol Issues"
date: 2009-08-23
forum: General Help
---

### Post by Sylos on 2009-08-23
Hello there and thanks for looking at this post.
I have been using Moblock (on Hardy Heron) for about 6 months now and recently updated it leading to a whole host of problems getting it working again ( from what I can gather a new version called blockcontrol has been released although the status output still says moblock). The details of that may not be important. I have checked whether moblock is running and it says that it is BUT it no longer displays a PID number like it used to. My question is does this mean that it isnt blocking anymore or is it normal?

 I have tried googling this and looked on the phoenix labs site but I dont really understand how the programme works (bit of a newb) and everything on the forum goes well over my head.

Any comments gratefully received.

---

### Post by lovinglinux on 2009-08-23
This might help you: [http://ubuntuforums.org/showthread.php?t=803183](http://ubuntuforums.org/showthread.php?t=803183)

---

### Post by Sylos on 2009-08-24
Thanks for the link. However, I may be being an utter dunce here, but I cant find a clear answer in the post as to whether the stauts output should be showing a PID number. All the posts on the thread you linked that show output of a runnning moblock show a PID. Should it have one?

---

### Post by jre on 2009-08-24
blockcontrol takes care of all (necessary) tasks around moblock.

There are problems with hardy heron LSB init-functions (they are responsible for starting/stopping and showing status and PID). So I´ve switched them off in blockcontrol 1.6.4-1. Make sure you use that version with "dpkg -l blockcontrol".

EDIT: If you are on a version below 1.6.4-1 and can´t update: set LSB="" in /etc/blockcontrol/blockcontrol.conf.

To be sure if it is working I suggest "sudo blockcontrol test".

"status" should give something like:
```
[...]
moblock is running..
PID: 4040    CMD: /usr/bin/moblock -p /var/lib/blockcontrol/guarding.p2p -q 92 -t -r 10 -a 20 /var/log/moblock.log

blockcontrol.wd is running..
PID: 4045    CMD: /bin/sh /usr/bin/blockcontrol.wd
```

---

### Post by lovinglinux on 2009-08-24
> **Sylos said:**
> Thanks for the link. However, I may be being an utter dunce here, but I cant find a clear answer in the post as to whether the stauts output should be showing a PID number. All the posts on the thread you linked that show output of a runnning moblock show a PID. Should it have one?

Sorry. I should have explained better. That link was just to point you to the General Moblock thread, were you can find several discussions about moblock. I wasn't directing you to a specific solution.

---

### Post by Sylos on 2009-08-24
Thanks for the advice.
Jre, I have tried doing the test and status commands and this is what I get.

> ric@ric-desktop:~$ sudo blockcontrol test
[sudo] password for ric: 
Testing moblock:

CAUTION: This is just a simple test to check if moblock blocks outgoing
connections. For this, an IP from the blocklist will be pinged. Then the test
checks if this IP appears in the logfile /var/log/moblock.log.

moblock marks packets to be blocked. This means you have to make sure that the
marked packets are also blocked later (with appropriate iptables rules). If you
are using the default configuration and moblock is started after other firewalls
this will be the case.

This test does not check if you have sane iptables rules or if your complete
blocklist is in the correct format. Therefore success doesn't imply that
everything is working as you expect it.

Also have a look at "blockcontrol status" and test manually with traceroute.

Trying to ping 4.17.192.255 from /var/lib/blockcontrol/guarding.p2p ...
 * moblock marked the IP to be blocked and the IP did not answer.
 * Test succeeded.
ric@ric-desktop:~$ sudo blockcontrol status
Current IPv4 iptables rules (this may take a while):

Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
  820 45800 blockcontrol_in  all  --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW MARK match !0x14 
19542   21M RH-Lokkit-0-50-INPUT  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 blockcontrol_fw  all  --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW MARK match !0x14 
    0     0 RH-Lokkit-0-50-INPUT  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy ACCEPT 16431 packets, 2121K bytes)
 pkts bytes target     prot opt in     out     source               destination         
 2042  121K blockcontrol_out  all  --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW MARK match !0x14 

Chain RH-Lokkit-0-50-INPUT (2 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:25 flags:0x17/0x02 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:22 flags:0x17/0x02 
 1309 65512 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
18233   21M ACCEPT     all  --  eth0   *       0.0.0.0/0            0.0.0.0/0           
    0     0 ACCEPT     udp  --  *      *       192.168.1.254        0.0.0.0/0           udp spt:53 
    0     0 REJECT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 reject-with icmp-port-unreachable 
    0     0 REJECT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp reject-with icmp-port-unreachable 

Chain blockcontrol_fw (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 RETURN     all  --  *      *       192.168.1.0/24       192.168.1.0/24      
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           MARK match 0xa 
    0     0 RETURN     all  --  *      *       0.0.0.0/0            192.168.1.254       
    0     0 NFQUEUE    all  --  *      *       0.0.0.0/0            0.0.0.0/0           NFQUEUE num 92

Chain blockcontrol_in (1 references)
 pkts bytes target     prot opt in     out     source               destination         
  164  5904 RETURN     all  --  *      *       192.168.1.0/24       0.0.0.0/0           
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           MARK match 0xa 
  654 39240 RETURN     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
    2   656 NFQUEUE    all  --  *      *       0.0.0.0/0            0.0.0.0/0           NFQUEUE num 92

Chain blockcontrol_out (1 references)
 pkts bytes target     prot opt in     out     source               destination         
  433 28074 RETURN     all  --  *      *       0.0.0.0/0            192.168.1.0/24      
  177  7460 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           MARK match 0xa reject-with icmp-port-unreachable 
  654 39240 RETURN     all  --  *      lo      0.0.0.0/0            0.0.0.0/0           
    0     0 RETURN     all  --  *      *       0.0.0.0/0            192.168.1.254       
   94  5640 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:443 
  478 28680 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:80 
  206 11529 NFQUEUE    all  --  *      *       0.0.0.0/0            0.0.0.0/0           NFQUEUE num 92

Current IPv6 iptables rules (this may take a while):

Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Please check if the above printed iptables rules are correct!

 * moblock is running


If I understand what you are saying then the fact that the PID is not being displayed doesnt mean much. Which leads me to the question what is PID?
*Found out what the PID is from google search. If moblock doesnt state the PID, does that mean it doesnt have a process identifier? I assume this would be impossible as every process has to have one.*
Many thanks,

---

### Post by jre on 2009-08-25
The pid (process ID) is written to a file, while the process is running. You find it in /var/run. E.g. /var/run/blockcontrol.wd.pid or /var/run/moblock.pid.
In that file you see 4 or 5 digits that are the pid.
The pidfile should always, but only then, exist when the process is running. (note: not all processes have pid files. But moblock and blockcontrol.wd both use pidfiles.)

You can check if a process is running e.g. with
```
ps aux | grep moblock
```

I don´t know, why the output of "status" is, as you get it. This is the code for moblock:
```
status_of_proc $DAEMON $NAME
RETVAL="$?"
if [ "$RETVAL" -eq 0 ] ; then
    echo "PID: $(cat $PIDFILE)    CMD: $(ps -o cmd -p $(cat $PIDFILE) | tail -1)"
    echo
fi
```
status_of_proc outputs in your case "moblock is running", which is just fine. But then, the return code that matches this log message is "0", so the PID and CMD should be shown...
Have you set LSB=""? Check
```
blockcontrol show_config | grep  LSB
```

---

### Post by Sylos on 2009-08-29
It appears from the output that a PID is being generated but moblock is not showing it. The LSB function is turned off as it should be.

I tried using mobloquer to turn off the whitelisting of HTTP and couldnt access google so I am reasonably sure that it is functioning as it should be. Just a bit wierd that the PID isnt being displayed.

If you want me to post any logs or other output for your own investigation then just tell me what you need.

Thanks for the help.

---

