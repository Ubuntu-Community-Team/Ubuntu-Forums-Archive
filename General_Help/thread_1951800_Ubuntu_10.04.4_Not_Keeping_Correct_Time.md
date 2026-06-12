---
title: "Ubuntu 10.04.4 Not Keeping Correct Time"
date: 2012-04-03
forum: General Help
---

### Post by wolf_3d on 2012-04-03
Sunday before last the clocks went forward 1 hour but the system time never updated and is always an hour behind. For instance it is 10:51 in the UK but the clock is still showing 09:51.

I keep going into System > Administration > Time & Date to change the time forward an hour but it never seems to stay the correct time when I log into Ubuntu. Sometimes when I change the time it gives an authentication error.

Pretty sure its not the CMOS battery as I fitted an new one last year. I have Ubuntu 12.04 installed on a test partition on this machine which still keeps perfect time.

---

### Post by wolf_3d on 2012-04-04
Bump #1 - Still a problem.

---

### Post by decrepit on 2012-04-04
check your time zone, is it set to London or GMT?

---

### Post by raja.genupula on 2012-04-04
* time zone is one issue 
* change time from manual to automatic update by choosing a network server . that will update your time automatically .

[https://help.ubuntu.com/community/UbuntuTime](https://help.ubuntu.com/community/UbuntuTime)

use that link as reference .

---

### Post by r-senior on 2012-04-04
Are you dual booting with Windows? This sounds like the old "Windows likes local time and Linux likes GMT" problem:

[http://mikebeach.org/2011/04/10/windows-linux-dual-boot-system-time-issues/](http://mikebeach.org/2011/04/10/windows-linux-dual-boot-system-time-issues/)

---

### Post by wolf_3d on 2012-04-04
Thank you for the responses, people.

> **decrepit said:**
> check your time zone, is it set to London or GMT?

It is set to Europe/London.

> **raja.genupula said:**
> * time zone is one issue 
* change time from manual to automatic update by choosing a network server . that will update your time automatically .

[https://help.ubuntu.com/community/UbuntuTime](https://help.ubuntu.com/community/UbuntuTime)

use that link as reference .

Forgot to mention that I tried this the other week too. I have installed ntp and selected 3 United Kingdom servers from the list. However it is still not showing the correct time. Restarting doesn't make a difference.

```
:~$ sudo dpkg-reconfigure tzdata
[sudo] password for ****: 

Current default time zone: 'Europe/London'
Local time is now:      Wed Apr  4 21:40:28 BST 2012.
Universal Time is now:  Wed Apr  4 20:40:28 UTC 2012.


```

Should be 22:40. 

NTP is definitely running;

```
:~$ sudo /etc/init.d/ntp status
 * NTP server is running

```

These are the servers that I'm using;
```
:~$ grep ^server /etc/ntp.conf or grep ^server /etc/ntp.conf.dhcp
/etc/ntp.conf:server ntp2a.mcc.ac.uk 
/etc/ntp.conf:server ntp2b.mcc.ac.uk
/etc/ntp.conf:server ntp2.ja.net
grep: or: No such file or directory
grep: grep: No such file or directory
grep: ^server: No such file or directory
grep: /etc/ntp.conf.dhcp: No such file or directory

```

Can't seem to reach any of the servers - firewall problem?

```
:~$ ntptrace ntp2b.mcc.ac.uk
ntpq: write to dir.mcc.ac.uk failed: Operation not permitted

```


> **r-senior said:**
> Are you dual booting with Windows? This sounds like the old "Windows likes local time and Linux likes GMT" problem:

[http://mikebeach.org/2011/04/10/windows-linux-dual-boot-system-time-issues/](http://mikebeach.org/2011/04/10/windows-linux-dual-boot-system-time-issues/)

I was dual-booting with Windows XP until February when I decided to replace it and install Fedora 16 and then I replaced Fedora 16 when Ubuntu 12.04 became beta in early March. No time problems until the other week though.

---

### Post by wolf_3d on 2012-04-04
Nevermind. It's fixed.

It was a firewall problem. Just added udp port 123 as a rule in my firewall and all is now working.

Thanks everyone.

---

### Post by hughr2005 on 2012-04-04
I wouldn't have thought a firewall issue! Learning something new everyday. My Mac updates time automatically, but I'm pretty sure port 123 isn't open. It must be some other protocol on mac.

---

