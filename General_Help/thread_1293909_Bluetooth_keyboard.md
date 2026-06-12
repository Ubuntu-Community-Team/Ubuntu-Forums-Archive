---
title: "Bluetooth keyboard"
date: 2009-10-17
forum: General Help
---

### Post by cpdondo on 2009-10-17
I'm trying to set up a bluetooth keyboard.  I can get it to associate with hidd --search and from there on it works fine.  But I need it to associate at boot so I don't have to ssh into the box to get the keyboard working.  I've built the latest bluetooth (4.52) as was suggested elsewhere; no difference.  The keyboard is seen, it's just disconnected as soon as you quit typing.

bluetoothd[3977]: Adapter /org/bluez/3977/hci0 has been enabled
bluetoothd[3977]: Computer is classified as desktop
bluetoothd[3977]: Setting 0x000104 for major/minor device class
bluetoothd[3977]: adapter_get_device(B9:82:09:07:08:AF)
bluetoothd[3977]: adapter_create_device(B9:82:09:07:08:AF)
bluetoothd[3977]: Creating device /org/bluez/3977/hci0/dev_B9_82_09_07_08_AF
bluetoothd[3977]: btd_device_ref(0xb8865068): ref=1
bluetoothd[3977]: Incoming connection on PSM 17
bluetoothd[3977]: Removing temporary device /org/bluez/3977/hci0/dev_B9_82_09_07_08_AF
bluetoothd[3977]: Removing device /org/bluez/3977/hci0/dev_B9_82_09_07_08_AF
bluetoothd[3977]: btd_device_unref(0xb8865068): ref=0
bluetoothd[3977]: device_free(0xb8865068)

How do I get it to stick and to act like a keyboard?

---

