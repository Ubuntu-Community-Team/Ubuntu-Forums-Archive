---
title: "what is &quot;twistd&quot; and why is it listening when I use lsof?"
date: 2011-07-09
forum: General Help
---

### Post by nrundy on 2011-07-09
I ran lsof -i -n -P and got this in one of the results:

twistd   1201 root    4u  IPv4   6041      0t0  TCP *:8080 (LISTEN)

What does the * mean in "*:8080"
What is "twistd"--can you explain how you found what twistd is if you looked it up somehow, cause my google searches have not been fruitful

thanks

---

### Post by matt_symes on 2011-07-09
Hi

From 

> [http://twistedmatrix.com/trac/wiki](http://twistedmatrix.com/trac/wiki)

> 
 Twisted is a networking engine written in Python, supporting numerous  protocols.  It contains a web server, numerous chat clients, chat  servers, mail servers, and more. 
  Twisted is made up of a number of sub-projects which can be accessed individually through the [twisted projects index]("http://twistedmatrix.com/trac/wiki/TwistedProjects"). 
 

Check out ```
man twistd
```

That was my starting point.

Kind regards

---

### Post by nrundy on 2011-07-09
what does the  *  mean in the lsof output?

Do you know how I can learn what app or process started the twistd?

---

### Post by Habitual on 2011-07-09
Here's a few tricks you can use:
```

lsof -i :port

lsof -i :80

firefox 4702   JJ   48u  IPv4 596982      0t0  TCP 192.168.1.246:48285->a96-7-46-73.deploy.akamaitechnologies.com:http (ESTABLISHED)
firefox 4702   JJ   55u  IPv4 596976      0t0  TCP 192.168.1.246:33712->a96-7-46-107.deploy.akamaitechnologies.com:http (ESTABLISHED)
firefox 4702   JJ   64u  IPv4 596990      0t0  TCP 192.168.1.246:48292->a96-7-46-73.deploy.akamaitechnologies.com:http (ESTABLISHED)

lsof -i :service

lsof -i :http

firefox 4702   JJ   48u  IPv4 596982      0t0  TCP 192.168.1.246:48285->a96-7-46-73.deploy.akamaitechnologies.com:http (ESTABLISHED)
firefox 4702   JJ   55u  IPv4 596976      0t0  TCP 192.168.1.246:33712->a96-7-46-107.deploy.akamaitechnologies.com:http (ESTABLISHED)
firefox 4702   JJ   64u  IPv4 596990      0t0  TCP 192.168.1.246:48292->a96-7-46-73.deploy.akamaitechnologies.com:http (ESTABLISHED)

lsof -i @remote_host

lsof -i@a96-7-46-73.deploy.akamaitechnologies.com

lsof -p <PID>

lsof +D /home/user/public_html

to "see" everything running out of /home/user/public_html

lsof -u nobody,nobody

lsof -Pni

lsof -i :3000-4000
lsof -r 2 -p <pid> -a -i TCP

Exclude root-owned processes:
lsof -u ^root

lsof -c <process name>
lsof -c exim

lsof -Pan -i tcp -i udp

lsof -u someuser -a +D /etc

```

---

