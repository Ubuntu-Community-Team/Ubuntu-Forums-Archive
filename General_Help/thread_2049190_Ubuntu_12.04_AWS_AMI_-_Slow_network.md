---
title: "Ubuntu 12.04 AWS AMI - Slow network"
date: 2012-08-28
forum: General Help
---

### Post by simonhawkins on 2012-08-28
All,

I have an Ubuntu 12.04 AWS (Amazon Web Services) AMI that is experiencing slow network transfer (I am using a c1.xlarge instance type). If i pscp up some files to the server I get a network speed of 10mbit. If I backup data from a Windows Server to the Ubuntu server I also get 10mbit. If I copy data from between Windows Servers (of the same instance type) i get 1gbit+. Does anyone know why?

If I use ethtool to investigate eth0 I get this:

Settings for eth0:         Link detected: yes  

And that's it.

If I try and force the speed to 1Gbps I get this:  

sudo /sbin/ethtool -s eth0 speed 1000 duplex full 

Cannot get current device settings: Operation not supported   not setting speed   not setting duplex  

The AMI I am using is 12.04 that is available on the quick start wizard if that helps. 

Does anyone have any ideas?

Simon

---

