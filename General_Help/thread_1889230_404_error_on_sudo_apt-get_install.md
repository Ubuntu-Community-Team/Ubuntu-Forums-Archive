---
title: "404 error on sudo apt-get install"
date: 2011-12-01
forum: General Help
---

### Post by skytreader on 2011-12-01
Hi. I'm trying to install openjdk on an Ubuntu 11.04 VM on Mac. However, I'm running into 404 errors on the command line which I can't diagnose what.

```
sudo apt-get install openjdk-6-jre-headless
...
Err http://ph.archive.ubuntu.com/ubuntu/ natty-updates/main openjdk-6-jre-lib all 6b22-1.10.2-0ubuntu1~11.04.1
  404  Not Found [IP: 10.16.3.143 8080]
Err http://ph.archive.ubuntu.com/ubuntu/ natty-updates/main tzdata-java all 2011g-0ubuntu0.11.04
  404  Not Found [IP: 10.16.3.143 8080]
Err http://security.ubuntu.com/ubuntu/ natty-security/main openjdk-6-jre-lib all 6b22-1.10.2-0ubuntu1~11.04.1
  404  Not Found [IP: 10.16.3.141 8080]
Err http://security.ubuntu.com/ubuntu/ natty-security/main openjdk-6-jre-headless i386 6b22-1.10.2-0ubuntu1~11.04.1
  404  Not Found [IP: 10.16.3.141 8080]
Err http://security.ubuntu.com/ubuntu/ natty-security/main icedtea-6-jre-cacao i386 6b22-1.10.2-0ubuntu1~11.04.1
  404  Not Found [IP: 10.16.3.141 8080]
Err http://security.ubuntu.com/ubuntu/ natty-security/main icedtea-6-jre-jamvm i386 6b22-1.10.2-0ubuntu1~11.04.1
...

```

But if I ping

```

 ping 10.16.3.141
PING 10.16.3.141 (10.16.3.141) 56(84) bytes of data.
64 bytes from 10.16.3.141: icmp_req=1 ttl=63 time=1.55 ms
64 bytes from 10.16.3.141: icmp_req=2 ttl=63 time=3.22 ms
64 bytes from 10.16.3.141: icmp_req=3 ttl=63 time=4.00 ms
64 bytes from 10.16.3.141: icmp_req=4 ttl=63 time=174 ms
64 bytes from 10.16.3.141: icmp_req=6 ttl=63 time=4.16 ms
64 bytes from 10.16.3.141: icmp_req=7 ttl=63 time=2.19 ms
64 bytes from 10.16.3.141: icmp_req=8 ttl=63 time=4.98 ms
64 bytes from 10.16.3.141: icmp_req=9 ttl=63 time=3.81 ms
64 bytes from 10.16.3.141: icmp_req=10 ttl=63 time=6.09 ms
64 bytes from 10.16.3.141: icmp_req=11 ttl=63 time=3.89 ms
64 bytes from 10.16.3.141: icmp_req=12 ttl=63 time=3.86 ms
64 bytes from 10.16.3.141: icmp_req=13 ttl=63 time=0.009 ms
64 bytes from 10.16.3.141: icmp_req=14 ttl=63 time=3.99 ms
^C
--- 10.16.3.141 ping statistics ---
14 packets transmitted, 13 received, 7% packet loss, time 13047ms
rtt min/avg/max/mdev = 0.009/16.610/174.132/45.496 ms

```

Any ideas? Is this my network's problem?

---

### Post by papibe on 2011-12-01
It looks like a temporary problem.

You may try to set up different software server repositories. Check the section 'Download Server' in this [help]("https://help.ubuntu.com/community/Repositories/Ubuntu") page.

Regards.

---

### Post by galvatron408 on 2011-12-03
404 error means that whatever you requested wasn't found. maybe it doesn't exists.

Look what happens when I try to grab something from yahoo.com that doesn't exist...

curl [www.yahoo.com/something_that_doesnt_exist](www.yahoo.com/something_that_doesnt_exist)

<html>
<head>
<meta http-equiv="refresh" content="10;url=/">
	<title>Yahoo!</title>
