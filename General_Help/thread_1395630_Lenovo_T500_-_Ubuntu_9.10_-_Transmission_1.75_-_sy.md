---
title: "Lenovo T500 - Ubuntu 9.10 - Transmission 1.75 - system crashing and freezing up!"
date: 2010-02-01
forum: General Help
---

### Post by tedrogers on 2010-02-01
Hi all,

I've just noticed this. I think it is Transmission 1.75, but can't be totally certain (maybe there is a crash log I can check - don't know where to look for this). Happy to look and post if someone can assist.

Running Transmission, downloading multiple files, then for no reason the entire system crashes. :shock:

Seems like a pretty serious crash too. Total black screen, sometimes a frozen cursor or mouse pointer. Totally unresponsive. Hard shutdown necessary.

This has happened a few times now. Any ideas anyone?

Thanks.

---

### Post by tedrogers on 2010-02-03
So, I had this again tonight! Just a collosal crash for no reason.

It is definitely something to do with Transmission 1.75.

I have now switched over to Deluge as a result, but I prefer Transmission, :(

Anyone got any ideas?

Thanks.

---

### Post by tedrogers on 2010-02-04
Okay, same thing just happened but with Deluge 1.1.9 instead.

So it's not Transmission's fault I'd guess.

It would certainly seem to have something to do with downloading multiple torrents.

Hmmmm...stuck!

---

### Post by tedrogers on 2010-02-04
I heard somewhere that this *might* be because of Firefox...so I ran Deluge without anything else for as long as it took to crash...and it just did! :(

This sucks. Please help.

---

### Post by tedrogers on 2010-02-07
I reinstalled and but it did not solve the problem.

Any help please? :( Stuck here.

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

### Post by cristofaro on 2010-02-10
You could try doing a memory test. Might be a hardware related issue.

HowTo Memory Test: [https://help.ubuntu.com/community/MemoryTest](https://help.ubuntu.com/community/MemoryTest)

---

### Post by tedrogers on 2010-02-10
Tried that and run it for 2 hours...no joy...all ok.

It is definitely something relating to the wireless driver and libtorrent as far as I can gather so far.

I've tried recursing kernels...2.6.31-17 so far with same problem. Currently testing 2.6.31-16 to see if that helps.

I've also found some info to suggest that enabling the backports (linux-backports-modules-karmic) could help because it allows me to use the latest (unsupported) drivers. This also includes a wireless backports section which could be the solution.

I'll know by the morning if this is working...my laptop will be on all night as usual and if I wake to a flashing CAPS light then I know it has crashed (again!!). If not, then perhaps the backports are working.

It seems that this problem is caused by either:

1. Overheating (unlikely in my case)
2. Wireless driver bug that affects ACPI and causes kernel panic (most likely based on my reading of [sometimes very] old posts).

So...I was on my own on this one until you replied...hopefully something I am trying will work. This is a modern laptop (T500) and so should be all good really!

My next step to test the libtorrent issue is to use ktorrent instead, which doesn't use libtorrent.

Both deluge and transmission do, and it is with those that I have been experiencing the crashes.

Wish me luck, or if you have other suggestions I would welcome them.

Thanks for your reply.

---

### Post by cristofaro on 2010-02-10
Perhaps a good test would be to disable the wireless and use the Ethernet port on your laptop to download the torrents instead. That way if you crash again at least we would have ruled out the wireless bug.  

Wish I could be more helpful, I'm a little out of my depth :P

---

### Post by tedrogers on 2010-02-11
No problem!

So far I think everything is okay. The backports that I installed might have done the trick.

I don't want to speak too soon, but the laptop has been on all night with deluge running and it was still alive in the morning and is still alive now after being used for two hours.

I'm going to keep an eye on things, but this will be a massive relief it it has worked. :)

---

### Post by tedrogers on 2010-02-12
Two days now and no problems...I'm gonna mark this as solved. :)

---

### Post by cristofaro on 2010-02-12
great! If you can you should provide a link to the specific backports used and how you installed them to help out others.

---

### Post by tedrogers on 2010-02-13
This has definitely fixed it for me! :)

I installed through synaptic:

linux-backports-modules-karmic-generic
linux-backports-modules-wireless-karmic-generic
linux-backports-modules-karmic

Hope this helps someone else.

---

