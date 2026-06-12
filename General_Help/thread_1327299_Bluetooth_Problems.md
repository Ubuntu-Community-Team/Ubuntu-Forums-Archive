---
title: "Bluetooth Problems"
date: 2009-11-15
forum: General Help
---

### Post by Vishesh on 2009-11-15
I recently bought a Bluetooth dongle for my desktop and after plugging it in it worked great (via blueman & kbluetooth) but then I had the great idea that I'll switch it off for some while since I'm not using it. I switched it off with the pop-up menu of blueman which comes when you right click on the icon.

I've tried everything and I can't seem to get it to work. (Even tried re-starting the comp)


```
vishesh@vishesh-desktop:~$ sudo /etc/init.d/bluetooth status
[sudo] password for vishesh:
 * bluetooth is running
vishesh@vishesh-desktop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 1131:1001 Integrated System Solution Corp. KY-BT100 Bluetooth Adapter
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
vishesh@vishesh-desktop:~$ rfkill list
1: hci0: Bluetooth
        Soft blocked: yes
        Hard blocked: no

```

For some reason it gets soft blocked occasionally. Does anyone know what that means? It doesn't show any error if I unblock it.

hcitool doesn't seem to help. It's seem as though it isn't detecting it.
```
vishesh@vishesh-desktop:~$ hcitool dev
Devices:
vishesh@vishesh-desktop:~$ hcitool scan
Device is not available: No such device

```

On running blueman-mananger, I get a request timed out operation while trying to enable bluetooth, and kbluetooth gives me a very long error, which I'm posting below.
```
vishesh@vishesh-desktop:~$ kbluetooth
QDBusObjectPath: invalid path ""
QDBusObjectPath: invalid path ""
process 22563: arguments to dbus_message_new_method_call() were incorrect, assertion "path != NULL" failed in file dbus-message.c line 1074.
This is normally a bug in some application using the D-Bus library.
QDBusConnection: error: could not send message to service "org.bluez" path "" interface "org.bluez.Adapter" member "GetProperties"
process 22563: arguments to dbus_message_new_method_call() were incorrect, assertion "path != NULL" failed in file dbus-message.c line 1074.
This is normally a bug in some application using the D-Bus library.
QDBusConnection: error: could not send message to service "org.bluez" path "" interface "org.bluez.Adapter" member "RegisterAgent"
AGENT registered !
process 22563: arguments to dbus_message_new_method_call() were incorrect, assertion "path != NULL" failed in file dbus-message.c line 1074.
This is normally a bug in some application using the D-Bus library.
QDBusConnection: error: could not send message to service "org.bluez" path "" interface "org.bluez.Adapter" member "GetProperties"
<unknown program name>(22562)/: Communication problem with  "kbluetooth" , it probably crashed.
Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken." "

```

