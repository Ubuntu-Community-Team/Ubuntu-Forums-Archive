---
title: "no Bluetooth on resume"
date: 2009-07-30
forum: General Help
---

### Post by yopnono on 2009-07-30
Ok if I put my laptop to sleep and resume, then the BT adapter is not found by the system.

Have found that the only way to make it work is to either reboot or restart the BT from the services-admin.

So is the any shell cmd that I can use, that are the same as the services-admin run? 

Running Hardy 
Logitec BT adapter.
Bus 003 Device 021: ID 046d:c709 Logitech, Inc. BT Mini-Receiver (HCI mode)


Have tried:
invoke-rc.d bluetooth restart
hciconfig hci0 reset

---

