---
title: "startup script to disable bluetooth device(hci0) works;but,later enables itself!"
date: 2010-05-14
forum: General Help
---

### Post by deepclutch on 2010-05-14
Hi,

I've a custom startup script myscript.sh placed inside  /etc/init.d/ directory with below lines to disable usb bluetooth device "hci0".this happens on Ubuntu **Lucid**.
```
#!/bin/bash
echo "Disabling hci0 bluetooth usb dongle"

/usr/sbin/hciconfig hci0 down &

here is  the /var/log/daemon.log 

```

When I rebooted it worked fine disabling the bluetooth dongle.
but ,later on ,it gets enabled!I've lost it!
```
May 15 00:20:02 linbox bluetoothd[1539]: probe failed with driver input-headset for device /org/bluez/1537/hci0/dev_00_1F_DE_FE_7C_34
May 15 00:20:02 linbox bluetoothd[1539]: Adapter /org/bluez/1537/hci0 has been enabled
May 15 01:07:39 linbox bluetoothd[810]: probe failed with driver input-headset for device /org/bluez/752/hci0/dev_00_1F_DE_FE_7C_34
May 15 01:07:39 linbox bluetoothd[810]: Adapter /org/bluez/752/hci0 has been enabled
May 15 01:07:49 linbox bluetoothd[810]: Adapter /org/bluez/752/hci0 has been disabled
May 15 07:46:10 linbox bluetoothd[1452]: probe failed with driver input-headset for device /org/bluez/1450/hci0/dev_00_1F_DE_FE_7C_34
**May 15 07:46:10 linbox bluetoothd[1452]: Adapter /org/bluez/1450/hci0 has been enabled**
```

I used update-rc.d myscript S 26 2 3 4 5 .  to update symlinks.Is this the way?Any Other thing I missed?

Thanks.

---

### Post by NoBugs! on 2010-05-22
Looks like bluetoothd is reenabling it?
This may fix it:

```
sudo hciconfig hci0 down
sudo killall bluetoothd
sudo /etc/init.d/bluetooth stop
```

---

### Post by deepclutch on 2010-05-22
@NoBugs:Thank You.Will I Try to Put "killall /usr/sbin/bluetoothd &" to the init Script?

Yes,I put the command to kill bluetoothd and it worked!
EDIT:I ended up changing the priority a bit less for the script as udev(?) or some other scripts keep making hci0 to be enabled.
Now it is at 51(update-rc.d start 51 2 3 4 5 . )

Thanks Again

---

