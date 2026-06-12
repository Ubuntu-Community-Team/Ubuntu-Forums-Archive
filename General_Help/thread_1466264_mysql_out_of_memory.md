---
title: "mysql out of memory"
date: 2010-04-30
forum: General Help
---

### Post by gabrie on 2010-04-30
Hi

Few months ago I downloaded a Turnkey virtual appliance with Wordpress pre-installed. I used this as a VM on my laptop and configured it. Then when everything looked good, I transfered it to my hosting provider (which is the company I work for) and they put the VM on ESX and connected it to the internet.

Now I'm running into the issue that sometimes quite often and sometimes not for a week or so, the VM will hang. When looking outside of the VM you can see it is taking up all cpu resources available and on the console there is the following error message:

[1052409.181756] Out of memory: Kill process 8811 (mysqld) score 37029 or a child.
[1052409.181919] Killed process 8811 (mysqld)

Strange thing is that when looking at the VM memory usage, it uses less than 300 MB (from a VMware perspective). Only thing that I can do then is reset the VM (hard reboot).

After reboot I can see that Ubuntu (which is running in the VM) is using only 300MB out of 1024MB. 

I tarred all logfiles from /var/log and downloaded them but I don't know where to start looking for. I also did an update using:

apt-get update
apt-get upgrade
apt-get distr-upgrade

After the update all is running, but of course I have no idea how long it will run without issues. 

Can someone point me in the direction I start looking? Which logs are important. Can I monitor / log mysql memory usage? How to see which queries are giving me issues or taking up memory? Maybe it isn't mysql at all. Really don't know.

Some info:
- Linux wordpress 2.6.24-27-virtual
- Ubuntu 8.04.4 LTS
- mysql  Ver 14.12 Distrib 5.0.51a, for debian-linux-gnu (i486) using readline 5.2


Screenshot of the error:

[IMG]http://farm4.static.flickr.com/3643/4565290976_14632ece31_d.jpg[/IMG]

Regards
Gabrie

---

### Post by indytim on 2010-04-30
Are you running a php script when the memory issue surfaces (check the cron's also)?

IndyTim / DataMan

---

### Post by gabrie on 2010-04-30
> **indytim said:**
> Are you running a php script when the memory issue surfaces (check the cron's also)?

IndyTim / DataMan

I have no phpscripts scheduled in crontab.

On a daily basis, crontab will run:
apache2
apt
bsdmainutils
man-db
ntp
standard
sysklogd

---

