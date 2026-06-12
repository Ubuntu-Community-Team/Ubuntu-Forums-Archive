---
title: "Ubuntu 9.10 64bit reboots itself!"
date: 2010-03-07
forum: General Help
---

### Post by Linux-Djihad on 2010-03-07
Did anybody already have this problem that Ubuntu reboots itself (on a PC, not a Laptop) without any warning or something else?
I have the problem at least once a day. In all that cases Eclipse was open (coincidence?). I made nothing special. I just looked for information on a website and didn't even hit any key or something like that so it reboots completely by itself! Which approaches do I have to solve this? Threre is nothing special in /var/log/messages. 
My crontab seems to be right too:

```

$ cat /etc/crontab 
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user    command
17 *    * * *    root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *    root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7    root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *    root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )


```

---

### Post by Linux-Djihad on 2010-03-08
Today it rebooted without Eclipse open so it's an other issue. I listened to webradio with audacious and suddendly to music hang like an old vinyl. Then the system rebooted itself! If this situation won't get solved, I'm on to upgrade to Ubuntu 10 or try another distribution because I'm always afraid of data loss with this.

---

### Post by Linux-Djihad on 2010-03-11
Just tried kernel 2.6.31-19 instead of 2.6.31-20, but the problem still occures.

---

### Post by prodigy_ on 2010-03-11
Why are you so sure it's a software problem? If your system logs are clean, all the more reason to suspect faulty hardware. Perhaps your PSU can't handle the load properly?

---

### Post by Linux-Djihad on 2010-03-11
Because I bought this computer one month ago and I still doubt that it's a hardware problem.
For now I've upgraded to Lucid. I will see if the problem still persists. I will let you know the results. (When there are no reboots within a week, I guess that Lucid is working)

---

### Post by Linux-Djihad on 2010-03-12
It happens again. Conspicuous is that the system hangs for about 2-3 seconds until it reboots. So a PSU issue or does it rather have something to do with graphics / x-server / drivers?

---

### Post by audiomick on 2010-03-12
So, a fresh install of a different version of the OS, and the problem is still there. That sounds a lot like a hardware problem to me. I would even tend to suspect that is a hardware problem *_**because**_* the machine is only one month old.

Backup any data you have on the machine and take it back to the shop. It is a pain, I know, but it really sounds like the box has a problem, and it is better to get it sorted under guarantee.

And don't let the guy in the shop tell you any crap about "don't support linux". A hardware problem is a hardware problem and has nothing whatsoever to do with the OS...;)

---

### Post by Seq on 2010-03-12
I'd be looking for bad memory or overheating.

Just because the system is new doesn't mean nothing could be wrong hardware-wise. I've had hard drives fail within a month, I've had memory DOA, Motherboards with bad capacitors, etc.

I'd try a memtest. Let it run and see if you have the same issue.

---

### Post by rnerwein on 2010-03-12
hi
what i'll will try first. disable cron and see if your problem still exists.
only a idea.
ciao
forgot - did the system do a fsck when it restarts - if not i guess it was a shutdown

---

### Post by Linux-Djihad on 2010-03-12
I let a memtest run (just for once) and no errors.
BIOS says that nothing seems to be overheated, because the temperatures are between 35 and 42°C.
What I did is raising the RAM voltage to 1.80V instead of 1.5V. Maybe 1.5V is too few for 6 GB DDR3?
@rnerwein: I don't think it's an cron issue because the computer hangs before reboot (why should it hang when it's an cron issue)
And yes, it does a fsck after reboot.

---

### Post by Linux-Djihad on 2010-03-20
I think the increasing of the RAM voltage was the solution. I've had no reboots for one week. If I will not have any reboots the whole next week, I would declare this posting as solved.

---

### Post by Linux-Djihad on 2010-03-24
Another reboot happens. Now, I will get it to the vendor.

---

### Post by Linux-Djihad on 2010-06-30
At that time I've made a last try - a BIOS reset (Plug off power, and removed the CMOS battery).
After that, the BIOS has somehow been set to a default state. After I set the basic settings (time, fan speed,...) I've never got problems anymore. This was 3 months ago. So the problem looks finally solved. 

(Obviously they somehow buggered my BIOS up in that market I bought this computer)

---

