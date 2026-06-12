---
title: "Anacron not working"
date: 2009-11-23
forum: General Help
---

### Post by dreamnid on 2009-11-23
Hi,

Running 9.10 x64 which was upgraded from 9.04

I was investigating why automysqlbackup is only backing up MySQL intermittently. 

```

carMonitor_2009-09-10_13h06m.Thursday.sql.gz
carMonitor_2009-09-16_12h37m.Wednesday.sql.gz
carMonitor_2009-10-25_23h14m.Sunday.sql.gz
carMonitor_2009-11-06_10h30m.Friday.sql.gz
carMonitor_2009-11-10_13h57m.Tuesday.sql.gz
carMonitor_2009-11-23_15h19m.Monday.sql.gz

```

I ran automysqlbackup manually today (11-23), but as you can see, it isn't backing up every day like it should.

I saw in the syslog that anacron will start the daily/weekly job, but it will shortly get a TERM signal.

Example as follows:

```

Nov 21 00:51:34 dreamnid-desktop anacron[5104]: Anacron 2.3 started on 2009-11-21
Nov 21 00:51:34 dreamnid-desktop anacron[5104]: Will run job `cron.daily' in 5 min.
Nov 21 00:51:34 dreamnid-desktop anacron[5104]: Will run job `cron.weekly' in 10 min.
Nov 21 00:51:34 dreamnid-desktop anacron[5104]: Jobs will be executed sequentially


Nov 21 00:51:34 dreamnid-desktop NetworkManager: <info>  Sleeping...
Nov 21 00:51:34 dreamnid-desktop NetworkManager: <info>  (eth0): now unmanaged
Nov 21 00:51:34 dreamnid-desktop NetworkManager: <info>  (eth0): device state change: 2 -> 1 (reason 37)
Nov 21 00:51:34 dreamnid-desktop NetworkManager: <info>  (eth0): cleaning up...
Nov 21 00:51:34 dreamnid-desktop NetworkManager: <info>  (eth0): taking down device.
Nov 21 00:51:35 dreamnid-desktop NetworkManager: <info>  (eth1): now unmanaged
Nov 21 00:51:35 dreamnid-desktop NetworkManager: <info>  (eth1): device state change: 2 -> 1 (reason 37)
Nov 21 00:51:35 dreamnid-desktop NetworkManager: <info>  (eth1): cleaning up...
Nov 21 00:51:35 dreamnid-desktop NetworkManager: <info>  (eth1): taking down device.
Nov 21 00:51:35 dreamnid-desktop NetworkManager: <info>  (eth2): now unmanaged
Nov 21 00:51:35 dreamnid-desktop NetworkManager: <info>  (eth2): device state change: 8 -> 1 (reason 37)
Nov 21 00:51:35 dreamnid-desktop NetworkManager: <info>  (eth2): deactivating device (reason: 37).
Nov 21 00:51:35 dreamnid-desktop NetworkManager: <info>  (eth2): canceled DHCP transaction, dhcp client pid 1492
Nov 21 00:51:35 dreamnid-desktop NetworkManager: <WARN>  check_one_route(): (eth2) error -34 returned from rtnl_route_del(): Sucess#012
Nov 21 00:51:35 dreamnid-desktop NetworkManager: <info>  (eth2): removing resolv.conf from /sbin/resolvconf
Nov 21 00:51:35 dreamnid-desktop avahi-daemon[1343]: Withdrawing address record for 192.168.1.101 on eth2.
Nov 21 00:51:35 dreamnid-desktop avahi-daemon[1343]: Leaving mDNS multicast group on interface eth2.IPv4 with address 192.168.1.101.
Nov 21 00:51:35 dreamnid-desktop avahi-daemon[1343]: Interface eth2.IPv4 no longer relevant for mDNS.
Nov 21 00:51:35 dreamnid-desktop NetworkManager: <info>  (eth2): cleaning up...
Nov 21 00:51:35 dreamnid-desktop NetworkManager: <info>  (eth2): taking down device.
Nov 21 00:51:35 dreamnid-desktop NetworkManager: <info>  (eth2): carrier now OFF (device state 1)
Nov 21 00:51:35 dreamnid-desktop avahi-daemon[1343]: Withdrawing address record for fe80::20e:cff:feab:53a0 on eth2.


Nov 21 00:51:36 dreamnid-desktop init: anacron main process (5104) killed by TERM signal

```

