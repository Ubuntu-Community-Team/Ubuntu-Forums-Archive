---
title: "apt-get/synaptic and proxy problem - help needed"
date: 2004-10-23
forum: General Help
---

### Post by dunric on 2004-10-23
I've correctly configured http proxy settings for both apt and synaptic.
When I started synaptic for the first time, all indexes have downloaded. I was able to upgrade with newer packages.
When I run reload in synaptic (or apt-get update) next time it stops with following error messages:
```

Err http://archive.ubuntu.com warty/universe Packages
  Connection failed
Err http://archive.ubuntu.com warty/universe Release
  Connection failed
Err http://archive.ubuntu.com warty/universe Sources
  Connection failed
Err http://archive.ubuntu.com warty/universe Release
  Connection failed
Fetched 5105B in 3s (1617B/s)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/warty/main/binary-i386/Packages.gz  Connection failed
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/warty/main/binary-i386/Release  Connection failed

```
I thought I breaked somehow apt configuration so I reinstalled whole Ubuntu 4.10 from fresh but again - **for the first time all went allright**, all indexes have been fetched, **for the second time suddenly all connections failed**. I didn't touch any settings, proxy is working all the time (I write this post from Firefox connected through the same proxy server).
What the hell am I doing bad ?  #-o 

My proxy settings:
```

In /etc/apt/apt.conf I have following line
Acquire::http::Proxy "http://myname:mypassword@ourproxy.ourdomain:4480";

In Synaptic - Settings/Preferences/Network -> Manual proxy configuration I have
HTTP proxy: http://myname:mypassword@ourproxy.ourdomain  Port: 4480

I even tried to set http_proxy variable but got the same results :( 

```

Thx

---

### Post by arctic on 2004-10-23
hi dunric and welcome :)

open a terminal as root and ping your apt-ressources mirror. then run in another terminal at the same time apt-get update. i know this bug from debian/knoppix/kanotix/yoper. somehow apt has some problems with certain modems/routers. once you ping your mirror, you should be able to get all files, although it is a "stupid" way to do apt-get. but it works. ;)

---

### Post by dunric on 2004-10-23
Pinging repository server is impossible because our LAN is connected to Internet only through proxy so routing or NAT is not supported.

I now suspect it has nothing to do with proxy or apt-get. I did later with synaptic many upgrades and installations and all went flawlessly. After a 2 hours I tried to fetch indexes again and *bump* - it worked ! After it finished I tried to update indexes again and ... same connection errors as before  :evil: 

It looks like repository servers have some kind of protection against "repeated traffic" from one IP address with some timeout. Could anybody confirm my guess ?

Thx in advance

---

### Post by bluefreak on 2004-10-24
i am also having proxy troubles....

i have        Acquire::http::Proxy "http://203.124.2.15:8080";      in my apt.conf

but i get these errors....


Err [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/universe Packages
  Could not resolve '8080'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/universe Release
  Could not resolve '8080'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/universe Sources
  Could not resolve '8080'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/universe Release
  Could not resolve '8080'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/warty/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/warty/universe/binary-i386/Packages.gz)  Could not resolve '8080'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/warty/universe/binary-i386/Release](http://archive.ubuntu.com/ubuntu/dists/warty/universe/binary-i386/Release)  Could not resolve '8080'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/warty/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/warty/universe/source/Sources.gz)  Could not resolve '8080'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/warty/universe/source/Release](http://archive.ubuntu.com/ubuntu/dists/warty/universe/source/Release)  Could not resolve '8080'
Reading Package Lists... Done
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_warty_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.


whenever i try to apt- get update.  i am trying to get the universe repository. when i comment the universe repositories out of the sources.conf, it can update ok.

---

### Post by bluefreak on 2004-10-24
> **bluefreak]i am also having proxy troubles....

i have        Acquire::http::Proxy "http://203.124.2.15:8080" said:**
> http://archive.ubuntu.com[/url] warty/universe Packages
  Could not resolve '8080'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/universe Release
  Could not resolve '8080'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/universe Sources
  Could not resolve '8080'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/universe Release
  Could not resolve '8080'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/warty/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/warty/universe/binary-i386/Packages.gz)  Could not resolve '8080'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/warty/universe/binary-i386/Release](http://archive.ubuntu.com/ubuntu/dists/warty/universe/binary-i386/Release)  Could not resolve '8080'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/warty/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/warty/universe/source/Sources.gz)  Could not resolve '8080'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/warty/universe/source/Release](http://archive.ubuntu.com/ubuntu/dists/warty/universe/source/Release)  Could not resolve '8080'
Reading Package Lists... Done
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_warty_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.


whenever i try to apt- get update.  i am trying to get the universe repository. when i comment the universe repositories out of the sources.conf, it can update ok.
 oh, it seems that this problem has been rectified. all it needed was a restart....

---

### Post by kOoLiNuS on 2006-11-15
> **dunric said:**
> 

My proxy settings:
```

In /etc/apt/apt.conf I have following line
Acquire::http::Proxy "http://myname:mypassword@ourproxy.ourdomain:4480";

In Synaptic - Settings/Preferences/Network -> Manual proxy configuration I have
HTTP proxy: http://myname:mypassword@ourproxy.ourdomain  Port: 4480 

```

Hi people ... maybe a bit old topic but with Dapper 6.06 when i open Synaptic i can only specify IP address and port, no mention for user authentication.

also i've tried to enter a value like
[B]Proxy HTTP: [ myuser:password@IP-of-theproxy]    Port: [ port-number ]
[/B]
but Synaptic {version 0.57.8} continues to fail .... any idea ?

---

### Post by libran_alok on 2007-09-21
Try this,... this will work

Acquire::http::Proxy "http://YourDomain\ourloginname:yourpassword@proxy:4480";


cheers!

---

### Post by jakswa on 2008-05-19
> **arctic said:**
> hi dunric and welcome :)

open a terminal as root and ping your apt-ressources mirror. then run in another terminal at the same time apt-get update. i know this bug from debian/knoppix/kanotix/yoper. somehow apt has some problems with certain modems/routers. once you ping your mirror, you should be able to get all files, although it is a "stupid" way to do apt-get. but it works. ;)

THANK YOU!  Worked like a charm! ^.^

edit: nevermind, fail... just looked to be working >.<

---

