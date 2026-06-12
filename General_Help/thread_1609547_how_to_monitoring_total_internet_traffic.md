---
title: "how to monitoring total internet traffic"
date: 2010-10-30
forum: General Help
---

### Post by Sysyphus Jones on 2010-10-30
Hi
I'm trying to find a way to monitor how much data is being downloaded in my ubuntu 10.04 system because of limitations set by my ISP.

The only PC connected is a laptop using wireless.

I'm trying to use NTM [http://netramon.sourceforge.net/eng/index.html](http://netramon.sourceforge.net/eng/index.html) which shows no network traffic with the default configuration of eth0

Given the wireless connection I guess that makes sense

So I've tried "lo" (loopback) as the interface, and this does  shows some traffic but nothing like the quantity of data that is actually being transferred.

I'm not sure what this is actually monitoring but typically its showing just a few bytes per second while my download manager is clearly fetching many times that.

I'm stuck and would appreciate either some suggestion on how to get NTM to monitor the full connection (there seems to be no documentation) or perhaps some other program to do this job

Thanks

---

### Post by CharlesA on 2010-10-30
Using ifconfig will show you how much data is sent or recieved.

However that resets after a reboot.

Check here: [http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html](http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html)

[http://www.cyberciti.biz/tips/keeping-a-log-of-daily-network-traffic-for-adsl-or-dedicated-remote-linux-box.html](http://www.cyberciti.biz/tips/keeping-a-log-of-daily-network-traffic-for-adsl-or-dedicated-remote-linux-box.html)

---

### Post by Sysyphus Jones on 2010-10-30
thanks for the reply

as a result I've set the NTM  interface to eth1 and the numbers now look more reasonable

---

