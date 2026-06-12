---
title: "ntp doesn't sync and time drifts off"
date: 2012-07-30
forum: General Help
---

### Post by jsedwards on 2012-07-30
I have several machines (on completely different networks) all running either 11.04 or 12.04.  On all of them except one NTP works fine and the time stays sync'd fine.  On the one machine NTP doesn't seem to ever find a server and sync to it.

The result of ntpq -p:


```
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
 sola-dal-09.ser 64.250.177.145   2 u   33   64    1   70.629  -4146.9   0.001
 ntp1.Rescomp.Be 169.229.128.214  3 u   32   64    1   63.629  -4158.7   0.001
 247.conarusp.ne 216.218.254.202  2 u   31   64    1   70.431  -4163.3   0.001
 helium.constant 129.7.1.66       2 u   30   64    1  102.066  -4179.0   0.001
 europium.canoni 193.79.237.14    2 u   29   64    1  171.013  -4187.2   0.001

```

I've restarted the ntp daemon many times and it gets a different list of servers every time, but I never see a + or * by any of the names.

If I run ntpdate it always says:

```
30 Jul 13:35:36 ntpdate[12171]: no servers can be used, exiting
```

Does anyone have any suggestions of other things I can check?

Thanks,
   -Scott

---

### Post by dodo3773 on 2012-07-30
First thing I would check are these two things:

```

sudo ntpd -qgddd

```
Note: -q switch should update the time. Pretty sure ntpupdate is more or less depreciated depending on what version of ntp you are running. -d is for debugging. Three should be sufficient. 

The second thing I would check is services:
```

cat /etc/services | grep ntp

```
Look for this:
```

ntp               123/tcp
ntp               123/udp

```

Lastly I would say check your config file. Mine is at "/etc/ntp.conf". Here is mine for reference if you want to look through it (the only parts I changed were the servers when I set it up):
```

server 0.us.pool.ntp.org iburst
server 1.us.pool.ntp.org iburst
server 2.us.pool.ntp.org iburst
server 3.us.pool.ntp.org iburst

restrict default nomodify nopeer
restrict 127.0.0.1
restrict ::1

driftfile /var/lib/ntp/ntp.drift
logfile /var/log/ntp.log

```

---

### Post by jsedwards on 2012-07-30
When I do this:

```
sudo ntpd -qgddd
```

It works fine, it sets the time correctly (I set the clock about 3 minutes fast before running it):

```

...
step_systime: step -191.185220 residual 0.000000
In ntp_set_tod
ntp_set_tod: clock_settime: 0: Success
ntp_set_tod: Final result: clock_settime: 0: Success
addto_syslog: ntpd: time set -191.185220 s
ntpd: time set -191.185220s
filegen  2 3552675327 0 3552595200

```

The /etc/services looks correct:

```

ntp		123/tcp
ntp		123/udp				# Network Time Protocol

```

My /etc/ntp.conf file is unchanged from what came with the package (I edited out all the commented lines):

```

driftfile /var/lib/ntp/ntp.drift

statistics loopstats peerstats clockstats
filegen loopstats file loopstats type day enable
filegen peerstats file peerstats type day enable
filegen clockstats file clockstats type day enable

server 0.ubuntu.pool.ntp.org
server 1.ubuntu.pool.ntp.org
server 2.ubuntu.pool.ntp.org
server 3.ubuntu.pool.ntp.org

server ntp.ubuntu.com

restrict -4 default kod notrap nomodify nopeer noquery
restrict -6 default kod notrap nomodify nopeer noquery

```

I then tried running it without the -q and it tries a few servers and then just stops and sits there without ever setting the time.

I can attach the output if that would be helpful?

Thanks,
  -Scott

---

### Post by dodo3773 on 2012-07-30
[QUOTE=jsedwards]
I then tried running it without the -q and it tries a few servers and then just stops and sits there without ever setting the time.
[/QUOTE]

The -q switch is what sets the time. So, if you run the command without it it won't change it. But, if it is working then it is working. Maybe if you change the default daemon options and add -q (/etc/default/ntp)? From this:
```

NTPD_OPTS='-g'

```
to this:
```

NTPD_OPTS='-g -q'

```

