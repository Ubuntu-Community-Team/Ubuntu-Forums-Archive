---
title: "How to disable printing service  - cupsd?"
date: 2011-10-23
forum: General Help
---

### Post by abcuser on 2011-10-23
Hi,
using Ubuntu 11.10/Unity 2D. Using two network commands I have found out that cupsd deamon, looks like printing service, is running:

```
netstat -a -t tcp localhost | grep LISTEN
tcp        0      0 localhost:ipp           *:*                     LISTEN     
tcp6       0      0 ip6-localhost:ipp       [::]:*                  LISTEN     

```
and

```
nmap localhost

Starting Nmap 5.21 ( http://nmap.org ) at 2011-10-23 15:19 CEST
Nmap scan report for localhost (127.0.0.1)
Host is up (0.0069s latency).
Not shown: 999 closed ports
PORT    STATE SERVICE
631/tcp open  ipp

Nmap done: 1 IP address (1 host up) scanned in 0.44 seconds

```

It looks like a printing service is running. I don't use any printer on this PC and I would like to disable printing service to reduce security risk as much as possible.

How to stop printing service running on 631 tcp port?
Regards

---

### Post by tartalo on 2011-10-23
I uninstall it, the added advantages are that you save space in your hard drive and that you will need less updates.

I search for 'cups', 'printing' and 'printer' in Synaptic, there are lot's of packages related printing that you don't need, but read carefully the descriptions because some packages you do need will appear among the results.

You can't unisnstall libcups2 and libcupsimage2, some packages you probably want would go away.

The meta-package ubuntu-desktop must go, although some recommend to keep it to ease dist-upgrades I never had a problem. I wish there was a ubuntu-printing metapackage that was just recommended by ubuntu-desktop.

---

### Post by ajgreeny on 2011-10-23
If you install bootup manager (bum) from the repos you can stop cups running easily, along with many other services which you may not need.

I assume it is still available for 11.10, but things may have changed.

---

### Post by rsvancara on 2011-10-23
Open a terminal and run:


```
sudo update-rc.d cups remove
```

Enter your password you used to log on to the system with.

--Randall
[http://www.knowyourlinux.com](http://www.knowyourlinux.com)

---

