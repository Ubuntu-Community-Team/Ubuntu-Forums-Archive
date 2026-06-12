---
title: "how to  file a possible bug report in kernel"
date: 2006-06-30
forum: General Help
---

### Post by lex1 on 2006-06-30
I have installed inn2 (news server) and get the error:

rw-r--r-- 1 news news 82 2006-06-29 10:51 /var/log/news/news.crit
-----
Server running
Allowing remote connections
Parameters c 10 i 50 (0) l 1000000 o 1011 t 300 H 2 T 60 X 0 normal specified
Not reserved
Readers follow enabled
Perl filtering enabled
-----
Jun 29 10:51:23 xstation innd: SERVER cant listen RCreader Address already in use



THE last line is the important one
and here in another lanuage there are bug reports which i do not understand
but can see it relates to the same kernel as dapper

[http://bugzilla.conectiva.com.br/show_bug.cgi?id=12476](http://bugzilla.conectiva.com.br/show_bug.cgi?id=12476)
[http://bugzilla.conectiva.com.br/long_list.cgi?buglist=10730](http://bugzilla.conectiva.com.br/long_list.cgi?buglist=10730)

any feedback would be helpful

lex1

"

---

### Post by Rui Pais on 2006-06-30
Oh well, hi again lex1 ;)

To report a bug, do it at [Launchpad]("https://launchpad.net/distros/ubuntu"), You will need to register.

Your links point to connectiva bugzilla but they are old, 2004 and 2005, they do not refer to the same kernel as dapper (that have Ubuntu only patchs) not even to kernel version. They refer to olds 2.6.3 and 2.6.4 kernels.

Anyway both reports refer the problem as conflicts with IPV6 and as solution/workaround deactivate it. 
Maybe it deserves a try.

Good luck.

---

### Post by lex1 on 2006-06-30
Since its not in english then it might be difficult 
whAT does workaround say?

yes it seems IPV6 related as i have  other running on tcp6

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 *:smtp                  *:*                     LISTEN     
tcp6       0      0 *:ssh                   *:*                     LISTEN     
tcp6       0      0 *:nntp                  *:*                     LISTEN     
tcp6       0      0 *:smtp                  *:*                     LISTEN  

I did a google search for
innd: SERVER cant listen RCreader Address already in use


lex1

---

### Post by Rui Pais on 2006-06-30
[QUOTE=lex1]Since its not in english then it might be difficult [/QUOTE]
Sorry, what is not in english? (Launchpad? if so, thats the official, plain english, bug report utility for ubuntu)

> whAT does workaround say?
They only mention disable ipv6 (if you don't know how to do it, [check here]("http://ubuntuforums.org/showthread.php?t=202838&highlight=ipv6+disable")) 
> yes it seems IPV6 related as i have  other running on tcp6

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 *:smtp                  *:*                     LISTEN     
tcp6       0      0 *:ssh                   *:*                     LISTEN     
tcp6       0      0 *:nntp                  *:*                     LISTEN     
tcp6       0      0 *:smtp                  *:*                     LISTEN  


portuguese is easy then network jargon ;)

---

### Post by lex1 on 2006-06-30
OK thanks for link to disable IPV6

how will this effect others programs running under IPV6

AM i getting mixed up with tcp6 and IPV6/ (see last post of netstat -tld output

but just wait read this carefully it may provide the answer?
[http://www.faqs.org/faqs/inn-faq/part3/](http://www.faqs.org/faqs/inn-faq/part3/)
Subject: (3.3) syslog message: inndstart: inndstart cant bind Address already in use
only problem is that /etc/inetd.conf  is empty


oh but my question was 
nnd: SERVER cant listen RCreader Address already in use

listen is the word not bind?

Lex1

ps OH yes you are from Portugal?

---

### Post by Rui Pais on 2006-06-30
hi,
yes i'm portuguese and thats one of the reasons i answer your thread, i could easily read those reports... unluckly i know only very little abot network related servers :( (The other reason was point to Launchpad, it's important do bug reports!)

As far as i know, for a desktop box ipv6 are almost unusefull and sometimes it's even better to disable it, since it could slow down some internet connections (one of the things that the bug reports mention is that distro had ipv6 disabled by default). But since you have an news server, and a mail server too if i understand well, running maybe its needed... I don't think so, but not sure... anyway it's easy to turn it off and if anything fails enable it again.

Anyway, the link you post seems to give a good clue (Subject 3.3). 
Check that (the file /etc/inetd.conf) first. 

You can always wait and see if someone with better knowlege can give you more enlightenned tips.

Good luck.

---

### Post by lex1 on 2006-07-01
t seems from this thread I must disable IVP6



I can disable but if i am runig a mail server
gives this(below) then would that be a wise move?

here is result of disablng IPV6
ul 1 11:51:33 xstation postfix/postdrop[4443]: warning: inet_protocols: IPv6 support is disabled: Address family not supported by protocol
Jul 1 11:51:33 xstation postfix/postdrop[4443]: warning: inet_protocols: configuring for IPv4 support only
Jul  1 12:11:26 xstation postfix/proxymap[4912]: warning: inet_protocols: IPv6 support is disabled: Address family not supported by protocol
Jul  1 12:11:26 xstation postfix/proxymap[4912]: warning: inet_protocols: configuring for IPv4 support only
Jul  1 12:11:26 xstation postfix/tlsmgr[4915]: warning: inet_protocols: IPv6 support is disabled: Address family not supported by protocol
Jul  1 12:11:26 xstation postfix/tlsmgr[4915]: warning: inet_protocols: configuring for IPv4 support only
Jul  1 12:27:14 xstation postfix/anvil[5483]: warning: inet_protocols: IPv6 support is disabled: Address family not supported by protocol
Jul  1 12:27:14 xstation postfix/anvil[5483]: warning: inet_protocols: configuring for IPv4 support only
Jul  1 12:27:14 xstation postfix/trivial-rewrite[5486]: warning: inet_protocols: IPv6 support is disabled: Address family not supported by protocol
Jul  1 12:27:14 xstation postfix/trivial-rewrite[5486]: warning: inet_protocols: configuring for IPv4 support only

and

where as before netstat -tld gave smpt fot tcp and tcp6 now its only for tcp

The POSITIVE side is that the error message has stopped which I posted in post no1!


lex1

---

