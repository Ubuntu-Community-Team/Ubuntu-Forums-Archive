---
title: "Server 11.04, CUPS unable to bind socket"
date: 2011-10-22
forum: General Help
---

### Post by crasher35 on 2011-10-22
Hello again. I am having a lot of issues with my Ubuntu Server. I feel like it would be best to write them as different threads since they don't seem to be related issues.

The issue for this thread is that I am having a problem with CUPS 1.4.6. It had been working just fine with my HP Deskjet 2050 j510 all-in-one then, about a week ago, it stopped printing.

When I log in to CUPS' web interface and view the error log, I find this error every time I start/restart CUPS.

> E [22/Oct/2011:11:20:20 -0400] Unable to bind socket for address 0.0.0.0:631 - Address already in use.

So I ran lsof -i :631 to see if anything else is using the port, and I see that CUPS is the only thing running on that port.
> cupsd   1556 root    5u  IPv6  10054      0t0  TCP ip6-localhost:ipp (LISTEN)
cupsd   1556 root    6u  IPv4  10055      0t0  TCP localhost:ipp (LISTEN)
cupsd   1556 root    8u  IPv4  10058      0t0  TCP crashserv.local:ipp (LISTEN)
cupsd   1556 root    9u  IPv4  10059      0t0  TCP crashserv.cfl.rr.com:ipp (LISTEN)
cupsd   1556 root   10u  IPv4  10062      0t0  UDP *:ipp


I'm out of ideas here. Any time I send a document to print from any of my other PCs (Windows 7 and Windows XP) it gets stuck at the Windows print queue. It was working fine before and then one day it just stopped working. The Sane scan server, however, continues to work fine so I know it's not a problem with the printer itself...

Any help would be greatly appreciated.

---

### Post by petersk on 2011-10-24
I'm having a similar problem, so I'd like to know how you get it solved if you solve it outside this forum.

---

