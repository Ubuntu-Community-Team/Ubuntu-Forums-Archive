---
title: "trying to get root script to run a command as normal user"
date: 2010-06-08
forum: General Help
---

### Post by maestrobwh1 on 2010-06-08
Because I have a flaky wireless device, I occasionally get a hung connection and this script gets things running again in just a few seconds except obviously the boldfaced item, as it still tries to run in the root directory and gives errors:

Configuration file "/root/.kde/share/config/knetworkmanagerrc" not writable.
Please contact your system administrator.

**So I am not sure how to get knetworkmanager to run as me, the user ubuntu in the /home/ubuntu directory**

#!/bin/bash
service network-manager stop
sleep 1
killall -9 knetworkmanager
ifconfig wlan0 down
rmmod r8192se_pci
sleep 1
rm /var/lib/NetworkManager/NetworkManager.state
modprobe r8192se_pci
ifconfig wlan0 up
service network-manager start
sleep 1
**sudo -u ubuntu knetworkmanager**
exit 0

---

### Post by dcstar on 2010-06-09
> **maestrobwh1 said:**
> Because I have a flaky wireless device, I occasionally get a hung connection and this script gets things running again in just a few seconds except obviously the boldfaced item, as it still tries to run in the root directory and gives errors:

Configuration file "/root/.kde/share/config/knetworkmanagerrc" not writable.
Please contact your system administrator.

**So I am not sure how to get knetworkmanager to run as me, the user ubuntu in the /home/ubuntu directory**

#!/bin/bash
service network-manager stop
sleep 1
killall -9 knetworkmanager
ifconfig wlan0 down
rmmod r8192se_pci
sleep 1
rm /var/lib/NetworkManager/NetworkManager.state
modprobe r8192se_pci
ifconfig wlan0 up
service network-manager start
sleep 1
**sudo -u ubuntu knetworkmanager**
exit 0

```
su -l
```

---

