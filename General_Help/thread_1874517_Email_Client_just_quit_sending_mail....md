---
title: "Email Client just quit sending mail..."
date: 2011-11-03
forum: General Help
---

### Post by JoeFriday49 on 2011-11-03
I found several threads concerning the Evolution email client and problems associated with it, but none seemed to help with my problem.  I have 7 different email accounts set up on this machine that Evolution checks and is set up to put the incomming mail in separate folders.  It has worked very well for well over a year now without a hickup until yesterday.  It now refuses to send outgoing mail to any account.  (I use 2 mail servers, one provided by my ISP with 3 associated accounts, the other 4 are from a webspace provider where I own a domain.) 

I'm running Ubuntu 10.04 and have since it was released.  The only thing I've added recently was File Backup Manager and had a problem setting it up and posted this thread [http://ubuntuforums.org/showthread.php?t=1873386](http://ubuntuforums.org/showthread.php?t=1873386)  I have since removed the software to see if that would cure the problem, but it did not help.

Most of the problem "fixes" I can find for problems with Evolution recommend simply changing over to Thunderbird for an email client, so last night I installed and set up this new client.  It too receives mail just fine, but refuses to send it at all. I am reluctant to change clients, due to the large amount of archived information I have stored in various folders. (Almost 1GB) But since Thunderbird gives the same symptoms as Evolution it seems they are suffering from a common problem with this machine.

As an afterthought, my Lady has accounts with both these same providers and they work flawlessly on her windoz boxes using Outlook Express over this home network using the same wireless connection.  And my accounts will also send just fine using their respective webmail clients.

The only error I receive is: Could not connect to smtp.gmail.com: Connection timed out

---

### Post by JoeFriday49 on 2011-11-03
Page #2...  I have set up another PC using Ubuntu with the Evolution and Thunderbird clients...  I get the same results with this machine as I was getting with the laptop...  Receives fine, just won't send.  I also tried completely turning OFF the firewalls in the modem and router and that didn't help either.  I also tried removing the OpenDNS name-server addresses and going back to those provided by my ISP.  Same result...  

Running out of options...

---

### Post by dcstar on 2011-11-04
> **JoeFriday49 said:**
> 
.........
The only error I receive is: Could not connect to smtp.gmail.com: Connection timed out

```
telnet smtp.gmail.com 25
```

---

### Post by JoeFriday49 on 2011-11-04
> **dcstar said:**
> ```
telnet smtp.gmail.com 25
```

Yields:
joefriday49@joefriday49-laptop:~$ telnet smtp.gmail.com 25
Trying 209.85.225.109...
Trying 209.85.225.108...
telnet: Unable to connect to remote host: Connection timed out
joefriday49@joefriday49-laptop:~$ 

Guess that means the DNS isn't resolving?...  It works fine on her windoz boxes through the same network...  I also tried reverting back to my old ISP's DNS settings and that didn't work either...

---

### Post by dcstar on 2011-11-04
> **JoeFriday49 said:**
> Yields:
joefriday49@joefriday49-laptop:~$ telnet smtp.gmail.com 25
Trying **209.85.225.109**...
Trying **209.85.225.108**...
telnet: Unable to connect to remote host: Connection timed out
joefriday49@joefriday49-laptop:~$ 

Guess that means the DNS isn't resolving?...  It works fine on her windoz boxes through the same network...  I also tried reverting back to my old ISP's DNS settings and that didn't work either...

An IP address means DNS is resolving - but those IP addresses listed seem bogus.

smtp.gmail.com on my system resolves to the following:
```
Source	TTL	Address Type	Record Type1	Resolution
smtp.gmail.com.	8	IN	CNAME	gmail-smtp-msa.l.google.com.
gmail-smtp-msa.l.google.com.	127	IN	A	**74.125.127.109**
gmail-smtp-msa.l.google.com.	127	IN	A	**74.125.127.108**
```

---

### Post by JoeFriday49 on 2011-11-04
I ran a Traceroute on smtp.gmail.com and got a blast of stuff that took a couple of minutes to finish...  I can understand how something can be wrong and I'm getting misdirected looking for the mail server, but why would the windows boxes find it just fine running Outlook Express?  

Here's the traceroute output:
joefriday49@joefriday49-laptop:~$ traceroute smtp.gmail.com
traceroute to smtp.gmail.com (209.85.225.109), 30 hops max, 60 byte packets
 1  192.168.10.1 (192.168.10.1)  9.603 ms  9.661 ms  9.800 ms
 2  192.168.0.1 (192.168.0.1)  12.605 ms  13.265 ms  13.431 ms
 3  * * *
 4  atlngahed11-gi1-2-2.network.tds.net (69.128.249.33)  45.565 ms  55.082 ms  64.706 ms
 5  atlngahed12-gi1-2-3.network.tds.net (64.50.238.26)  52.709 ms  53.321 ms  57.472 ms
 6  google-atlnga.peering.tds.net (64.50.238.234)  84.555 ms  30.180 ms  32.582 ms
 7  72.14.233.56 (72.14.233.56)  34.248 ms 72.14.233.54 (72.14.233.54)  36.593 ms  41.853 ms
 8  72.14.239.91 (72.14.239.91)  60.494 ms 209.85.242.214 (209.85.242.214)  62.250 ms 72.14.239.91 (72.14.239.91)  63.875 ms
 9  72.14.237.130 (72.14.237.130)  66.278 ms  67.734 ms  68.706 ms
10  209.85.241.22 (209.85.241.22)  81.791 ms  100.078 ms  84.863 ms
11  209.85.241.35 (209.85.241.35)  86.802 ms 209.85.241.27 (209.85.241.27)  87.599 ms 209.85.241.29 (209.85.241.29)  89.896 ms
12  66.249.95.138 (66.249.95.138)  67.521 ms * 72.14.239.18 (72.14.239.18)  73.618 ms
13  iy-in-f109.1e100.net (209.85.225.109)  72.296 ms  74.570 ms  75.698 ms

---

### Post by dcstar on 2011-11-04
> **JoeFriday49 said:**
> I ran a Traceroute on smtp.gmail.com and got a blast of stuff that took a couple of minutes to finish...  I can understand how something can be wrong and I'm getting misdirected looking for the mail server, but why would the windows boxes find it just fine running Outlook Express?  
.........

Because they must be using different DNS services.

Look at the DNS settings on the Linux boxes and compare them to the Windows settings:
```
cat /etc/resolv.conf
netstat -rn
ifconfig
```

---

### Post by llamabr on 2011-11-04
And if that's the problem, you could just try google dns (when it's working):

