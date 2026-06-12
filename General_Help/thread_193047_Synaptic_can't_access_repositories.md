---
title: "Synaptic can't access repositories?"
date: 2006-06-09
forum: General Help
---

### Post by tjay on 2006-06-09
I just installed 6.06, and finally managed to get Firefox running. My internet connection was definitely working (I could ping any website) but I had to disable IPv6 before Firefox would load anything.

Now I have another problem. Synaptic doesn't work... I added the Ubuntu repositories under Settings and hit Reload, but it couldn't. I think it could load the Security Updates repositories, just couldn't work with the Ubuntu ones. Can't remember...
The Ubuntu repo was set to [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) while the Securities repo was set to [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu).
I changed the [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) to [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) and then I could Reload, but could not download any packages, so I changed it back to "my.archive.ubuntu..."

I noticed once that I got the same error as this guy [http://www.ubuntuforums.org/showthread.php?t=192756&highlight=synaptic](http://www.ubuntuforums.org/showthread.php?t=192756&highlight=synaptic) (No route towards the host), but I didn't copy the error msg down. Is there a log file somewhere?

So I thought maybe I had to disable IPv6 for the whole system. I followed the instructions on this thread [http://www.ubuntuforums.org/showthread.php?t=87798&highlight=IPv6](http://www.ubuntuforums.org/showthread.php?t=87798&highlight=IPv6) and to disable IPv6.

Now I get this when I Reload (since this problem seemed to be getting out of my hands, I started taking notes :p): 

> [http://my.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:](http://my.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:) Could not connect to my.archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://my.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:](http://my.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:) Could not connect to my.archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://my.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg:](http://my.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg:) Could not connect to my.archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:) Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out

Why are the IP addresses all 1.0.0.0? When I ping in the terminal I get "PING my.archive.ubuntu.com (85.133.25.7) 56(84) bytes of data.", which seems to suggest that Synaptic got the IP addresses wrong.

I don't know how to check if IPv6 really is disabled, but I ran lsmod and it gave me this:

> Module                  Size  Used by
isofs                  37688  1
udf                    88452  0
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
ppdev                   9220  0
......
ipv6                  265600  6
......


So what in the world is going on? I can't figure this out at all...
Please help. And please help me like you would help a complete newbie, because that's what I am. I need easy to use instructions and such >.<

---

### Post by pyromithrandir on 2006-06-09
Well, since when you ping the site, you get the IP right, I think you may be on to something with thinking it may be Synaptic.
Try *sudo apt-get update* in a terminal and see if that returns the same errors.

---

### Post by tjay on 2006-06-10
I typed sudo apt-get update in the terminal as you suggested and got this: (I stopped it after what must've been 30 minutes -- that was a lot of Minesweeper matches :P )

> [b]Err [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) dapper Release.gpg
  Could not connect to my.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)[/b]
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Err [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) dapper-updates Release.gpg
  Could not connect to my.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) dapper-backports Release.gpg
  Could not connect to my.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Err [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) dapper Release

Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) dapper-backports Release
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) dapper/main Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) dapper/restricted Packages
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) dapper/universe Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) dapper/multiverse Packages
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) dapper-backports/main Packages
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) dapper-backports/restricted Packages
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) dapper-backports/universe Packages
21% [Connecting to my.archive.ubuntu.com (1.0.0.0)]

---

### Post by jvictor on 2006-06-10
Disable IPV6 systemwide
Use ur ISPs DNS server add in /etc/resolv.conf

---

### Post by pyromithrandir on 2006-06-10
Okay, it is giving us the same problem as before, as expected.
If not for having the right IP address when pinging it, I would say that the problem is probably with the /etc/hosts file. I'm suspect to say that's the cause now, though, but you could post your /etc/hosts anyway?

There's also a chance (though I don't know how) that there is a problem with your /etc/apt/sources.list file, so if you could post that I'd take a look at it.

One possibie fix might be to use different mirrors in your sources.list, i.e. I use us.archive.ubuntu.com instead of my.archive.ubuntu.com. That might not be the fastest way to go, but it might actually, well, go. ;) Although, seeing that security.ubuntu.com gives the same wrong IP problem as my.archive.ubuntu.com does, I don't know that it would help at all.

---

### Post by tjay on 2006-06-10
/etc/resolv.conf:

> #nameserver 192.168.1.1 <-- This is from the original file. My router's ip. The router knows the addresses of my isp's DNS servers.
nameserver 202.188.0.133 <-- New line. ISP's DNS servers.
nameserver 202.188.1.5 <-- New line. ISP's DNS servers.

After adding those 2 lines I tried to Reload the package list again, and got this:

> [http://my.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:](http://my.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:) Could not connect to my.archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://my.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:](http://my.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:) Could not connect to my.archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://my.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg:](http://my.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg:) Could not connect to my.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
[http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:) Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
......

And here's my /etc/apt/sources.list:

> #
# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted


# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted

# Line commented out by installer because it failed to verify:
deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

I tried using just the us mirror, but it gave me the same error:

> [http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:) Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out

](*,)

