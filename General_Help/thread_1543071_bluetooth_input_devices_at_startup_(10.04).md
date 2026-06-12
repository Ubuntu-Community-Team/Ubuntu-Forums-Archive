---
title: "bluetooth input devices at startup (10.04)"
date: 2010-07-31
forum: General Help
---

### Post by bobismeyep on 2010-07-31
Hello,

I have a bluetooth keyboard and mouse that I want to connect at startup; however, after following the Ubuntu Guide [here]("https://help.ubuntu.com/community/BluetoothSetup") and searching various other places, I cannot connect at startup.  My problem appears to come from the fact that I don't have any of these files:
[LIST]
[*]/etc/default/bluetooth
[*]/etc/bluetooth/hcid.conf (found at [http://ubuntuforums.org/showthread.php?t=594624]("http://ubuntuforums.org/showthread.php?t=594624"))
[/LIST]

I can connect to a bluetooth device via KBluetooth and by doing:
```
$ sudo hidd --connect aa:bb:cc:dd:ee:ff
```
but I dont' want to have to have a cable connected keyboard to log in and go back to KBluetooth to connect.

Thanks for the help!

---

