---
title: "openssl wont install!"
date: 2011-11-29
forum: General Help
---

### Post by bignixs on 2011-11-29
I uninstalled openssl and when I tried to re-install I got this:

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
  ca-certificates
The following NEW packages will be installed:
  openssl
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 510 kB of archives.
After this operation, 1,040 kB of additional disk space will be used.
Err http://us.archive.ubuntu.com/ubuntu/ oneiric/main openssl i386 1.0.0e-2ubuntu4
  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_1.0.0e-2ubuntu4_i386.deb  Temporary failure resolving 'us.archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

What is wrong?

---

### Post by jonobr on 2011-11-29
The thing seems to show a dns resolution failure
Can you ping 

us.archive.ubuntu.com 

and 

91.189.92.183

Are you having intermittent dns issues?

---

### Post by bignixs on 2011-11-29
> **jonobr said:**
> The thing seems to show a dns resolution failure
Can you ping 

us.archive.ubuntu.com 

and 

91.189.92.183

Are you having intermittent dns issues?


Ok I pinged 91.189.92.183 and got:


--- 91.189.92.183 ping statistics ---
101 packets transmitted, 101 received, 0% packet loss, time 100133ms
rtt min/avg/max/mdev = 157.521/164.397/175.627/3.830 ms


and us.archive.ubuntu.com :

ping: unknown host us.archive.ubuntu.com


> Are you having intermittent dns issues?Not sure

---

### Post by jonobr on 2011-11-29
You have a dns issue somewhere

What happens when you type 

```
nslookup us.archive.ubuntu.com
```

Can you get to other websites ok?

Again, if your urgently needing to get that package (and your happy about doing this)
you can modify your host file to have an entry for
us.archive.ubuntu.com so it will get around the DNS issue.

Always be very careful modifying the host file and again, this would be a temporary stop gap measure

---

### Post by bignixs on 2011-11-29
> **jonobr said:**
> You have a dns issue somewhere

What happens when you type 

```
nslookup us.archive.ubuntu.com
```Can you get to other websites ok?

Again, if your urgently needing to get that package (and your happy about doing this)
you can modify your host file to have an entry for
us.archive.ubuntu.com so it will get around the DNS issue.

Always be very careful modifying the host file and again, this would be a temporary stop gap measure

do you thin I have an error in host file?

nslookup us.archive.ubuntu.com
;; connection timed out; no servers could be reached

---

### Post by jonobr on 2011-11-29
No, Im sure your hosts file is fine.

What I believe is happening is that , from your logs when you go to install openssl
it tries to get the package from us.archive.ubuntu.com 

It goes to your dns server to find out what the IP address is for us.archive.ubuntu.com 

From your logs.........
> Failed to fetch ........... Temporary failure resolving 'us.archive.ubuntu.com'

So, when you ping us.archive.ubuntu.com directly it does the same thing, it goes to DNS for an IP for us.archive.ubuntu.com
in that case its failing also, pointing to issues with resolution.

If you go directly to us.archive.ubuntu.com by pinging its IP address it works, confirming its a DNS resolution issue.

if you can ping google.com or pingplotter.com etc, then your issue is with getting resolution for that one particular site.

If you cant ping google.com or pingplotter.com then you have a resolution issue which is affecting your machine and could be misconfiguration in /etc/resolv.conf

The mention of the hosts file was to give a workaround if you needed SSL working immediately,
not an indication of problems with your file

---

### Post by bignixs on 2011-11-29
> **jonobr said:**
> No, Im sure your hosts file is fine.

What I believe is happening is that , from your logs when you go to install openssl
it tries to get the package from us.archive.ubuntu.com 

It goes to your dns server to find out what the IP address is for us.archive.ubuntu.com 

From your logs.........


So, when you ping us.archive.ubuntu.com directly it does the same thing, it goes to DNS for an IP for us.archive.ubuntu.com
in that case its failing also, pointing to issues with resolution.

If you go directly to us.archive.ubuntu.com by pinging its IP address it works, confirming its a DNS resolution issue.

if you can ping google.com or pingplotter.com etc, then your issue is with getting resolution for that one particular site.

If you cant ping google.com or pingplotter.com then you have a resolution issue which is affecting your machine and could be misconfiguration in /etc/resolv.conf

The mention of the hosts file was to give a workaround if you needed SSL working immediately,
not an indication of problems with your file

my resolv.conf is as follows:

```
search 5-on-it.com.
nameserver 192.168.1.110
```

changed th my static ip which is [http://96.41.82.107/](http://96.41.82.107/) and it installed correctly

---

### Post by bignixs on 2011-11-29
Thanks a lot for the help! it seems to be fixed now but can you help me with this error?

I run this command:

```
sudo openssl genrsa -des3 -out www.5-on-it.com.key 2048
```
I get:

```
3074762904:error:0E065068:configuration file routines:STR_COPY:variable has no value:conf_def.c:618:line 220
```

---

### Post by jonobr on 2011-11-29
Nope

That aint my wheelhouse ,
I can only guess that line 220 of your openssl,cnf file needs to be looked at to figure whats up

But again, outside my area.

Cheers

Jonobr

---

