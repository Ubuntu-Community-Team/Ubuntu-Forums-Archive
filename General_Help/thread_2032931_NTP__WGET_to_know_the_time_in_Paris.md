---
title: "NTP / WGET to know the time in Paris?"
date: 2012-07-25
forum: General Help
---

### Post by honeybear on 2012-07-25
Hi,

I would like to use into a script the time based on a website or ntp (that would be robust) to insert date/time in this format:

2012-07-23-01-20-20.
yy-mm-dd-hh-mm-ss

Would you know such a website or ntp use that would allow this.

thank you

---

### Post by codemaniac on 2012-07-25
> **honeybear said:**
> Hi,

I would like to use into a script the time based on a website or ntp (that would be robust) to insert date/time in this format:

2012-07-23-01-20-20.
yy-mm-dd-hh-mm-ss

Would you know such a website or ntp use that would allow this.

thank you

You can transform the date in your required format i.e [yy-mm-dd-hh-mm-ss].

```
date +"%Y-%m-%d-%H-%M-%S"
```

---

### Post by greenpeace on 2012-07-25
> **codemaniac said:**
> You can transform the date in your required format....

Expanding on your answer, the following will give you the time in Paris... assuming that the time on your box is correct! :)

```
TZ='Europe/Paris' date +"%Y-%m-%d-%H-%M-%S"
```

---

### Post by honeybear on 2012-08-04
I didnt mean how to use date ... ;)

---

### Post by kjohri on 2012-08-04
There are two parts of the problem. First, finding the current time using the NTP. Second, formatting the time using the date command.

The current time can be found using the ntpdate command,

$ sudo ntpdate fr.pool.ntp.org

This is a one time query of current time. If you wish to synchronize time on a continuous basis, you need to run the NTP daemon, ntpd.

Once the correct time is available in the system, it can be printed using the date command as suggested by codemaniac.

For more information about NTP, refer to the following links,

[http://www.softprayog.in/tutorials/synchronize-your-computers-clock-using-the-ntp](http://www.softprayog.in/tutorials/synchronize-your-computers-clock-using-the-ntp)
[http://www.pool.ntp.org/zone/fr](http://www.pool.ntp.org/zone/fr)

---

### Post by honeybear on 2012-08-04
You know sthg for instance like this using https, but a pool ntp to wget would be much better.

wget -q -e 'http_proxy=' --no-cache --no-check-certificate -O - [https://ntp-a1.nict.go.jp/cgi-bin/time](https://ntp-a1.nict.go.jp/cgi-bin/time)

---

