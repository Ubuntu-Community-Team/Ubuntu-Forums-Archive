---
title: "Scripting timezone changing process"
date: 2010-03-25
forum: General Help
---

### Post by dheerajkabra on 2010-03-25
Hi,

I am new user and hence my 1st post. I have worked on redhat/fedora for last 5 yrs but now working on ubuntu as well. Need your help.

I have around 200 ubuntu VMs on which I have to change the timezone. I know I can do that using "dpkg-reconfigure tzdata", But doing it manually on 200 machines is not what I really want to do.

Hence I am looking for a way to script this process. On fedora, its simple, change the "ZONE" entry in "/etc/sysconfig/clock" and copy corresponding file from /user/share/zoneinfo to /etc/localtime. Hence I can script is easily.

But in ubuntu, with "dpkg-reconfigure tzdata", I don't know how to script it.
I am not aware of any other method.
please help to automate timezone change on ubuntu.

Many thanks.
-Dheeraj.

---

### Post by dheerajkabra on 2010-03-25
I think i Got it. i found a file /etc/timezone where i can make the timzone entry...

---

### Post by gmargo on 2010-03-25
You can see from the tzdata.postinst and tzdata.config files (in /var/lib/dpkg/info/) that:

/etc/timezone contains the timezone string.
/etc/localtime contains a copy of the zoneinfo file.

---

