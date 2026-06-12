---
title: "/etc/hosts not resolving on different subnet"
date: 2010-04-05
forum: General Help
---

### Post by hipster on 2010-04-05
--removed duplicate posting--

---

### Post by hipster on 2010-04-05
hi there.  i've posted this in the server section as well, but in retrospect it may be more applicable to just general help. 

i'm syslogging a bunch of routers to this particular server, and in order to get the rsyslog entries to show up with the proper hostname, instead of IP, _without_ enabling rsyslog DNS, i am dumping the hosts into /etc/hosts.

the problem is - the only one that resolves is EDTN-LAB-CR03. the commonality? - CR03 and this server are both in 172.25.130.0/24, whereas the other routers are in 250.0/24. this particular server is at 172.25.130.9.

i have googled my face off to figure this one out... no luck so far. any tips on where to look?

/etc/hosts
172.25.250.2 EDTN-LAB-MA01
172.25.250.3 EDTN-LAB-MA02
172.25.130.197 EDTN-LAB-CR03 ##<------works!
172.25.250.4 EDTN-LAB-MR21
172.25.250.11 EDTN-LAB-MR22 ##<------doesn't work!
172.25.250.6 EDTN-LAB-MR23

rsyslog bad:
Apr 5 12:53:19 172.25.250.11 138 Base ISIS-WARNING-vRtrIsisAdjacencyChange-2017 [Adjacency state change]: Adjacency status changed to up for interface

rsyslog good:
Apr 5 12:53:14 edtn-lab-cr03 1256 Apr 5 12:53:19: %LINK-SP-3-UPDOWN: Interface Port-channel10, changed state to up

i know for sure that rsyslog is reading /etc/hosts (probably based on /etc/nsswitch.conf). if i modify the 172.25.130.197 entry in /etc/hosts to "hello_world", it will certainly show up in my log file with that hostname.  modifying any of the other entries results in absolutely no success.

i've also looked at /etc/host.conf and 'order hosts,bind' is in place. 

any tips from the fine folks here at ubuntuforums.org? much appreciated!

-ryanL

---

### Post by Iowan on 2010-04-05
Threads merged. Whichever forum you prefer (but not  both) :P

---

### Post by gordintoronto on 2010-04-05
> **hipster said:**
> hi there, first post so pls be gentle :)

i'm syslogging a bunch of routers to this particular server, and in order to get the rsyslog entries to show up with the proper hostname...


Your first post is supposed to be something like, "where is the off button." [smile]

I know a fair bit, and I've set up servers, but I didn't understand anything in the second sentence I quoted. It certainly isn't a "general help" question.

---

### Post by redmk2 on 2010-04-06
> **hipster said:**
> hi there, first post so pls be gentle :)


Meh!  You makes your complicated post and you takes your chances. :D

To be frank, this kind of question is not *general *in any way you want to look at it.  Most of the time it will just sit here, dry out and blow away.  But...

> 

i'm syslogging a bunch of routers to this particular server, and in order to get the rsyslog entries to show up with the proper hostname instead of IP _without_ enabling rsyslog DNS, i am dumping the hosts into /etc/hosts.

the problem is - the only one that resolves is EDTN-LAB-CR03.  the commonality - CR03 and this server are both in 172.25.130.0/24, whereas the other routers are in 250.0/24.  server is 172.25.130.9.

Well,  maybe...

How about: All the others have the first 10 characters that are the same.  The only unique one is the one that resolves.  I've delt with plenty of routines that only parse the first 8 or so char's.

I would try renaming one of the [FONT="Courier New"]EDTN-LAB-M..[/FONT] hosts to, um...*myrouter* and see what happens.
> 

i have googled my face off to figure this one out... no luck so far.  any tips on where to look?

/etc/hosts
172.25.250.2    EDTN-LAB-MA01
172.25.250.3    EDTN-LAB-MA02
172.25.130.197  EDTN-LAB-CR03  ##<------works!
172.25.250.4    EDTN-LAB-MR21
172.25.250.11    EDTN-LAB-MR22 ##<------doesn't work!
172.25.250.6    EDTN-LAB-MR23

rsyslog bad:
Apr  5 12:53:19 172.25.250.11 138 Base ISIS-WARNING-vRtrIsisAdjacencyChange-2017 [Adjacency state change]:  Adjacency status changed to up for interface

rsyslog good:
Apr  5 12:53:14 edtn-lab-cr03 1256 Apr  5 12:53:19: %LINK-SP-3-UPDOWN: Interface Port-channel10, changed state to up

i know for sure that rsyslog is reading /etc/hosts (probably based on /etc/nsswitch.conf).  if i modify the 172.25.130.197 to "hello_world", it will certainly show up in my log file with that hostname.

any tips from the fine folks here at ubuntuforums.org?  much appreciated!

-ryan

What do the folks at Cisco say?

---

### Post by hipster on 2010-04-06
hi guys.  thanks for replying!  apologies if i've buggered this up and put it in the wrong location, but i do appreciate the replies nonetheless.

it isn't specific to cisco devices at all.  and as i indicated in my OP, i can rename the *working* router that is on the local subnet to "hello_world" and "hello_world" indeed shows up in the log file.  renaming any of the non-130.0/24 host entries does not give the desired results.

this is entirely different than "logging origin-id hostname" that you might be thinking of in cisco IOS.

cheers

-ryan

---

### Post by hipster on 2010-04-07
no ideas from anyone hmm?  does anyone think this is worth filing a bug?  i've tried as much as i'm capable of doing, and it isn't an issue on my solaris box.

---

### Post by dcstar on 2010-04-07
> **hipster said:**
> no ideas from anyone hmm?  does anyone think this is worth filing a bug?  i've tried as much as i'm capable of doing, and it isn't an issue on my solaris box.

You should ping each name and see if it resolves, if it does then maybe syslog is the problem.

---

### Post by hipster on 2010-04-08
> **dcstar said:**
> You should ping each name and see if it resolves, if it does then maybe syslog is the problem.

yeah i believe i've further isolated it to rsyslog as the problem.  other services on this box are reading /etc/hosts properly, but only rsyslog is resolving for the host on the same subnet.  very interesting/annoying.

---

### Post by dcstar on 2010-04-09
> **hipster said:**
> yeah i believe i've further isolated it to rsyslog as the problem.  other services on this box are reading /etc/hosts properly, but only rsyslog is resolving for the host on the same subnet.  very interesting/annoying.

Make the DNS name lengths shorter (<8 chars) and see what happens.

---

### Post by dcstar on 2010-04-09
> **hipster said:**
> yeah i believe i've further isolated it to rsyslog as the problem.  other services on this box are reading /etc/hosts properly, but only rsyslog is resolving for the host on the same subnet.  very interesting/annoying.

Have a look at this:

[http://www.gossamer-threads.com/lists/rsyslog/users/3487](http://www.gossamer-threads.com/lists/rsyslog/users/3487)

---

