---
title: "My System is acting frustratingly weird and I don't know why :("
date: 2011-05-26
forum: General Help
---

### Post by Mechatronical on 2011-05-26
Hi friends,

So first my network appindicator disappeared, then my weather appindicator won't show me the weather, NOW my computer won't let me download anything from the software center and won't let me update anything in the upgrade manager. Please help!

Thank you in advance :)

---

### Post by sanguinoso on 2011-05-26
Can you post the output of ```
ifconfig
```

and ```
ps aux | grep nm-applet
```

and ```
ps aux | grep NetworkManager
```

---

### Post by Mechatronical on 2011-05-26
```
ifconfig
```eth0      Link encap:Ethernet  HWaddr 00:23:ae:3d:f1:86  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:22:5f:b1:f7:c1  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:5fff:feb1:f7c1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:223410 errors:0 dropped:0 overruns:0 frame:1060221
          TX packets:193135 errors:41 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:218798640 (218.7 MB)  TX bytes:33361445 (33.3 MB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18768 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18768 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3369622 (3.3 MB)  TX bytes:3369622 (3.3 MB)


```
ps aux | grep nm-applet
```hubie     5428  0.0  0.3 152600 13804 ?        SLl  11:59   0:00 nm-applet --sm-disable
hubie     7434  0.0  0.0   4160   868 pts/0    S+   14:54   0:00 grep --color=auto nm-applet

```
ps aux | grep NetworkManager
```

root       629  0.0  0.1  26520  4672 ?        Ssl  00:17   0:05 NetworkManager
root      7174  0.0  0.0   2552  1240 ?        S    14:37   0:00 /sbin/dhclient -d -4 -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-eth1.pid -lf /var/lib/dhcp/dhclient-f48e3bb5-1031-4df7-b38f-11cd2b66e2f5-eth1.lease -cf /var/run/nm-dhclient-eth1.conf eth1
hubie     7436  0.0  0.0   4160   868 pts/0    S+   14:55   0:00 grep --color=auto NetworkManager

There you go :) thanks for the response, btw :)

---

### Post by Mechatronical on 2011-05-26
bump?

---

### Post by wildmanne39 on 2011-05-26
> **Mechatronical said:**
> Hi friends,

So first my network appindicator disappeared, then my weather appindicator won't show me the weather, NOW my computer won't let me download anything from the software center and won't let me update anything in the upgrade manager. Please help!

Thank you in advance :)
Hi, what version of ubuntu are you using? Did you remove any packages,What errors are you getting when trying to update.Click on the # key and put the errors between the code boxes.

---

### Post by Mechatronical on 2011-05-27
> **wildmanne39 said:**
> Hi, what version of ubuntu are you using? Did you remove any packages,What errors are you getting when trying to update.Click on the # key and put the errors between the code boxes.

I am using Ubuntu 11.04.
I did not remove any packages.

Here are my errors:

```

Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade:
The package 'ubuntu-desktop' is marked for removal but it is in the removal blacklist.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

This is most likely a transient problem, please try again later.

```

Oh and I don't know what you mean about the # key?

---

### Post by Mechatronical on 2011-05-27
Oh come on! Now my volume indicator is gone! :( :( :( what's going on?!

---

### Post by wildmanne39 on 2011-05-27
> **Mechatronical said:**
> Oh come on! Now my volume indicator is gone! :( :( :( what's going on?!
Hi, I have never seen that message before.
Try this```
sudo apt-get update
sudo apt-get-upgrade
sudo apt-get dist-upgrade
```

---

### Post by linuxinstalledfromhdd on 2011-05-27
You can try creating a new user and logging into that user for the moment.  See if the problem is OS or user configuration setting problems.  Also when you are in there try downloading ubuntu rescue disc for later use, if need be. Make sure to have one handy, just as a precaution.

---

### Post by Mechatronical on 2011-05-27
@wildmanne39

I tried and it didn't do anything :-/

> **linuxinstalledfromhdd said:**
> You can try creating a new user and logging into that user for the moment.  See if the problem is OS or user configuration setting problems.  Also when you are in there try downloading ubuntu rescue disc for later use, if need be. Make sure to have one handy, just as a precaution.

I made a new account and it has the same problem as my main one.

---

### Post by Mechatronical on 2011-05-27
bump?

---

### Post by linuxinstalledfromhdd on 2011-05-27
First you should research what PPA's you have added to your system recently, if any, so you can run a PPA Purge and roll back as many of the customisations you have made to your system.  You are going to probably want to do that from the recovery mode and the root command line.  It may be simpler to burn a reinstallation disc, and reinstall.  There are some really great guides for getting a system put together the way you want it to work.

[http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)

---

### Post by wildmanne39 on 2011-05-27
> **Mechatronical said:**
> bump?

Hi, did you activate the cube or any effects in compiz?

---

