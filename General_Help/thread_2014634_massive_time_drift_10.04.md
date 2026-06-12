---
title: "massive time drift 10.04"
date: 2012-07-02
forum: General Help
---

### Post by willis11of12 on 2012-07-02
I recently had to go back to Ubuntu 10.04 LTS because vino-server keeps crashing in 12.04 LTS, but since doing so, I am seeing massive time drifts, like about a minute and a half over night!  I set up automatic time synchronization from the internet, via time and date settings as I think that fixed the problem for me in 12.04, but it's not stopping the time drift here.  

It sounds like that way only updates once a day, but the time drift I am having is so severe that a daily update isn't even close to what I need.  So what's a better way of fixing this issue?

---

### Post by matt_symes on 2012-07-04
Hi

Have you taken a look at ntpd (the daemon) as oppose to using debian ntpdate ?

```
sudo apt-get install ntp
```

It's configured through

```
/etc/ntp.conf
```

Here's one server you can use
```
ntp.ubuntu.com
```That may work for you.

Kind regards

---

### Post by msammels on 2012-07-04
Aww Matt, you stole my thunder. :P Anyway, you say you use network synchronization, but have you also tried manually setting it? Although, Matt's solution should work too.

---

### Post by willis11of12 on 2012-07-11
Thanks guys.  I'm actually not sure which one I am using, if it's ntpd or ntpDate.  I have manually set the time, but then it would be off again by several minutes when I checked it a few hours later.  It seems that after a few days of running, it eventually reached a point where it updates the time frequently enough that my problem is not so bad, meaning I don't loose my interaction abilities like before, but I am guessing it has to constantly be updating.  Below is what I have in the ntp.conf file, tell me if that looks right to you or if you suggest I do something different.  Many thanks!  :)

[COLOR=Blue]driftfile /var/lib/ntp/ntp.drift

statistics loopstats peerstats clockstats
filegen loopstats file loopstats type day enable
filegen peerstats file peerstats type day enable
filegen clockstats file clockstats type day enable

restrict -4 default kod notrap nomodify nopeer noquery
restrict -6 default kod notrap nomodify nopeer noquery

restrict 127.0.0.1
restrict ::1

server clock.redhat.com 
server clock2.redhat.com[/COLOR]

---

### Post by willis11of12 on 2012-07-11
By the way, here is what is in my drift file mentioned in the other file above:

[COLOR=Blue]500.000[/COLOR]

Does that mean it drifts 500 seconds in some given period of time?

---

### Post by SeijiSensei on 2012-07-11
I think that's in milliseconds but I'm not sure.

You might also want to run hwclock once or twice a day to sync your hardware clock with the NTP-delivered system time.  That only matters if you reboot, though.  I run this twice a day from /etc/crontab

```
/sbin/hwclock --systohc
```

Also I notice that clock2.redhat.com no longer has a DNS record.  You might consider replacing your server list with these:

server 0.centos.pool.ntp.org
server 1.centos.pool.ntp.org
server 2.centos.pool.ntp.org

I can ping all of those.  (They aren't single servers; they point to a number of servers using "round-robin" DNS so they are protected against any single machine going offline.)

---

