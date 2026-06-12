---
title: "Random crashes (black screen and freezing) on 9.10 on Lenovo T500"
date: 2010-01-23
forum: General Help
---

### Post by tedrogers on 2010-01-23
Hi,

Got a new Lenovo T500, slapped 9.10 on it. Set of programmes is exactly as on my previous IBM T42, but every so often I get a random crash. No errors, just a complete freeze with a "underscore" cursor in the top-left of the screen.

I think / suspect it may have something to do with Transmission running, or perhaps the recent kernel update to 2.6.31-17.

Anyone else had anything similar? Maybe on a T400 or R60 / R61 / T60 / T61?

Thanks.

---

### Post by tedrogers on 2010-02-08
Not solved by a reinstall of 9.10.

No idea of what is causing it.

Really stuck now. :(

Can anyone help please?

---

### Post by tedrogers on 2010-02-09
Not solved at all...happened again. Can anyone help.

Can I post the output of some log file to help diagnosis?

I suspect WPA Supplicant based on looking in /var/log/syslog...but I'm not really sure what I'm looking at. I just noticed that there is a big gap between 10.30pm and 7am when I noticed the machine had hung.

Here's a sample, but can post the whole thing if required:

```
Feb  8 22:46:32 t500 wpa_supplicant[1126]: WPA: Group rekeying completed with **INSERT MAC ADDRESS HERE** [GTK=CCMP]
Feb  8 22:46:32 t500 NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> group handshake
Feb  8 22:46:32 t500 NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Feb  8 22:48:06 t500 wpa_supplicant[1126]: CTRL-EVENT-SCAN-RESULTS 
Feb  9 07:16:35 t500 kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
Feb  9 07:16:35 t500 rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="904" x-info="http://www.rsyslog.com"] (re)start
Feb  9 07:16:35 t500 rsyslogd: rsyslogd's groupid changed to 102
Feb  9 07:16:35 t500 rsyslogd: rsyslogd's userid changed to 101
Feb  9 07:16:35 t500 kernel: [    0.000000] Initializing cgroup subsys cpuset
Feb  9 07:16:35 t500 kernel: [    0.000000] Initializing cgroup subsys cpu
Feb  9 07:16:35 t500 kernel: [    0.000000] Linux version 2.6.31-19-generic (buildd@palmer) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #56-Ubuntu SMP Thu Jan 28 01:26:53 UTC 2010 (Ubuntu 2.6.31-19.56-generic)
```

At 7.16am I think those entries are me restarting the computer.

Can anyone help please?

This is going to force me onto Windows 7 if I don't get it fixed and I would hate that.

Thanks.

---

### Post by tedrogers on 2010-02-12
It is definitely something relating to the wireless driver and libtorrent as far as I can gather so far.

I've also found some info to suggest that enabling the backports (linux-backports-modules-karmic) could help because it allows me to use the latest (unsupported) drivers. This also includes a wireless backports section which could be the solution.

Two days now and now problems after install the backports. :)

---

### Post by Struki on 2010-02-12
I'm having some crashes also, check the thread [http://ubuntuforums.org/showthread.php?t=1402806](http://ubuntuforums.org/showthread.php?t=1402806)
To see if we share some of the symptoms...

---

### Post by tedrogers on 2010-02-12
I've looked at your post, and you all seem to be using Hewlett Packard machines...but really I have no idea what could be causing your problems.

Have you tried the rollback to 9.04 though?

---

### Post by Struki on 2010-02-13
Not yet, i did upgrade from 9.04 so rolling back is my no win scenario, I'm also considering Fedora since I had some other problems on 9.04

---

### Post by tedrogers on 2010-02-13
In my experience, Fedora is really good at just *working* when Ubuntu has not been playing ball. Maybe because it's more up-to-date or bleeding edge.

However, I prefer Ubuntu...it's just a touch friendlier I think. :)

By all means let me know if you do try Fedora and it solves the problem for you.

---

### Post by starwed on 2010-03-08
I have exactly this problem (random crashes to black screen and unblinking cursor) on an ASUS eeepc 1008ha.

But I only noticed it *after* enabling the backports module!  (Which I installed to resolve a slightly different issue: previously I would get occasional freezes where the trackpad/keyboard became unresponsive, and this is apparently a known issue fixed by the backports.)

I'm curious which version of the backports you installed.  I have the set corresponding to 2.6.31.19, including the wireless specific ones.  

(Also, FWIW I haven't been running transmission when it crashed.)

---

### Post by tedrogers on 2010-03-08
> **starwed said:**
> I have exactly this problem (random crashes to black screen and unblinking cursor) on an ASUS eeepc 1008ha.

But I only noticed it *after* enabling the backports module!  (Which I installed to resolve a slightly different issue: previously I would get occasional freezes where the trackpad/keyboard became unresponsive, and this is apparently a known issue fixed by the backports.)

I'm curious which version of the backports you installed.  I have the set corresponding to 2.6.31.19, including the wireless specific ones.  

(Also, FWIW I haven't been running transmission when it crashed.)

I'm running 2.6.31.20.33 with no problems.

linux-backports-modules-karmic
linux-backports-modules-karmic-generic
linux-backports-modules-wireless-karmic-generic
linux-backports-modules-2.6.31-20-generic

---

### Post by starwed on 2010-03-09
As it happens, I got auto-upgraded to 2.6.31-20 today and haven't seen a crash since; it was a bit intermittent in the first place, but hopefully... :)

-edit-
Just for the record it's 5 days later and I haven't seen that crash since updating the backports.

---

### Post by psytrox on 2011-05-04
> **starwed said:**
> As it happens, I got auto-upgraded to 2.6.31-20 today and haven't seen a crash since; it was a bit intermittent in the first place, but hopefully... :)

-edit-
Just for the record it's 5 days later and I haven't seen that crash since updating the backports.


I have the same netbook(or close enough), with the same problem, after I dealt with installing backports for wireless-compat.  I am now trying an older kernel, and it hasn't given any further issues. If there is a fix for newer kernels, that would be better.

---