EDIT: Forgot to post /etc/hosts

> 127.0.0.1 localhost jay
127.0.1.1 jay

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Is 1.0.0.0 my own computer?

---

### Post by tjay on 2006-06-10
I pinged 1.0.0.0 :p Here's what I got back:

> $ ping -c 2 1.0.0.0
PING 1.0.0.0 (1.0.0.0) 56(84) bytes of data.
From 210.187.132.115 icmp_seq=2 Time to live exceeded

--- 1.0.0.0 ping statistics ---
2 packets transmitted, 0 received, +1 errors, 100% packet loss, time 1009ms


Did I just get pong'ed? I looked up 210.187.132.115 on whois.net and it gave me this:

> [whois.melbourneit.com]
Invalid/Unsupported whois name check for: 132.115

What does this mean?

---

### Post by jvictor on 2006-06-10
Did u disable IPV6 ? That can be another villain in the show

---

### Post by tjay on 2006-06-10
I added my ISP's DNS server addresses in /etc/resolv.conf as you suggested, and I also followed the instructions in the 5.10 [HowTo] thread to disable IPv6, but I think it's still running --> lsmod tells me that ipv6 is being used by 6 programs (but it doesnt tell me which 6).

So now I don't know if I have disabled it... But how come ping works regardless of ipv6/4?

---

### Post by jvictor on 2006-06-10
OK lets get this right, I've some questions here

1) How do you connect to the internet , using a wired / wireless router ?

2) Do u use DHCP or Static IP

3) Is there a default gateway added ?, Can u post the o/p of 
$route 

4) Did u reboot after Disabling IPV6 ?

5) Can u run the shell , and give us the o/p of 
$ping my.archive.ubuntu.com 
$less /etc/hosts

---

### Post by tjay on 2006-06-11
OK, here are the answers :p And thanks for helping :)

1) The router has wireless functions, but my computer connects to it using wires, so I guess this counts as a "wired" connection.

2) Static IP.

3) What is an o/p? I did an "echo $route" and it was just blank. I added my router as the gateway under System>Administration>Networking.

4) Yes. I rebooted a few times, but ipv6 is still there in lsmod, with an unknown 6 programs using it.

5) > **$ping my.archive.ubuntu.com** *(I Ctrl-C'ed it after 5 pings)*
PING my.archive.ubuntu.com (85.133.25.7) 56(84) bytes of data.
64 bytes from my.archive.ubuntu.com (85.133.25.7): icmp_seq=1 ttl=42 time=662 ms
64 bytes from my.archive.ubuntu.com (85.133.25.7): icmp_seq=2 ttl=43 time=662 ms
64 bytes from my.archive.ubuntu.com (85.133.25.7): icmp_seq=3 ttl=43 time=662 ms
64 bytes from my.archive.ubuntu.com (85.133.25.7): icmp_seq=4 ttl=43 time=662 ms
64 bytes from my.archive.ubuntu.com (85.133.25.7): icmp_seq=5 ttl=43 time=664 ms

--- my.archive.ubuntu.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4000ms
rtt min/avg/max/mdev = 662.116/662.832/664.477/0.841 ms

> **$less /etc/hosts**
127.0.0.1 localhost jay
127.0.1.1 jay

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by jvictor on 2006-06-11
3) By o/p I meant **output** .. sorry for the mixup

we need to see your route table, so open a terminal and type
```

route -n

```

My route table looks like this

```
juby@fiero:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
```

There must be a line similar to this in your route table.
```
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
```

Ur /etc/hosts file looks bit concerning to me it shows only loopbac addresses 127.0.0.1 - 127.255.255.255 are reserved for this purpose afaik.

Mine looks something like this

```
127.0.0.1       localhost
**192.168.1.2     fiero**

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```


Here **192.168.1.2     fiero** is the static IP i'm using 

So can u try adding ur static IP to the /etc/hosts file in the same format ?


My routers IP is 192.168.1.1

U can try to add  the router to ur default route table using the command

```
route add -n gw XXX.XXX.X.X 
```
(replace Xs with actual ip of ur router)


Coming to the IPV6 problem, can u plz post the output of 

```
 less /etc/modprobe.d/aliases
```


The unknown 6 villains are the entries in ur /etc/hosts file I guess
```

::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

U can comment them off safely 

EDIT
Also I'd like to know the IP add of your router and static IP of ur machine, just curious bcoz of the hosts file :) 


Plz try these and getback to us.

---

### Post by tjay on 2006-06-14
Hi :) My monitor broke and now I can't use my Ubuntu pc. I'll be able to get a monitor next week, I hope. Will post again when I have the monitor. Thanks again ;)

---

### Post by teaker1s on 2006-06-15
any suggestions I have a ubuntu dapper that works perfectly and another computer with same router and settings that can use firefox but not synaptic /apt-get as it can't download repositories that work fine on one computer. tried ipv6 no difference. other than  re-installing networking any ideas

---