[http://code.google.com/speed/public-dns/](http://code.google.com/speed/public-dns/)

---

### Post by amjjawad on 2011-11-05
> **JoeFriday49 said:**
> I'm running Ubuntu 10.04

Hi,

Kindly use [ubuntu] prefix and not [lubuntu] prefix. You are not using Lubuntu as per your post :)
The reason I'm asking for that is because I'm a member of Lubuntu Team and I do search for threads related to Lubuntu issues and offer my help. I always come across many threads where users haven't even used Lubuntu :)

Thank you!

---

### Post by JoeFriday49 on 2011-11-29
> **dcstar said:**
> Because they must be using different DNS services.

Look at the DNS settings on the Linux boxes and compare them to the Windows settings:
```
cat /etc/resolv.conf
netstat -rn
ifconfig
```

Here's what I got.  Looks like it's simply looking at my router:

[COLOR=Navy]joefriday49@joefriday49-laptop:~$ cat /etc/resolv.conf
# Generated by NetworkManager
domain TRENDnet
search TRENDnet
nameserver 192.168.10.1[/COLOR]

The next command yielded:

[COLOR=Navy]joefriday49@joefriday49-laptop:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.10.0    0.0.0.0         255.255.255.0   U         0 0          0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 wlan0
0.0.0.0         192.168.10.1    0.0.0.0         UG        0 0          0 wlan0[/COLOR]

And the final line gave me:

[COLOR=Navy]joefriday49@joefriday49-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:38:55:87:3b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1c:26:c7:52:7a  
          inet addr:192.168.10.101  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:26ff:fec7:527a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:36750 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37732 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24854700 (24.8 MB)  TX bytes:9286242 (9.2 MB)[/COLOR]

What I have done is simply set up all of the email accounts to be handled through a webmail client, which works, it just doesn't solve the problem...

---

