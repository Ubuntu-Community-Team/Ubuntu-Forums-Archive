---
title: "Squid not starting at boot"
date: 2011-02-18
forum: General Help
---

### Post by PANNY on 2011-02-18
I seem to have a strange issue with squid which does not start at boot. I checked if it is set up correctly (using rcconf) and it shows that squid should be OK. Also if I start squid manually it works, so I don't think there is an error. I am using Ubuntu 10.04 with squid 2.7 (notice that I am not using squid3). It used to work but I think and update or something messed it up. Any hints?

---

### Post by PANNY on 2011-02-26
bump

---

### Post by RyanGT on 2011-04-06
I have the same problem.  It seems like it ought to be simple, but it isn't.  All I want is squid to automatically start at boot or login or whatever.

Bump.

---

### Post by linuxyogi on 2011-05-28
I am writing a song about this  :

Bump Bump .....Squid wont start Bump  Bump......Super bump.

Same here.

---

### Post by linuxyogi on 2011-05-28
**_Solution:_**

```
gksu gedit /etc/rc.local
```add the following line :

**/etc/init.d/squid start**

Save the file ......Reboot ....Done !!!

Then mark this thread as solved.

---

### Post by daxumaming on 2011-06-01
It wouldn't work on Maverick, Natty, and future releases. The devs has abandoned the SysV init script approach. 

The script you're looking for is now on /etc/init/squid.conf, so you can add that to /etc/rc.local

or, use the correct method

**replace**

```
start on (local-filesystems
          and net-device-up IFACE!=lo)
stop on runlevel[!2345]
```

**with**

```
start on (net-device-up
          and local-filesystems
          and runlevel [2345])
stop on runlevel [016]
```

---

### Post by lance bermudez on 2012-05-19
using Ubuntu 12.04 LTS precise having same problem on my laptp. Squid3 does not start up after restart of computer I have to do "sudo service squid3 start" then things work fine. How do I fix this?

---

### Post by PhobosK on 2012-09-17
> **lance bermudez said:**
> using Ubuntu 12.04 LTS precise having same problem on my laptp. Squid3 does not start up after restart of computer I have to do "sudo service squid3 start" then things work fine. How do I fix this?

Use what ***@daxumaming*** proposes, but with a small change.

Do not alter the /etc/init/squid3.conf file.

Just create the file: **/etc/init/squid3.override**
And put inside it this:

```

start on (net-device-up IFACE!=lo
          and local-filesystems
          and runlevel [2345])
stop on runlevel [016]

```

---

