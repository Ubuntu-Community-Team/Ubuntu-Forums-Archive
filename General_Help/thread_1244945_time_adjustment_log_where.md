---
title: "time adjustment log where"
date: 2009-08-20
forum: General Help
---

### Post by hgraham on 2009-08-20
Does 9.04 keep a log of the NTP time adjustments made and if so where is it?

---

### Post by tgeer43 on 2009-08-20
I don't have my Ubuntu system handy at the moment to check but I'd assume that if it does keep one then it would be somewhere in /var/log with all of the other log files. Have a look if you haven't already done so.

tgeer

---

### Post by hgraham on 2009-08-20
I have /var/log/ntpstats  but it is empty

---

### Post by tgeer43 on 2009-08-20
Are you sure that your system is configured to automatically connect to a time server?

tgeer

---

### Post by hgraham on 2009-08-20
I am not sure.  I went to applications/systemtools/systemsettings/

clicked on time and date,  checked set time and date automatically, picked asia.pool.ntp.org, clicked on apply, entered my password and exited

with System Monitor I found an: 

ntpd process under username ntp using Memory 0M  and shared memory 1M   also

cron process under username root using Memory 0M  and shared memory 1M

I have looked at many files with the name cron or ntp in them and can find no log of time correction.  9.04 seems to make a record of everything it does.  I just find it odd that there apparently is no log of time corrections.  Sometimes I do want an accurate time.

---

### Post by tgeer43 on 2009-08-20
It looks like everything is configured and working properly. If you want to check if the time server is responding correctly, open up a terminal and type:
```
sudo ntpdate ntp.asia.pool.ntp.org
```and see what message(s) it returns. It also wouldn't hurt to double check that ntpd is installed on your system. Don't confuse ntpdate with ntpd which are two totally different ways of synchronizing the time. Ntpdate is installed by default in Ubuntu but ntpd is not. Ntpd is a daemon that calculates the drift of your system clock and continuously adjusts it and is far superior to ntpdate. It is therefore the preferred method for time synchronization.
```
sudo apt-get install ntp
```will install ntpd if it is not already installed.

For more information go here:

[https://help.ubuntu.com/8.04/serverguide/C/NTP.html](https://help.ubuntu.com/8.04/serverguide/C/NTP.html)

This page contains detailed information on installing and/or configuring ntpdate and ntpd.

Hope this helps,

tgeer

---

### Post by hgraham on 2009-08-20
I got this with your suggestions

howard@howard-desktop:~$ sudo ntpdate asia.pool.ntp.org
[sudo] password for howard: 
20 Aug 22:05:42 ntpdate[1184]: the NTP socket is in use, exiting
howard@howard-desktop:~$ sudo apt-get install ntp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ntp is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
howard@howard-desktop:~$ 


Howard

---

### Post by hgraham on 2009-08-20
I rephrased the question in another post.  I asked, In Ubuntu 9.0, How do you set up an NTP time sync program and prove that it is working?

The title of the post is 'How ntp and verify'

Thank you very much for your help

Howard

---

### Post by tgeer43 on 2009-08-20
You are welcome and good luck - I'm stumped. :(

tgeer

---

