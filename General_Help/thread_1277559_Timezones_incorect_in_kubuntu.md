---
title: "Timezones incorect in kubuntu"
date: 2009-09-28
forum: General Help
---

### Post by mahela007 on 2009-09-28
I've set the correct timezone in my version of Kubuntu but the time that is displayed is way off the actual time. What do I do?

---

### Post by McWeirdo on 2009-09-28
same problem in ubuntu :D   here anyway...

---

### Post by slakkie on 2009-09-28
* Set the correct timezone in /etc/timezone

eg Europe/Amsterdam

* Install openntpd and ntpdate

sudo aptitude install openntpd ntpdate

* Update your current time:

sudo ntpdate 0.debian.pool.ntp.org

* Edit openntpd's config file

sudo nano /etc/openntpd/ntpd.conf

* Don't worry about it again.

---

### Post by dancro on 2009-10-01
Please tell me what is the update to be made to /etc/openntpd/ntpd.conf?  I added a single server but my time is still wrong by seven hours (GMT) after I power off.  

Taking a stab at the update I am adding the IP address of my machine as listen on. Is that the correct answer?

Thank you in advance for any assistance, and for the info you have provided that makes it easier for me to set the time when I power on.  Now if I could just make the time right all the time.

Don't actually know when the time went bad, it used to be fine.

Thanks again,
Dan

---

### Post by slakkie on 2009-10-02
> **dancro said:**
> Please tell me what is the update to be made to /etc/openntpd/ntpd.conf?  I added a single server but my time is still wrong by seven hours (GMT) after I power off.  

Taking a stab at the update I am adding the IP address of my machine as listen on. Is that the correct answer?

Thank you in advance for any assistance, and for the info you have provided that makes it easier for me to set the time when I power on.  Now if I could just make the time right all the time.

Don't actually know when the time went bad, it used to be fine.

Thanks again,
Dan

No, i have the following configured in my ntpd.conf:

```

# use a random selection of 4 public stratum 2 servers
# see http://twiki.ntp.org/bin/view/Servers/NTPPoolServers
# and http://www.pool.ntp.org/
server 0.debian.pool.ntp.org
server 1.debian.pool.ntp.org
server 2.debian.pool.ntp.org
server 3.debian.pool.ntp.org

```

You might want to look into your BIOS to set/check your hardware clock..

---

### Post by dondos on 2009-10-02
Probably this is a dual-boot system.

Microsoft operating systems adjust the hardware clock in local-time. Linux on the other side, assumes that the hardware clock is in UTC/GMT. However, this can be changed, if you edit /etc/default/rcS. Change **UTC=yes** to **UTC=no**. Finally, synchronize your system with an NTP server.
Hope this helps too.

Also see: [http://linux.die.net/man/8/hwclock]("http://linux.die.net/man/8/hwclock").

---

### Post by SuperSonic4 on 2009-10-02
What does the BIOS clock say?

---

### Post by dancro on 2009-10-03
SOLVED
Thank you all for replying.  To respond to your questions and suggestions:

slakkie,
I have the four server statements also and removed the other changes that I made.  

dondos
Yes, this is a dual boot system, but I seldom boot into Windows.
utc=no is already set.  
I run sudo ntpdate 0.debian.pool.ntp.org to set the time.  The time is off by seven hours after I power off.

SuperSonic4
The BIOS time is the correct time.  

Your questions and advise led me to the solution.
I found a file /etc/default/openntpd with this info:
# Uncomment to set the system time when starting in case the offset 
# between the local clock and the servers is more than 180 seconds.
# For other options, see man ntpd 
#DAEMON_OPTS="-s"

I uncommented the DAEMON_OPTS statement and now the system powers up with the correct time.

I'm sure it doesn't matter but I am not running kubuntu
Thanks again for leading me in the right direction.
Dan

---

