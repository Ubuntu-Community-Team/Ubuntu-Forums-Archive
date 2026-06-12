---
title: "Date and Time (I can't set it)"
date: 2011-03-10
forum: General Help
---

### Post by Sale on 2011-03-10
ubuntu 10.10 64bit here

my system clock keeps running late, and for some reason, I can't use NTP to synchronize it.

If I try to use System -> Preferences -> Administration -> Time and date I can't unlock the popup (see attached screenshot) - I can click on the little yellow lock icon but when I do so, nothing happens.

I tried "sudo ntpdate..." but i get the "the NTP socket is in use, exiting" error.

What can I do?

Thanks

---

### Post by rotave on 2011-03-10
It sounds like you haven't installed the package "ntp". Try
 
```
 sudo apt-get install ntp
```
 
And then you should be able to unlock it.

---

### Post by Sale on 2011-03-11
NTP is already installed
```
~$ sudo apt-get install ntp
[sudo] password for sale: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ntp is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by Krytarik on 2011-03-11
Ok, I don't know why you can't access the options via the GUI, but let's get deeper than this!

First, check if the "ntp" daemon is running:
```
service ntp status
```
Turns out in my case:
```
 * NTP server is running
```

Then check on which runlevels it is set up, therefore we need the "sysv-rc-conf" package:
```
sudo apt-get install sysv-rc-conf
sysv-rc-conf --list ntp
```
Turns out in my case:
```
ntp          0:off    1:off    2:on    3:off    4:off    5:off    6:off
```
To adjust the runlevel settings:
```
sysv-rc-conf
```

To check if any servers are set up: "/etc/ntp.conf"

If you need to manually syncronize the time:
- stop the ntp daemon
```
sudo service ntp stop
```
- run your "ntpdate" command

---

### Post by Sale on 2011-03-11
Thanks Krytarik

Manual update "ntpdate..." after stopping NTP service seems to work, but my clock is already off (late) by about a minute just 10min after the update.

Anyhow, the output from "sysv-rc-conf --list ntp" is:

```
ntp          1:off	2:on	3:on	4:on	5:on
```

Do you think I need to change anything?

---

### Post by Krytarik on 2011-03-11
Just set it the way I have it, I believe that is the default.

As for the repeatedly lagging time, you may
- replace the CMOS/BIOS battery
- check the BIOS settings, I found a post regarding AMD Cool'n'Quiet feature as the maybe-culprit:
[http://social.technet.microsoft.com/Forums/en/w7itprohardware/thread/e56e5469-9ffd-49c9-859a-d0e4291bdb58](http://social.technet.microsoft.com/Forums/en/w7itprohardware/thread/e56e5469-9ffd-49c9-859a-d0e4291bdb58)
- check for a BIOS update

---

### Post by ericrichards420 on 2011-03-11
if nothing else restart your computer go into the bios and set your time and date there save your settings and restart your computer.

---

### Post by Sale on 2011-03-11
OK...

Krytarik, I set the ntp runlevels the way you have them, and I guess we'll have to wait and see now ;)

As for the clock lagging, It looks I was a bit too jumpy on that one, it's fine now after all ...But thanks for the suggestions to both you and Eric, I'll keep those in mind, just in case.

---

### Post by Krytarik on 2011-03-11
Did you reboot after that, and more importantly did you specify a time server in "/etc/ntp.conf"?

---

### Post by Sale on 2011-03-11
NTP server was already specified in "/etc/ntp.conf", sorry I forgot to mention that before.

The NTP service is running and I've rebooted some 10 minutes ago (thanks for reminding me) and, so far it looks like things are fine. Just in case, I'll check back tomorrow, and report here.

BTW, I've noticed I still cant unlock the GUI "Time and Date" applet, but I can manually run "ntpdate...". I don't get the "the NTP socket is in use, exiting" error anymore, even though the ntp service is running.

---

### Post by Krytarik on 2011-03-11
> **Sale said:**
> but I can manually run "ntpdate...". I don't get the "the NTP socket is in use, exiting" error anymore, even though the ntp service is running.
Then the ntp daemon isn't running. I get the error when I run ntpdate. Re-check what I wrote earlier.

---

### Post by Sale on 2011-03-11
```
sale@sale-at-home:~$ service ntp status
 * NTP server is running
sale@sale-at-home:~$ sudo ntpdate pool.ntp.org
[sudo] password for sale: 
11 Mar 22:40:19 ntpdate[2866]: the NTP socket is in use, exiting
sale@sale-at-home:~$ 

```

It's ok now...I guess what i wrote before referred to the state of the system **before** the reboot...it's getting late here... ;)

---

### Post by Krytarik on 2011-03-11
Instead of simply waiting, you can also check "/var/log/daemon.log" for if ntp is doing its job. A handy tool for logs is "System -> Administration -> Log File Viewer".

---

### Post by Sale on 2011-03-11
I did check...looks like I'm fine now :)

---

