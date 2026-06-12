---
title: "hosts.allow - probably everyone except me knows this"
date: 2012-03-03
forum: General Help
---

### Post by DebN on 2012-03-03
I am trying to edit the hosts.allow/deny files so everyone from LAN can access everything on the ubuntu server, but only a small group called mygroup can access SSHD (only) from outside through my router. Following line in hosts.deny seems to be doing its part of the job-
ALL: ALL EXCEPT 192.168.0.

But what is the correct entry for hosts.allow so the mygroup members can enter through the router for SSHD ? I have tried the following- 
SSHD: @mygroup

Thanks so much in advance.

---

### Post by efflandt on 2012-03-03
Unless you are actually running something called **SSHD**, you might try **sshd** instead (the actual name of the daemon or service).  Unlike Windows, Linux is case sensitive about many things.

see **man hosts_access**

> In  the  following text, daemon is the process name of a network daemon process, and client is the name and/or address  of  a  host  requesting service.  Network  daemon process names are specified in the inetd configuration file.

Note that some services launched by inetd instead of running constantly as a daemon may have a "in." prefix, but I do not seem to have any /etc/inetd.conf.

---

### Post by DebN on 2012-03-03
Thank you efflandt. I checked and yes, it should be sshd and not SSHD. I corrected that but I think I need to allow something more than sshd. I get no login prompt for outside connections when ALL is blocked in hosts.deny file.

---

### Post by Khayyam on 2012-03-03
> **DebN said:**
> [...] I think I need to allow something more than sshd. I get no login prompt for outside connections when ALL is blocked in hosts.deny file.

Because you are blocking everything but "192.168.0." ... anyhow, you can't block by group using tcpwrappers, its host/service based, not UID/GID. You can allow/disallow users/groups via /etc/ssh/sshd_config however. An example:

```
DenyUsers root
AllowUsers bob john jane
AllowGroups group1 group2
```
HTH ... khay

---

### Post by DebN on 2012-03-03
Khay, Thank you so much for your reply. I agreed with you even before I read your reply. 

I am looking for a way to allow everything for everyone on the LAN, but only allow ssh to a small group coming through WAN.

As you can see, with my insufficient knowledge, it is a bit hard.

---

### Post by Khayyam on 2012-03-03
> **DebN said:**
> Khay, Thank you so much for your reply. I agreed with you even before I read your reply.

In which case you read my mind you fiend! ... hehe ... in any case your welcome. 

> **DebN said:**
> I am looking for a way to allow everything for everyone on the LAN, but only allow ssh to a small group coming through WAN.

OK, then you allow 'sshd 192.168.0, .domain1.tld, domain2.tld, domain3.tld' and deny 'ALL: ALL'. It depends on how fine grain you want it, you can allow IP, or host.domain.tld.

Basically, with deny 'ALL: ALL' nothing gets through except whats defined in hosts.allow.

Perhaps a better method would be to disable password logins and have your users use 'key' authentication.

> **DebN said:**
> As you can see, with my insufficient knowledge, it is a bit hard.

Hey, fake it! ... at least until you know better :)
 
best ... khay

---