I spaced out the NetworkManager section to make it easier to find the anacron process.

/etc/crontab and /etc/anacrontab haven't been modified by me.

Thanks!

---

### Post by honda on 2009-12-01
I'm having the exact same issue on 9.10 (32bit) upgraded from 9.04. 

anacron main process killed by TERM signal

, in syslog.

---

### Post by honda on 2009-12-07
This is a kludge of epic proportions... but at least I got my backups running....

After several minutes of thorough investigation of upstart I found out that I can delay the premature termination of anacron by adding this to the end of /etc/init/anacron.conf

pre-stop script
    # waste some time
    sleep 3600
end script


This gives plenty of time (1h) for anacron jobs to run before the job is terminated by the evil upgrade ghost hiding somewhere in the system.

---

### Post by edwardp on 2009-12-11
> **honda said:**
> This is a kludge of epic proportions... but at least I got my backups running....

After several minutes of thorough investigation of upstart I found out that I can delay the premature termination of anacron by adding this to the end of /etc/init/anacron.conf

pre-stop script
    # waste some time
    sleep 3600
end script


This gives plenty of time (1h) for anacron jobs to run before the job is terminated by the evil upgrade ghost hiding somewhere in the system.

I'm willing to try this on my desktops (both 32- and 64-bit) to see if it works, as I noticed both anacron and the software updater doesn't run automatically on either (from brand new, fresh installs, no upgrade).  

The laptop (strangely), 32-bit, also with a fresh, new install, updates fine and anacron does run daily.

---

### Post by dreamnid on 2009-12-11
Well, I saw from other threads that anacron is set to run at 7 in the morning in /etc/cron.d/anacron.  Since my computer is sleeping at that time, it will never run anacron.  I don't know why it is not set to run at some hourly interval.  

So I simply change my cron.d/anacron to read
30 */5 * * * root start -q anacron || :

This will run anacron every 5 hours.  Anacron has an internal db to make sure that the commands are only run once. 

I guess the other issue is that the wake-up scripts should also run the anacron, but I think that's where it dies early.  Honda seemed to come up with a hack.

In summary, if the acpi scripts for power-on and resume does start anacron and let it run successfully, then the reason for having it run at 7 makes sense.  Since this does not work, we'll have to run anacron at an hourly interval to make sure it does run to completion.

I haven't put much more research into this, so let me know if anything above is wrong.

---

### Post by edwardp on 2009-12-11
> **dreamnid said:**
> Well, I saw from other threads that anacron is set to run at 7 in the morning in /etc/cron.d/anacron.  Since my computer is sleeping at that time, it will never run anacron.  I don't know why it is not set to run at some hourly interval.  

anacron is designed for systems that are not powered on 24/7, from what I read.

I am happy to report that after adding those four lines specified in honda's message above, to /etc/init/anacron.conf on both of my desktops, anacron started five minutes after the system booted up earlier this morning.  I powered the other desktop on just now and anacron promptly started at 5:23 PM local time.

Since I noticed the package manager icon appear automatically earlier this morning on the other desktop, I believe this solves the update problem I had on both desktops.

Thank you, honda, for providing that information.  :grin:

---

### Post by disabled_20220313 on 2009-12-23
Hi,

It seems that having a upstart job script that simply has the exec statement works too. See below.

```

# anacron - anac(h)ronistic cron
#
# anacron executes commands at specific periods, but does not assume that
# the machine is running continuously

description	"anac(h)ronistic cron"

exec anacron -s

```

I don't know upstart, but a script like this would atleast always run to completion if it takes longer than an hour.

nb. I have only so far tested this on one reboot, but it did work.

Ciarán

---

### Post by billct on 2010-01-01
I'm using a Linux Mint 8 desktop with S3 suspend to ram.  I also ran into this problem with anacron being killed on resume.  The motherboard is an ECS A780GM-M3 and S3 suspend works well.

---

