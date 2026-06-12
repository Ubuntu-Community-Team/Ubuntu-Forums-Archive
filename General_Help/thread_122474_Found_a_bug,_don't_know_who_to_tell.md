---
title: "Found a bug, don't know who to tell"
date: 2006-01-27
forum: General Help
---

### Post by nikdc5 on 2006-01-27
Hi, I'm a complete newbie (gosh i hate that term) to linux, and have made extensive use of some of the posts on this forum, particularly ones relating to setting up wireless networking and support for mp3, mpeg etc, (so many thanks)... but I have found a (very) minor bug in the program and wasn't sure who to tell, so thought I would post it here.  This bug seems to be present in all distros of linux - I have had friends check other versions - so it is not only ubuntu, but the problem is as thus;

If a web address contains a dash as the last letter such as "http://thepost-.blogspot.com", linux will say that it cannot find the address.  This has happened to me in mozilla, firefox 1.0x, firefox 1.5, and Konquerer.  However, the address is valid, as it can be accessed in Windows (including using Mozilla and Firefox).  There doesn't seem to be any action i can take to remedy the situation.  Has anyone any ideas?  Adding "www" at the start has no effect (altho the site will still load fine with that prefix in Windows)

---

### Post by ]Nbx*cmD[ on 2006-01-28
Wow i can't believe!
I can't get there through Opera neither lynx and Ping can't resolve that address... are you sure it is correct?

---

### Post by engla on 2006-01-28
This was fun, and strange. I think it looks like you are right:

```
$ host thepost-.blogspot.com
thepost-.blogspot.com is an alias for blogspot.blogger.com.
blogspot.blogger.com has address 66.102.15.101
thepost-.blogspot.com is an alias for blogspot.blogger.com.
thepost-.blogspot.com is an alias for blogspot.blogger.com.
$ ping thepost-.blogspot.com
ping: unknown host thepost-.blogspot.com
$ ping 66.102.15.101
PING 66.102.15.101 (66.102.15.101) 56(84) bytes of data.
64 bytes from 66.102.15.101: icmp_seq=1 ttl=242 time=189 ms
64 bytes from 66.102.15.101: icmp_seq=2 ttl=242 time=188 ms
64 bytes from 66.102.15.101: icmp_seq=3 ttl=242 time=186 ms
64 bytes from 66.102.15.101: icmp_seq=4 ttl=242 time=186 ms

--- 66.102.15.101 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3002ms
rtt min/avg/max/mdev = 186.717/187.701/189.213/1.062 ms

```

---

### Post by steve.horsley on 2006-01-28
This is the place to report Ubunti bugs:
[https://wiki.ubuntu.com/ReportingBugs?action=show&redirect=BugReports](https://wiki.ubuntu.com/ReportingBugs?action=show&redirect=BugReports)

I can add some info:

Using Ethereal, I can see the DNS request goes out correctly, and is answered correctly (as far as I can see) by the DNS server (same address as in the posts above), so I think the problem is in  parsing the DNS response. Of course, it may be that the DNS response os malformed somehow.

If you add thepost-.blogspot.com to the /etc/hosts file, then you can ping it without problems, which narrows down the search for the problem code. It also provides a bit of a workround.

---