Then restart the daemon. Does that work?

---

### Post by jsedwards on 2012-07-30
I'm confused then, because the man page says that -q makes it quit after the first time the clock is set (which is what it does):

```

-q     Exit the ntpd just after the first time the clock is set.  This behavior mimics that of the ntpdate program, which is to be retired.   The  -g and -x options can be used with this option.  Note: The kernel time discipline is disabled with this option.

```

That last line is interesting however, I have no idea what the "kernel time discipline" is, but I wonder if the time is set with the -q because it disables the kernel thing?

---

### Post by dodo3773 on 2012-07-30
> **jsedwards said:**
> I'm confused then, because the man page says that -q makes it quit after the first time the clock is set (which is what it does):


So, if you add that option to the daemon it kills / ends the daemon process? Is that what you mean? The only other thing I could suggest to you would be to add the command that works to roots crontab and maybe do it that way. Other than that I have no idea

---

### Post by jsedwards on 2012-07-30
> So, if you add that option to the daemon it kills / ends the daemon process? Is that what you mean?

Yes that is exactly what happens.  Apparently ntpd -q is the replacement for ntpdate.

> The only other thing I could suggest to you would be to add the command that works to roots crontab and maybe do it that way. 

I thought about doing that myself.  I guess I could do that as a last resort.

I ran ntpd -gddd on one of the machines that works, it syncs right up and after a few minutes it picks some servers and is happy:


```

     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
+utility-lax.rac 50.97.210.169    3 u   20   64  377   60.526    5.327   5.013
-ns2.uplogon.com 66.228.35.252    3 u   10   64  377   62.722   -3.923   1.797
*clock.team-cymr 172.16.32.4      2 u    8   64  377   53.364    1.711   4.443
-ntp1.Housing.Be 169.229.128.214  3 u    9   64  377   85.730   15.681   2.388
+europium.canoni 193.79.237.14    2 u    8   64  377  142.582    2.573   5.291

```


The bad machine never seems to select the servers.  I'm wondering if it is because it drifts off so fast, that ntp cannot correct it fast enough?  It gains about 1 second per minute.

Anyway, thanks for your help and suggestions!

---

### Post by dodo3773 on 2012-07-30
> **jsedwards said:**
> 
The bad machine never seems to select the servers.  I'm wondering if it is because it drifts off so fast, that ntp cannot correct it fast enough?  It gains about 1 second per minute.

Anyway, thanks for your help and suggestions!

You are welcome. I am glad to help. If it is a server problem then why not just use different servers?

---

### Post by jsedwards on 2012-07-31
> If it is a server problem then why not just use different servers?

It picked different servers from the pool each time I started ntp, it just didn't seem to like any of them.  I noticed the jitter was very high (>1000) on the bad system and very low (<10) on the working ones.  So I did a search and found this thread:  [http://fixunix.com/ntp/67593-ntp-high-jitter-reject-condition.html]("http://fixunix.com/ntp/67593-ntp-high-jitter-reject-condition.html")

I gather from it that ntp cannot correct for a clock that drifts off that quickly (it was gaining 1 second every minute).  I also gather from that thread that it might be a hardware problem.

It appears to be fixed after I did this:

```
sudo tickadj 9900
```

Now the ntpq -p prints this:


```
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
-wwwco1test12.mi 64.236.96.53     2 u   57   64  377   81.122  161.488  38.258
+stripes.jentfoo 71.252.193.26    3 u   55   64  377   75.010   85.534  30.261
*clock01.chil01. 204.9.54.119     2 u   55   64  377   94.233  116.040  24.678
-ns2.oninit.com  208.85.173.56    3 u   58   64  377   84.958  124.831  35.303
+europium.canoni 193.79.237.14    2 u   57   64  377  168.348   76.030  36.582

```

So it has selected 3 servers and seems to be staying in sync

:guitar:

---

### Post by dodo3773 on 2012-07-31
Oh awesome. Glad you sorted it out.

---

