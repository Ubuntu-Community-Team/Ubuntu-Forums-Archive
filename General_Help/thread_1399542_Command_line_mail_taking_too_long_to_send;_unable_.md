---
title: "Command line mail taking too long to send; unable to qualify my own domain name"
date: 2010-02-05
forum: General Help
---

### Post by narnie on 2010-02-05
Hello,

I'm having a problem with my mail. When I send mail, it takes a long time for the send to complete.

In the below, datestamp is just a simple script to put in a no-white-space date/time stamp.

```
$ datestamp ; mail woodnt; datestamp
02-05-10@193844
Subject: test
timer
Cc: 
02-05-10@193956
```

a tail -50 /var/log/syslog shows a problem with :

```
Feb  5 19:38:56 toshiba-laptop sendmail[10772]: My unqualified host name (toshiba-laptop) unknown; sleeping for retry
Feb  5 19:38:59 toshiba-laptop ypbind[1512]: broadcast: RPC: Timed out.
Feb  5 19:39:56 toshiba-laptop sendmail[10772]: unable to qualify my own domain name (toshiba-laptop) -- using short name
Feb  5 19:39:56 toshiba-laptop sendmail[10772]: o161duSX010772: from=woodnt, size=32, class=0, nrcpts=1, msgid=<201002060139.o161duSX010772@toshiba-laptop>, relay=woodnt@localhost
Feb  5 19:39:56 toshiba-laptop sm-mta[10774]: o161duNP010774: from=<woodnt@toshiba-laptop>, size=321, class=0, nrcpts=1, msgid=<201002060139.o161duSX010772@toshiba-laptop>, proto=ESMTP, daemon=MTA-v4, relay=localhost [127.0.0.1]
Feb  5 19:39:56 toshiba-laptop sendmail[10772]: o161duSX010772: to=woodnt, ctladdr=woodnt (1000/1000), delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=30032, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (o161duNP010774 Message accepted for delivery)
```

Here is my /etc/hosts file:

```
$ cat /etc/hosts
127.0.0.1	localhost
#127.0.0.1	toshiba-laptop
192.168.1.50	dell-desktop
192.168.1.51	gateway
192.168.1.52	woodnt-laptop
192.168.1.53	fujitsu
192.168.1.54	toshiba-laptop
192.168.1.61	krista-netbook
192.168.1.62	luke-netbook
192.168.1.63	beth-netbook

# The following lines are desirable for IPv6 capable hosts
#::1     localhost ip6-localhost ip6-loopback
#fe00::0 ip6-localnet
#ff00::0 ip6-mcastprefix
#ff02::1 ip6-allnodes
#ff02::2 ip6-allrouters
#ff02::3 ip6-allhosts
```

Here is my ifconfig output showing the correct ip:

```
$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:1e:65:07:72:c6  
          inet addr:192.168.1.54  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:65ff:fe07:72c6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:131563 errors:0 dropped:0 overruns:0 frame:0
          TX packets:122576 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:127932916 (127.9 MB)  TX bytes:18785169 (18.7 MB)
```

Please note the lag between timestamp 19:38:59 and 19:39:56 where broadcast RCP timed out and it was unable to qualify my own domain name. Any idea how to fix this?

With thanks,
Narnie

---

### Post by narnie on 2010-02-05
Well, I figured it out just now after I posted this.

The last thing I tried was commenting out my hostname listing in /etc/hosts like so:
```
#192.168.1.54    toshiba-laptop
```This is an auto-generated hosts file from a script I wrote to make sure all computers have the same hosts-file on my home network.

Evidently, it is not good to have your own hostname in the hosts file like this.

**If any networking guru might want to comment on why this is so, this may help us mere amateurs learn from my mistake.**

Hope this might help someone else that might ever have this problems.

Yours,
Narnie

---

### Post by narnie on 2010-02-05
I take it back. It isn't a fix.

When I commented out the computer in /etc/hosts, then the system gave this:

```
$ sudo su
sudo: unable to resolve host toshiba-laptop
```

and this:

```
$ ssh -p 50505 toshibia-laptop
ssh: Could not resolve hostname toshibia-laptop: Name or service not known
```

Now back to square one. How to resolve the original issue.

Narnie

---

### Post by Barriehie on 2010-02-05
Do you have a file in your **/etc** directory named **hostname** that contains your hostname???

Barrie

---

### Post by narnie on 2010-02-05
> **Barriehie said:**
> Do you have a file in your **/etc** directory named **hostname** that contains your hostname???

Barrie

Yes. 

```
$ cat /etc/hostname
toshiba-laptop
```

---

### Post by Barriehie on 2010-02-05
Forgot one!  What about **/etc/mailname**? Should be same as **/etc/hostname**.

---

### Post by narnie on 2010-02-05
OK, here's the "partial fix."

sendmail MUST have a fully qualified domain name or it gives this error. So "tweak" the /etc/hosts file like so:

```
127.0.0.1    localhost localhost.localdomain toshiba-laptop toshiba-laptop.foobar
```

That fixed both problems. mail now sends quickly and I can ssh to toshiba-laptop without error and do a sudo su without an error report.

The problem now is that I don't get mail. Hehe. Oh the joys ! Any ideas how to fix all these issues at once?

Cheerio,
Narnie

---

### Post by narnie on 2010-02-05
> **Barriehie said:**
> Forgot one!  What about **/etc/mailname**? Should be same as **/etc/hostname**.

Yes, it is there:

```
$ cat /etc/mailname 
toshiba-laptop
```

---

### Post by Barriehie on 2010-02-05
Glad you got it!

---

### Post by narnie on 2010-02-05
Ok, here is the real fix.

