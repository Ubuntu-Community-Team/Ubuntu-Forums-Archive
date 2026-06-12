---
title: "wlan-ng and gtkwifi-problems"
date: 2006-05-07
forum: General Help
---

### Post by wangdang on 2006-05-07
Hiya!

i just found the gtkwifi app, it works brilliantly with my one wifi nic that uses a ndiswrapper driver....but it doesnt seem to be able to use my nic that uses the wlan-ng driver.

The wlan-ng card (DLINK DWL-122)works flawlessly in airsnort and kismet though

---

### Post by wangdang on 2006-05-07
solved :)

i just had to sudo rmmod the prism2_usb module and reconnect it...apparently something was amiss...it just works dandy now :)

---

