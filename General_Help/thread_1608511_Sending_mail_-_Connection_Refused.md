---
title: "Sending mail - Connection Refused"
date: 2010-10-29
forum: General Help
---

### Post by Alex53 on 2010-10-29
I am trying to get an Ubuntu web server to send mail to users in my local network

Everything is Windows except the web servers. The mail server is exchange, and the DNS, domain controllers, etc. are also Windows.

I am using Postfix, and when I try to send mail I get;

Oct 29 12:13:05 juliet postfix/smtp[28456]: connect to mydomain.com[192.168.1.1]:25: Connection refused
Oct 29 12:13:05 juliet postfix/smtp[28456]: connect to mydomain.com[192.168.1.2]:25: Connection refused

192.168.1.1 and 192.168.1.2 are the DNS servers, not the mail server, which I find a bit puzzling. Why would the DNS servers listen on port 25? i.e. they don't, so the connection is refused. 

Why is Postfix trying to send mail to the DNS servers rather than the mail server ?

---

### Post by Grenage on 2010-10-29
Do you have an internal MX record for the domain, so it knows where to route mail?

---

### Post by Alex53 on 2010-10-29
Thanks for your reply. 

I didn't before today, but I added it before installing Postfix.

The thing is the error above reads to me as if Postfix was trying to connect to port 25 of a DNS server, which doesn't make sense.

---

### Post by Grenage on 2010-10-29
It's possible that the postfix information is just misleading; I'm sure someone else will chime in, if so.

From the postfix server, can you telnet to the mail server, on port 25?  If so, we  can assume that it's an odd message syntax, or it's trying to connect to the DNS server.

Double-check the lookup using *nslookup*.  First enter that command in a terminal, then set the query type, then enter your e-mail domain:

```
nslookup
```

```
set q=mx
```

```
mydomain.com
```

---

### Post by Alex53 on 2010-10-29
Yeah something wrong here obviously;

with telnet;
```

telnet: could not resolve mailserver.mydomain.com/[25]: Servname not supported for ai_socktype
```

with nslookup;
```

> mydomain.com
Server:		192.168.1.2
Address:	192.168.1.2#53

*** Can't find mydomain.com: No answer

```

192.168.1.2 being a DNS server

I dont understand, I can ping the mail server, and from a windows PC I can telnet it and I get a proper reply on port 25.

---

### Post by Grenage on 2010-10-29
Well that's *kind* of good news; at we know it's probably a network config issue, and not some glitchy problem.

I'm assuming you can resolve other machine names when using ping.  Does the file /etc/services exist on your server?

---

### Post by Alex53 on 2010-10-29
Yup, it pings the hostnames of all the other machines just fine.

As for the /etc/services file, yes, there is one, with a long list of services and their port, protocol, etc.

---

### Post by Alex53 on 2010-10-29
Bah, I take a lot of the above back. 

I was typing telnet mailserver [25], with the square brackets. 

If I type it properly, I get a reply from the mail server, but the logs still show the 'connection refused' line I posted.

---

### Post by Grenage on 2010-10-29
Hmm, out of curiosity, is smtp in there?

---

### Post by Alex53 on 2010-10-29
Yup it is.

---

### Post by Grenage on 2010-10-29
Do you get a connection refused from the telnet session when you connect, or does it allow you to *HELO*, etc?

---

### Post by dcstar on 2010-10-29
> **Alex53 said:**
> Bah, I take a lot of the above back. 

I was typing telnet mailserver [25], with the square brackets. 

If I type it properly, I get a reply from the mail server, but the logs still show the 'connection refused' line I posted.

The log you have posted clearly shows that there is no connection attempt being made to "mailserver", only attempts to connect to other names.

If you have other logs that show differently, then post them.

---

### Post by Alex53 on 2010-10-30
> **Grenage said:**
> Do you get a connection refused from the telnet session when you connect, or does it allow you to *HELO*, etc?

No. The telnet connection works fine.

---

### Post by Alex53 on 2010-10-30
> **dcstar said:**
> The log you have posted clearly shows that there is no connection attempt being made to "mailserver", only attempts to connect to other names.

If you have other logs that show differently, then post them.

Well that is precisely my problem. If that is the case, why is postfix trying to send e-mail to my DNS servers? 

The DNS servers have MX records pointing to the mail server and the only place the DNS servers are mentioned in my ubuntu web server is the network settings.

---