```
$ cat /etc/hosts
127.0.0.1	localhost localhost. toshiba-laptop toshiba-laptop.
192.168.1.50	dell-desktop
192.168.1.51	gateway
192.168.1.52	woodnt-laptop
192.168.1.53	fujitsu
192.168.1.54	toshiba-laptop.
192.168.1.61	krista-netbook
192.168.1.62	luke-netbook
192.168.1.63	beth-netbook
```

Note periods at the end the hosts of the 127.0.0.1 line and 192.158.1.54 as in:

localhost.
toshiba-laptop.

That satisfied sendmail and mail works immediately with no sleeping and actually delivers the mail !!! ssh'ing works as well now.

That problem is now solved. YEA! Now on to others ;)

Cheerio all,
Narnie

---

### Post by JSeymour on 2010-02-05
> **narnie said:**
> Please note the lag between timestamp 19:38:59 and 19:39:56 where broadcast RCP timed out and it was unable to qualify my own domain name. Any idea how to fix this?
Proper configuration of your system and sendmail.

For example:
> **narnie said:**
> The last thing I tried was commenting out my hostname listing in /etc/hosts like so:
```
#192.168.1.54    toshiba-laptop
```This is an auto-generated hosts file from a script I wrote to make sure all computers have the same hosts-file on my home network.

Evidently, it is not good to have your own hostname in the hosts file like this.Sure it is.  Every machine I've had on every network I've ever done, well, all the 'nix machines, anyway, have had their own hostnames in their own /etc/hosts.  But it should be more like:
dot.ed.qu.ad hostname.example.com hostname
rather than just
dot.ed.qu.ad hostname

Lacking a proper domain, you might be able to get away with using "localdomain" for the domain name, internally.  As long as all the machines and any MTAs know they're running in "localdomain," you should be able to get away with it.  (N.B.: I haven't tried anything like that in a long, long, *long* time.)

As for configuring sendmail properly: Can't help you with that.  I haven't used sendmail in about forever.  Sendmail's causing the delay because you're sending to "woodnt" and it's trying to figure out "woodnt@what?"  It's finally giving up and deciding, for lack of a better choice, it must be "woodnt@localhost."  If you either configured sendmail properly or sent the email to "woodnt@localhost" or "woodnt@toshiba-laptop," it'd know where to send it right off.

Trying to throw email around on a LAN w/o a proper mailserver and DNS, esp. using sendmail, is an exercise in masochism, IMO ;).

Not sure what the point to running an MTA on a laptop is, or passing email around internally to the laptop, but if it amuses you: By all means: Have at it :)

Last time I ran an MTA on a laptop, other than for experimental/test purposes, was in the days before 'net connections were commonly available in hotels.  When I went out-of-town on business I'd make a dialup UUCP connection back to the mothership, which would trigger a download of any email awaiting me.  Then I'd dump the connection.  I could read and answer it at my leisure and the MTA would queue it up until I triggered the next "phone home," at which time my outgoing would get sent on its way and any new incoming would get picked up.  Sounds crude, by today's standards, but it actually worked quite well :).

Jim

---

### Post by dcstar on 2010-02-06
> **JSeymour said:**
> 
.......
Trying to throw email around on a LAN w/o a proper mailserver and DNS, esp. **using sendmail, is an exercise in masochism**, IMO ;).
.......

There is no point whatsoever in installing **sendmail** on an Ubuntu system, Ubuntu already installs **postfix** by default which is a far easier to configure MTA and it "works out of the box".

---

### Post by narnie on 2010-02-07
> **JSeymour said:**
> Proper configuration of your system and sendmail.

For example:
Sure it is.  Every machine I've had on every network I've ever done, well, all the 'nix machines, anyway, have had their own hostnames in their own /etc/hosts.  But it should be more like:
dot.ed.qu.ad hostname.example.com hostname
rather than just
dot.ed.qu.ad hostname

Lacking a proper domain, you might be able to get away with using "localdomain" for the domain name, internally.  As long as all the machines and any MTAs know they're running in "localdomain," you should be able to get away with it.  (N.B.: I haven't tried anything like that in a long, long, *long* time.)

As for configuring sendmail properly: Can't help you with that.  I haven't used sendmail in about forever.  Sendmail's causing the delay because you're sending to "woodnt" and it's trying to figure out "woodnt@what?"  It's finally giving up and deciding, for lack of a better choice, it must be "woodnt@localhost."  If you either configured sendmail properly or sent the email to "woodnt@localhost" or "woodnt@toshiba-laptop," it'd know where to send it right off.

Trying to throw email around on a LAN w/o a proper mailserver and DNS, esp. using sendmail, is an exercise in masochism, IMO ;).

Not sure what the point to running an MTA on a laptop is, or passing email around internally to the laptop, but if it amuses you: By all means: Have at it :)

Last time I ran an MTA on a laptop, other than for experimental/test purposes, was in the days before 'net connections were commonly available in hotels.  When I went out-of-town on business I'd make a dialup UUCP connection back to the mothership, which would trigger a download of any email awaiting me.  Then I'd dump the connection.  I could read and answer it at my leisure and the MTA would queue it up until I triggered the next "phone home," at which time my outgoing would get sent on its way and any new incoming would get picked up.  Sounds crude, by today's standards, but it actually worked quite well :).

Jim

I'm going it because cron automatically sends mail when a process runs to alert the user that it was done. I would like to receive these alerts.

Also, on this laptop, cron jobs are piling up because it is trying to mail to the user but mail can't get through. It can result in hundreds of cron processes if left unchecked. Please see this thread to see my problem if u r interested.  It is very frustrating to me and I don't want to have to reinstall just to "fix" this. I'd rather fix, fix it and learn in the process.

[http://ubuntuforums.org/showthread.php?t=1399618]("http://ubuntuforums.org/showthread.php?t=1399618")

With thanks,
Narnie

---

