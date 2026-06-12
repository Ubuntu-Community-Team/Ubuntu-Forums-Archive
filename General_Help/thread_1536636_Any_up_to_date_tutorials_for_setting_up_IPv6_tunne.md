---
title: "Any up to date tutorials for setting up IPv6 tunneling?"
date: 2010-07-22
forum: General Help
---

### Post by YosefKaro on 2010-07-22
All of the tutorials that I am finding for IPv6 tunneling are old and out of date saying to use tspc which simply does not work (no longer found in the repos for obvious reasons).  I have tried using [https://wiki.ubuntu.com/IPv6](https://wiki.ubuntu.com/IPv6) but sixXS has not approved my request and when it comes to freenet6, their software for linux just will not install.  What I need is a good, up-to-date tutorial which will provide step-by-step instructions that actually work.  Any ideas?

-Yos

---

### Post by sanderj on 2010-07-22
Here's good tutorial to get IPv6:


```
sudo apt-get install miredo

```

That's it! Now you have IPv6 and you can visit [ipv6.google.com]("http://ipv6.google.com/")

And checkout my signature.

---

### Post by YosefKaro on 2010-07-22
That works when your ISP offers IPv6 support.  But my problem is, I have to tunnel through IPv4 because my ISP only offers IPv4.

---

### Post by sanderj on 2010-07-23
> **YosefKaro said:**
> That works when your ISP offers IPv6 support.

No. Not true; no ISP support needed. Try it, and you will see.

---

### Post by YosefKaro on 2010-07-23
I have tried it my friend that is why I know it does not work unless your ISP provides IPv6 support.  Otherwise, you have to tunnel.

---

### Post by sanderj on 2010-07-23
> **YosefKaro said:**
> I have tried it my friend that is why I know it does not work unless your ISP provides IPv6 support.  Otherwise, you have to tunnel.

Wanna bet that you don't need ISP support ... ? ;-)

Post the output of 'ifconfig' here.

---

### Post by YosefKaro on 2010-07-23
[http://pastebin.com/LXbupAmh](http://pastebin.com/LXbupAmh)

---

### Post by sanderj on 2010-07-23
Are you sure you've installed 'miredo'? I don't see a teredo interface ...

Below is my ifconfig output. Note the teredo interface.

```


	
show details Jun 13
sander@athlon64:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:92:77:27:ab  
          inet addr:192.168.2.150  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:92ff:fe77:27ab/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1439157 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1081325 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1837817053 (1.8 GB)  TX bytes:93843164 (93.8 MB)
          Interrupt:25 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:862245 errors:0 dropped:0 overruns:0 frame:0
          TX packets:862245 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:122904592 (122.9 MB)  TX bytes:122904592 (122.9 MB)

teredo    Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet6 addr: fe80::ffff:ffff:ffff/64 Scope:Link
          inet6 addr: 2001:0:53aa:64b:1040:ab2f:3c0f:b8c8/32 Scope:Global
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1280  Metric:1
          RX packets:3150 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5647 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:3128342 (3.1 MB)  TX bytes:492430 (492.4 KB)

sander@athlon64:~$

```

---

### Post by YosefKaro on 2010-07-23
Reading package lists... Done
Building dependency tree       
Reading state information... Done
miredo is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up tspc (2.1.1-6.1) ...
Setting up IPv6 tunnel: No common authentication mechanism found
Did you forget to specify a username?
Authentification error

Error is 7: AUTHENTIFICATION_ERROR
TSP session done
invoke-rc.d: initscript tspc, action "start" failed.
dpkg: error processing tspc (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 tspc
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by sanderj on 2010-07-23
Are you sure this is the output of "sudo apt-get install miredo"? I see other package names ...


> **YosefKaro said:**
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
miredo is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up tspc (2.1.1-6.1) ...
Setting up IPv6 tunnel: No common authentication mechanism found
Did you forget to specify a username?
Authentification error

Error is 7: AUTHENTIFICATION_ERROR
TSP session done
invoke-rc.d: initscript tspc, action "start" failed.
dpkg: error processing tspc (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 tspc
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by YosefKaro on 2010-07-23
yos@yos:~$ sudo apt-get install miredo
[sudo] password for yos: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
miredo is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
yos@yos:~$

---

### Post by sanderj on 2010-07-23
And what is now the full output of "ifconfig"?

---

### Post by YosefKaro on 2010-07-23
I'm getting so tired of having to refresh my browser 20 times for each reply...damn, fix the forums already!!!

How do I start miredo ?

---

### Post by sanderj on 2010-07-23
> **YosefKaro said:**
> I'm getting so tired of having to refresh my browser 20 times for each reply...damn, fix the forums already!!!

How do I start miredo ?

miredo should start itself, so I'm surprised it's not showing started / not showing up.

You can restart your system. 
If you don't like that, it could be something like "sudo /etc/init.d/miredo start", or a network restart.

---

### Post by sanderj on 2010-07-24
Any progress? Have you started miredo, or rebooted your machine? If so, does 'ifconfig' show a teredo interface?

If no teredo interface is shown, check your syslog. Here's mine:

```


sander@quirinius:~$ cat /var/log/syslog* | grep -i miredo | sort -u

Jul 24 09:49:45 quirinius miredo[904]: Starting...
Jul 24 09:49:45 quirinius miredo[906]: Cannot resolve Teredo server address "teredo-debian.remlab.net": No address associated with hostname
Jul 24 09:50:39 quirinius miredo[904]: Child 906 exited (code: 0)
Jul 24 09:50:39 quirinius miredo[904]: Reloading configuration on signal 1 (Hangup)
Jul 24 09:50:39 quirinius miredo[904]: Starting...
Jul 24 09:50:40 quirinius miredo[1634]:  (address: 2001:0:53aa:64c:3c1:b29:ad5:e46, MTU: 1280)
Jul 24 09:50:40 quirinius miredo[1634]: New Teredo address/MTU
Jul 24 09:50:40 quirinius miredo[1634]: Teredo pseudo-tunnel started
sander@quirinius:~$


```

---

### Post by mikewhatever on 2010-07-24
Here is a relatively recent tutorial, in case you still need one.
[http://www.linux.com/learn/tutorials/308738-weekend-project-transition-to-ipv6](http://www.linux.com/learn/tutorials/308738-weekend-project-transition-to-ipv6)

---

