---
title: "script not working.."
date: 2012-09-02
forum: General Help
---

### Post by ganga1234 on 2012-09-02
this is the script to disable ehci_hcd and restarting nm-applet..need help to get it work.

#!/bin/bash
cd /sys/bus/pci/drivers/ehci_hcd/
echo "user passwd" | sudo sh -c 'find ./ -name "0000:00:*" -print | sed "s/\.\///" > unbind'
echo "user passwd" | sudo restart network-manager
nm-applet

---

### Post by sisco311 on 2012-09-02
Please don't post the same thing in multiple locations:
[http://ubuntuforums.org/showthread.php?t=2051882](http://ubuntuforums.org/showthread.php?t=2051882)

Thread closed.

---

