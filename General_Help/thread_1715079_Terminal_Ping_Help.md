---
title: "Terminal Ping Help"
date: 2011-03-26
forum: General Help
---

### Post by 1chess2u Christian on 2011-03-26
When I try to ping with the terminal to check a website's availability, it always just keeps going on and on and on... How do I get it to stop after a set amount of pings? Is there some type of command? If there is, I would love to have that.

---

### Post by vivek.pandey on 2011-03-26
hi
perhaps you are looking for crtl + c

---

### Post by Lateralis on 2011-03-26
Ping is a useful programme with a variety of command line switches.  The manual pages ('man ping') will help.  

In your specific case, you can use the -c switch:

```

ping -c <# of pings> <website>

```

---

### Post by throese on 2011-03-26
There is a command that lets you set the number of times to ping a site before stopping:

```
ping -c [insert number of times to ping here] www.domainname.com
```

Where it says *[insert number of times to ping here]* put in any number from 1-100 and it'll ping the URL that many times. Domain name being the name of the site.

Example:

ping -c 5 [www.yahoo.com](www.yahoo.com) will ping Yahoo's website fives times before giving the final output.

```


ping -c 5 www.yahoo.com

PING any-fp.wa1.b.yahoo.com (98.137.149.56) 56(84) bytes of data.
64 bytes from ir1.fp.vip.sp2.yahoo.com (98.137.149.56): icmp_seq=1 ttl=50 time=1152 ms
64 bytes from ir1.fp.vip.sp2.yahoo.com (98.137.149.56): icmp_seq=2 ttl=50 time=1330 ms
64 bytes from ir1.fp.vip.sp2.yahoo.com (98.137.149.56): icmp_seq=3 ttl=50 time=1221 ms
64 bytes from ir1.fp.vip.sp2.yahoo.com (98.137.149.56): icmp_seq=4 ttl=50 time=642 ms
64 bytes from ir1.fp.vip.sp2.yahoo.com (98.137.149.56): icmp_seq=5 ttl=50 time=852 ms

--- any-fp.wa1.b.yahoo.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4016ms
rtt min/avg/max/mdev = 642.464/1040.168/1330.684/254.331 ms, pipe 2

```

---

### Post by 1chess2u Christian on 2011-03-26
Thank you all! are there any other useful commands that I should know about the Ping?

---

### Post by mendhak on 2011-03-26
It depends on what you want to do with it, but it does have other switches.  In terminal, type

ping --help

You can also type

man ping

The first one brings a short list of command line switches, the second one is the manual page for the ping command.

---

### Post by 1chess2u Christian on 2011-03-27
I know about the "--help" command, but I don't really know what the commands mean, or the units used (like with interval (-i) is that in milliseconds, or in seconds?) Thank you though. Does the "man" command bring up the manual for every program?

---

