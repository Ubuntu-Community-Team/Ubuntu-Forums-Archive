---
title: "Bluetooth keyboard disconnects upon screensaver"
date: 2011-09-28
forum: General Help
---

### Post by malaeum on 2011-09-28
Hello everyone,

I picked up an HP TouchPad Wireless Keyboard recently and have begun using it on my desktop running Ubuntu 11.04. I have a few major issues that seem to prevent me from using this keyboard exclusively that I would like to solve and I believe that they pertain to any bluetooth keyboard, not just this specific device.

1. Whenever the screensaver is engaged, my bluetooth keyboard is disconnected. I have to use my USB keyboard (which is at the end of its life) to enter my password and then I have to click on the bluetooth icon in the system tray and manually reconnect to the bluetooth keyboard. 

2. When logging in with GDM, the bluetooth connection has not yet been established and I have to again use my USB keyboard. I would like to have the bluetooth connection established automatically during the boot procedure. 

I have found references to workarounds for these issues on the internet but they refer to modifying /etc/default/bluetooth, however on my system this file does not exist. I have created it and added the following to the file

[INDENT]HIDD_ENABLED=1
HIDD_OPTIONS="--master --connect 90:7F:61:80:31:04 --server"[/INDENT]

This doesn't seem to have solved my issue and I am struggling to find an original copy of the file. I see now that bluetooth is handled my udev, perhaps this file became obsolete then? I am not entirely sure how everything interacts.

I figure there has to be a known workaround for this issue, bluetooth keyboards are not that uncommon these days.

Thank you in advance for any and all help,
Matt

---

### Post by lightwarrior on 2011-09-28
Try this:

Ubuntu 11.04 Install via the command line  (excerpt from [https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup) )

sudo apt-get install bluez python-gobject python-dbus
python-gobject and python-dbus are needed for the python scripts bluez-simple-agent and bluez-test-device to work.

Discover the hciX location of the dongle with:

hcitool dev

Devices:
        hci0    00:11:95:00:1A:CF
 Your Bluetooth device will have a different id.

sudo bluez-simple-agent hci0 XX:XX:XX:XX:XX:XX
XX:XX:XX:XX:XX:XX is the MAC or BT ADD or BlueTooth Address of the bt device. Press the reset or pair button on your keyboard, simple-agent will ask to specify a pin like 1111, then type that pin on the bt keyboard and your bt keyboard is paired.

sudo bluez-test-device trusted XX:XX:XX:XX:XX:XX yes
To set the device as trusted

#sudo /etc/init.d/bluetooth restart
To restart the bluetooth daemon.

Check if the device is added:

dmesg|tail
The last lines will list your device.

Found the method for 10.04 and 11.04 here: [http://www.spinics.net/lists/linux-bluetooth/msg13445.html](http://www.spinics.net/lists/linux-bluetooth/msg13445.html)

---

### Post by malaeum on 2011-09-28
In trying to follow the method you laid out, I get the following error:
```
sudo bluez-simple-agent hci0 00:11:67:D6:01:07
Release
Creating device failed: org.bluez.Error.ConnectionAttemptFailed: Page Timeout
```

Just to be clear, the keyboard is connected and works fine now (I am typing on it). I believe that these instructions are simply to add/trust the device. It is already added and trusted. It seems that part of the gnome-screensaver initialization is to disconnect bluetooth devices. I want to override this functionality.

Thanks for the suggestion and let me know if I am misunderstanding something. 

Cheers

---

### Post by brAzzi64 on 2011-11-18
Hey!

I'm thinking about buying this keyboard and I want to make sure it'll work in my Ubuntu installation. Did you have any luck, finally?

Thx!

---

