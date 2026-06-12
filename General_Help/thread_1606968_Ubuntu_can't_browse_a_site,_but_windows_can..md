---
title: "Ubuntu can't browse a site, but windows can."
date: 2010-10-27
forum: General Help
---

### Post by muze4life on 2010-10-27
Hi,
Please see screenshot,
I tried browsing bloomberg.com from Ubuntu - no luck - all browsers fail saying it's some network problem or so,
but when I launched windowsXP from VirtualBox from inside Ubuntu (Maverick x64) - no problem viewing this site.
Anyone any idea what could be wrong?

ps. with other sites so far no issues.

---

### Post by Verbeck on 2010-10-27
Strange.. i can see it

---

### Post by muze4life on 2010-10-27
No issues with other sites... I thought maybe it's some type of IPv4 vs 6 stuff..

---

### Post by cogier on 2010-10-27
I have tried it with Firefox, Opera and Chrome all with no problem.

---

### Post by yetiman64 on 2010-10-27
Hi muze4life, I just loaded that page here without a problem with firefox on 10.04.

I then pinged the site [www.bloomberg.com]("http://www.bloomberg.com") and got an IP of 173.223.232.144.

Could you run in a terminal,
```
ping -c 5 www.bloomberg.com
```and compare the IP address to rule out a DNS issue, though it puzzles me as to why Windows in a Virtual machine would connect if it was.
It sounds as though your ISP may have an out of date DNS cache if only 1 site is affected though, worth a check.

---

### Post by muze4life on 2010-10-27
Thanks, I ran your command (from Ubuntu obviously) and it says:
ping: unknown host [www.bloomberg.com]("http://www.bloomberg.com")

Do you know what to do about it?

---

### Post by yetiman64 on 2010-10-27
Rather than use my ISPs DNS, I use openDNS.com their servers IP addresses are 208.67.222.222 and 208.67.220.220.

I'm not actually sure how to change that from the local machine as I program those IP addresses in my router and any install I have automatically picks them up. Someone else may have more specific information on how to do it in the version you are running locally.

Try doing the same command on say [www.google.com]("http://www.google.com") and if you get an IP back it sounds very much like a DNS issue.

---

### Post by muze4life on 2010-10-27
Thanks, I'll do a clean install of Ubuntu on another partition and see if problem solved. As to pinging google.com I get some funny results (a funny "ey-in-f147.1e100.net"):

> 
ping -c 5 [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (74.125.79.147) 56(84) bytes of data.
64 bytes from ey-in-f147.1e100.net (74.125.79.147): icmp_req=1 ttl=54 time=252 ms
64 bytes from ey-in-f147.1e100.net (74.125.79.147): icmp_req=2 ttl=54 time=291 ms
64 bytes from ey-in-f147.1e100.net (74.125.79.147): icmp_req=3 ttl=54 time=210 ms
64 bytes from ey-in-f147.1e100.net (74.125.79.147): icmp_req=4 ttl=54 time=136 ms
64 bytes from ey-in-f147.1e100.net (74.125.79.147): icmp_req=5 ttl=54 time=117 ms

--- [www.l.google.com](www.l.google.com) ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 8557ms
rtt min/avg/max/mdev = 117.118/201.577/291.373/66.461 ms


---

### Post by yetiman64 on 2010-10-27
That is normal, the IP is consistent throughout your results, definitely looks like a DNS issue. 

A reinstall may not fix the problem though if it is a problem emanating from your ISP. 

However if you are operating through a modem/router look in its configuration pages to see if you can force the use of a particular DNS service as I have done and restart both the router and your current installation after any changes.

---

### Post by Verbeck on 2010-10-27
try flushing your dns

```
sudo apt-get install nscd 
sudo /etc/init.d/nscd restart
```

or restart netowrking
```

sudo /etc/init.d/networking restart

```

---

### Post by muze4life on 2010-10-27
Thanks all, unfortunately restarting the network/nscd didn't help,
I have Fedora 14 x64 installed on another partition so I tried browsing this site from it - and no issues - so it looks like some issue with Ubuntu, so I'll do the easiest thing people usually do when all bets are off - do a clean install :)

---

### Post by Tony Flury on 2010-10-27
Strange that is works from the Virtual box - i would not have thought that a virtual box install of Windows would go to a different DNS server - effectively proxied via the host system - assuming that the Virtual Box is set up to do NAT.

---

### Post by muze4life on 2010-10-27
Hmm... I just did a clean install (formatted the partition) with all updates and the issue is still there. Looks like it's some **obscure** bug in Ubuntu since (as I said earlier) I booted into Fedora and it had no issue browsing that site, not to mention window$.
Unfortunately I can't use Fedora cause on my system it has sound issues, nor window$ cause it's susceptible to viruses.

---

### Post by yetiman64 on 2010-10-27
Can you try something as a workaround (that is since only one site is affected), try add bloomberg.com to your hosts file.

```
gksudo gedit /etc/hosts
```and just below your local machines hostname add the line,
> 173.223.232.144    [www.bloomberg.com]("http://www.bloomberg.com")It should look something like (note this example is from 10.04),
> 127.0.0.1    localhost
127.0.1.1    x-xxxxx-xxxx
173.223.232.144    [www.bloomberg.com]("http://www.bloomberg.com")

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts Note x-xxxxx-xxxx is me censoring my hostname on this site only.

Then try to connect to the site again. Though like Tony Flury I'm wondering as to why it works in the VM but not the host.

Edit: note the format changes slightly when posted here, keep the layout the same as in the hosts file.

---

### Post by muze4life on 2010-10-27
Thanks, it helped, sort of, it loads the site but it looks crippled (see screenshot).

---

### Post by muze4life on 2010-10-27
There we go, I launched VirtualBox again and ran this time Ubuntu 10.04.1 and it works with that site, so it looks like this issue is related only to Ubuntu x64 10.10.
To make sure I'm correct I'll install 10.04.1 to a physical partition and see if it still works, if it does, I'll migrate back to Ubuntu 10.04.1, cause frankly saying I saw from time to time other (smaller) network glitches with 10.10 which might too be related.

---

### Post by linux-hack on 2010-10-27
In my opinion you should use the LTS for everyday use and the others in VMs this way you don't have this kind of problems ...

---

### Post by yetiman64 on 2010-10-27
> **muze4life said:**
> There we go, I launched VirtualBox again and ran this time Ubuntu 10.04.1 and it works with that site, so it looks like this issue is related only to Ubuntu x64 10.10.
To make sure I'm correct I'll install 10.04.1 to a physical partition and see if it still works, if it does, I'll migrate back to Ubuntu 10.04.1, cause frankly saying I saw from time to time other (smaller) network glitches with 10.10 which might too be related.

Yes sounds pretty right to me. I have 10.10., 10.04 and 9.04 in a parallel setup and am having all sorts of network problems in 10.10 to the point I now boot into 10.04 almost exclusively.

Can't use some of the network tools in 10.10 that work flawlessly in 10.04 (ping is one of them, that is why I got you to use the terminal earlier). They will hopefully improve over the next few months with updates etc. in 10.10 considering it is less than 1 month after release. Usually things really improve after 3 to 6 months from release date when the bugs get ironed out.

---

