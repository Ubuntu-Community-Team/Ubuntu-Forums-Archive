---
title: "dhclient messages"
date: 2011-10-25
forum: General Help
---

### Post by awacs on 2011-10-25
Lucid: I'm getting LOTS of dhclient messages, viz.:
Oct 25 18:08:20 pizza dhclient: DHCPREQUEST of 24.191.111.65 on eth0 to 10.240.162.77 port 67
Oct 25 18:09:22 pizza dhclient: last message repeated 4 times
Oct 25 18:10:25 pizza dhclient: last message repeated 5 times
Oct 25 18:11:33 pizza dhclient: last message repeated 4 times
Oct 25 18:12:34 pizza dhclient: last message repeated 5 times
Oct 25 18:13:35 pizza dhclient: last message repeated 4 times
Oct 25 18:14:35 pizza dhclient: last message repeated 4 times
Oct 25 18:15:35 pizza dhclient: last message repeated 5 times

etc., etc., connecting to cable. I'm not continually disconnecting (I should hope!) so, why the stream of dhcprequests?

And, how do I tell dhclient to not log the thousands of requests?

Thanks!

---

### Post by dcstar on 2011-10-26
> **awacs said:**
> Lucid: I'm getting LOTS of dhclient messages, viz.:
Oct 25 18:08:20 pizza dhclient: DHCPREQUEST of 24.191.111.65 on eth0 to 10.240.162.77 port 67
Oct 25 18:09:22 pizza dhclient: last message repeated 4 times
Oct 25 18:10:25 pizza dhclient: last message repeated 5 times
Oct 25 18:11:33 pizza dhclient: last message repeated 4 times
Oct 25 18:12:34 pizza dhclient: last message repeated 5 times
Oct 25 18:13:35 pizza dhclient: last message repeated 4 times
Oct 25 18:14:35 pizza dhclient: last message repeated 4 times
Oct 25 18:15:35 pizza dhclient: last message repeated 5 times

etc., etc., connecting to cable. I'm not continually disconnecting (I should hope!) so, why the stream of dhcprequests?

And, how do I tell dhclient to not log the thousands of requests?

Thanks!

[http://unix.derkeiler.com/Newsgroups/comp.unix.bsd.freebsd.misc/2003-09/1604.html](http://unix.derkeiler.com/Newsgroups/comp.unix.bsd.freebsd.misc/2003-09/1604.html)

---

### Post by awacs on 2011-10-26
Ah, thanks for that. Syslog is now 80% smaller. :-)

But what's causing the numerous messages in the first place? Surely optimum is not terminating my lease every few seconds, right?

---

### Post by dcstar on 2011-10-27
> **awacs said:**
> Ah, thanks for that. Syslog is now 80% smaller. :-)

But what's causing the numerous messages in the first place? Surely optimum is not terminating my lease every few seconds, right?

```
cat /var/lib/dhcp3/dhclient.eth***X***.leases
```

---