</head>

<body>
<center>
<table width=650 cellpadding=0 cellspacing=2 border=0>
	<tr>
	<td width=1% valign=top><a href="/[COLOR="Black"]**404**[/COLOR]/*http://www.yahoo.com"><img src=http://us.i1.yimg.com/us.yimg.com/i/yahoo.gif width=147 height=31 border=0 alt="Yahoo"></a></td>

---

### Post by oldtimer7777 on 2011-12-03
Install Jave JRE from the PPA instead:

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

It is about 1/4th the way down the checklist above.


> **skytreader said:**
> Hi. I'm trying to install openjdk on an Ubuntu 11.04 VM on Mac. However, I'm running into 404 errors on the command line which I can't diagnose what.

```
sudo apt-get install openjdk-6-jre-headless
...
Err http://ph.archive.ubuntu.com/ubuntu/ natty-updates/main openjdk-6-jre-lib all 6b22-1.10.2-0ubuntu1~11.04.1
  404  Not Found [IP: 10.16.3.143 8080]
Err http://ph.archive.ubuntu.com/ubuntu/ natty-updates/main tzdata-java all 2011g-0ubuntu0.11.04
  404  Not Found [IP: 10.16.3.143 8080]
Err http://security.ubuntu.com/ubuntu/ natty-security/main openjdk-6-jre-lib all 6b22-1.10.2-0ubuntu1~11.04.1
  404  Not Found [IP: 10.16.3.141 8080]
Err http://security.ubuntu.com/ubuntu/ natty-security/main openjdk-6-jre-headless i386 6b22-1.10.2-0ubuntu1~11.04.1
  404  Not Found [IP: 10.16.3.141 8080]
Err http://security.ubuntu.com/ubuntu/ natty-security/main icedtea-6-jre-cacao i386 6b22-1.10.2-0ubuntu1~11.04.1
  404  Not Found [IP: 10.16.3.141 8080]
Err http://security.ubuntu.com/ubuntu/ natty-security/main icedtea-6-jre-jamvm i386 6b22-1.10.2-0ubuntu1~11.04.1
...

```But if I ping

```

 ping 10.16.3.141
PING 10.16.3.141 (10.16.3.141) 56(84) bytes of data.
64 bytes from 10.16.3.141: icmp_req=1 ttl=63 time=1.55 ms
64 bytes from 10.16.3.141: icmp_req=2 ttl=63 time=3.22 ms
64 bytes from 10.16.3.141: icmp_req=3 ttl=63 time=4.00 ms
64 bytes from 10.16.3.141: icmp_req=4 ttl=63 time=174 ms
64 bytes from 10.16.3.141: icmp_req=6 ttl=63 time=4.16 ms
64 bytes from 10.16.3.141: icmp_req=7 ttl=63 time=2.19 ms
64 bytes from 10.16.3.141: icmp_req=8 ttl=63 time=4.98 ms
64 bytes from 10.16.3.141: icmp_req=9 ttl=63 time=3.81 ms
64 bytes from 10.16.3.141: icmp_req=10 ttl=63 time=6.09 ms
64 bytes from 10.16.3.141: icmp_req=11 ttl=63 time=3.89 ms
64 bytes from 10.16.3.141: icmp_req=12 ttl=63 time=3.86 ms
64 bytes from 10.16.3.141: icmp_req=13 ttl=63 time=0.009 ms
64 bytes from 10.16.3.141: icmp_req=14 ttl=63 time=3.99 ms
^C
--- 10.16.3.141 ping statistics ---
14 packets transmitted, 13 received, 7% packet loss, time 13047ms
rtt min/avg/max/mdev = 0.009/16.610/174.132/45.496 ms

```Any ideas? Is this my network's problem?

---

### Post by thaelim on 2011-12-03
Usually this problem occurs if the archive has been updated but your system hasn't run apt-get update yet. Simple solution is to manually run it:```
sudo apt-get update
```

---

### Post by raja.genupula on 2011-12-03
if you got any errors please post them here after the above command and place that code between ```
 
``` by clicking at # in this post  window

---

