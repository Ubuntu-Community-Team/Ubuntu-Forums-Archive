---
title: "Problem verifying credentials?????"
date: 2012-06-14
forum: General Help
---

### Post by jaws222 on 2012-06-14
I use a tool from TD Ameritrade called Trade Architect and when I log in it just spins in an infinite loop while it is verifying credentials.  I'm convinced it is a bug with 12.04.  I've tried it on three different computers and used three different browsers (Google Chrome, Chromium & Firefox).  Everything was fine on 11.10 and previous versions.  Any ideas?

---

### Post by jaws222 on 2012-06-16
I guess nobody else has encountered this problem.

---

### Post by sffvba[e0rt on 2012-06-16
*Thread moved to **General Help**.*


404

---

### Post by steeldriver on 2012-06-16
is the firewall enabled?

```
service ufw status
``` maybe that tool needs some ports opened in order to authenticate/run?

---

### Post by jaws222 on 2012-06-18
It looks like there was not a firewall program installed.  when I run service ufw status the response is ufw start/running.  I installed gufw but am not sure what would need opening.  I guess I can experiment.  I found this guide here, not sure what port to try though:

**Basic Usage**

 Getting started with ufw is easy. For example, to enable firewall, allow ssh access, enable logging, and check the status of the firewall, perform:
$ sudo ufw allow ssh/tcp
$ sudo ufw logging on 
$ sudo ufw enable
$ sudo ufw status

 Firewall loaded  
To                                    Action           From
 22:tcp                           ALLOW          ANYWHERE
 
**Advanced Functionality**

 As mentioned, the ufw framework is capable of doing anything that iptables can do. This is achieved by using several sets of rules files, which are nothing more than iptables-restore compatible text files. Fine-tuning ufw and/or adding additional iptables commands not offered via the ufw command is a matter of editing various text files: 

[LIST]
[*]**/etc/default/ufw**: high level configuration, such as default policies, IPv6 support and kernel modules to use
[*]**/etc/ufw/before[6].rules**: rules in these files are evaluated before any rules added via the ufw command
[*]**/etc/ufw/after[6].rules**: rules in these files are evaluated after any rules added via the ufw command
[*]**/etc/ufw/sysctl.conf**: kernel network tunables
[*]**/var/lib/ufw/user[6].rules** or **/lib/ufw/user[6].rules** (0.28 and later): rules added via the ufw command (should not normally be edited by hand)
[*]**/etc/ufw/ufw.conf**: sets whether or not ufw is enabled on boot, and in 9.04 (ufw 0.27) and later, sets the LOGLEVEL
[/LIST]
After modifying any of the above files, activate the new settings with:
$ sudo ufw disable $ sudo ufw enableAny suggestions?

> **steeldriver said:**
> is the firewall enabled?

```
service ufw status
``` maybe that tool needs some ports opened in order to authenticate/run?

---

### Post by steeldriver on 2012-06-18
> **jaws222 said:**
> It looks like there was not a firewall program installed.  when I run service ufw status the response is **ufw start/running**.   I installed gufw but am not sure what would need opening.  I guess I  can experiment.  I found this guide here, not sure what port to try  though:

This means the ufw firewall program **is** installed and running - gufw is just a graphical interface for setting up rules (personally I find the terminal interface simpler).

You could start by verifying that ufw *is* the problem - it may not be - by stopping it temporarily and trying to authenticate:

```
sudo service ufw stop
```If it turns out to be that, then you have a few options e.g. (a) disable ufw permanently (shouldn't be an issue if you are already behind a NAT router / firewall) (b) enable it and look at the logs to figure out what ports it's trying to use (c) google for what open ports you application needs (d) contact TD and ask them

If you *do* have a firewall on your router you could start by looking at what ports were opened on *that*

Hope this helps

---

### Post by seaq on 2012-11-05
jaws222 I'm having the same issue.. you`re not alone ...

[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/839902](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/839902)

It seems a flash player issue, thou ...

---

### Post by seaq on 2012-11-05
effectively it's related to flash.

with the Shockwave Flash 11.5 r31 available in google chrome beta works as before.

---