Does anyone have any idea whats wrong? I've tried looking for a solution for quite some time now, but I can't seem to find anything. :-(

EDIT : This is what my hciconfig says
```
vishesh@vishesh-desktop:~$ hciconfig -a
hci0:   Type: USB
        BD Address: 22:22:22:22:22:22 ACL MTU: 678:8 SCO MTU: 48:10
        DOWN
        RX bytes:684 acl:0 sco:0 events:21 errors:0
        TX bytes:88 acl:0 sco:0 commands:29 errors:8
        Features: 0xbf 0xfe 0x8d 0x78 0x08 0x18 0x00 0x00
        Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3
        Link policy: RSWITCH HOLD SNIFF PARK
        Link mode: SLAVE ACCEPT

```

---

### Post by Vishesh on 2009-11-15
Bump!

I checked KSystemlog and this is what I get - 
```
Today 23:06:28	vishesh-desktop	bluetoothd[9633]	HCI dev 0 registered
Today 23:06:28	vishesh-desktop	bluetoothd[9633]	HCI dev 0 up
Today 23:06:28	vishesh-desktop	bluetoothd[9633]	Starting security manager 0
Today 23:06:28	vishesh-desktop	bluetoothd[9633]	Parsing /etc/bluetooth/serial.conf failed: No such file or directory
Today 23:06:28	vishesh-desktop	bluetoothd[9633]	probe failed with driver input-headset for device /org/bluez/9607/hci0/dev_00_21_08_61_7F_6F
Today 23:06:28	vishesh-desktop	bluetoothd[9633]	Adapter /org/bluez/9607/hci0 has been enabled
Today 23:06:28	vishesh-desktop	bluetoothd[9633]	Stopping security manager 0
Today 23:06:28	vishesh-desktop	bluetoothd[9633]	HCI dev 0 down
Today 23:06:28	vishesh-desktop	bluetoothd[9633]	Adapter /org/bluez/9607/hci0 has been disabled

```

It enables then disables itself. Weird. I think I'll boot in from a live-cd and test it out in the morning. Or maybe someone would know how to fix it till then.

---

### Post by walmis on 2009-11-16
Which version of blueman do you have?

---

### Post by Vishesh on 2009-11-16
> **walmis said:**
> Which version of blueman do you have?
I had 1.0 something earlier, then I added the new repository and upgraded. Now I'm using 1.21. I don't really think it's an issue with blueman cause even **hcitool** doesn't seem to detect it.

---

### Post by Vishesh on 2009-11-16
I booted in from a live-CD and plugged in the Bluetooth dongle. It worked perfectly. After that I rebooted into my system, and guess what? It still didn't work! :-(

I even tried purging my system of Bluetooth and reinstalling it, but it didn't really help.
```

sudo aptitude purge bluez bluez-utils bluetooth kdebluetooth
sudo aptitude install bluez bluez-utils bluetooth kdebluetooth
``` 

Now, I really have absolutely no idea what I can do. It can't be a bug in the kernel cause the live-CD is using the same kernel (2.6.31-14--generic). 

Does anyone have any idea what all files are responsible for Bluetooth? That way I can purge them and try reinstalling.

---

### Post by Vishesh on 2009-11-17
Bump!

I've tried re-installing libbluetooth as well. But it still isn't working. For some reason the moment it registers itself it encounters a parsing error for a file ( /etc/bluetooth/serial.conf ) which is not supposed to exist. A probe fails, and then it deactivates itself.
Does anyone have any idea?

Maybe I should file a bug report...

```
Today 18:23:27	vishesh-desktop	kernel	[ 1211.108023] usb 3-1: new full speed USB device using uhci_hcd and address 5
Today 18:23:27	vishesh-desktop	kernel	[ 1211.263361] usb 3-1: configuration #1 chosen from 1 choice
Today 18:23:27	vishesh-desktop	bluetoothd[27325]	HCI dev 0 registered
Today 18:23:27	vishesh-desktop	bluetoothd[27325]	HCI dev 0 up
Today 18:23:27	vishesh-desktop	bluetoothd[27325]	Starting security manager 0
Today 18:23:27	vishesh-desktop	bluetoothd[27325]	Parsing /etc/bluetooth/serial.conf failed: No such file or directory
Today 18:23:27	vishesh-desktop	bluetoothd[27325]	probe failed with driver input-headset for device /org/bluez/27324/hci0/dev_00_21_08_61_7F_6F
Today 18:23:28	vishesh-desktop	bluetoothd[27325]	Adapter /org/bluez/27324/hci0 has been enabled
Today 18:23:28	vishesh-desktop	bluetoothd[27325]	Stopping security manager 0
Today 18:23:28	vishesh-desktop	bluetoothd[27325]	HCI dev 0 down
Today 18:23:28	vishesh-desktop	bluetoothd[27325]	Adapter /org/bluez/27324/hci0 has been disabled

```

---

### Post by walmis on 2009-11-17
What do you get from rfkill list?
maybe try sudo rfkill unblock bluetooth

---

### Post by Vishesh on 2009-11-17
It mostly shows 
```
3: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no

```
but sometimes it's Soft blocked. But even then unblocking it really doesn't help. :-(

---

### Post by letterman on 2009-11-17
I'm using the latest version on Kubuntu 9.10 and when my mouse tries to connect it asks me if I want to trust, and I click trust and it doesn't connect but a minute later the same popup appears.. I click trust always and repeat the entire process. FIX: Go into device manager it may list the device as always trusted it may list the device as connceted.. but it is not. click NEW it will list the device, and using this will connect the device. However if it times out and tries to reconnect, it needs to be removed from devices, and re added using this method. There is something definitely wrong. Will file bug report.

---

### Post by Vishesh on 2009-12-21
I managed to solve it. 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/281949](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/281949)

```

sudo rmmod btusb && sudo modprobe btusb reset=1

```

Damn, I'd even filled a bug report.

---

