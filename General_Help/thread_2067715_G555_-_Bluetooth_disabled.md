---
title: "G555 - Bluetooth disabled"
date: 2012-10-07
forum: General Help
---

### Post by Nico-dk on 2012-10-07
I'm running Ubuntu 12.04 (clean install) on a Lenovo G555, and since day one bluetooth has been sketchy.

If I click the bluetooth icon from the top panel, I only have 3 options:
Bluetooth: on
Turn off bluetooth
bluetooth settings

Turning BT on switches the panel icon from gray to white, indicating BT is on, but going into Bluetooth settings reveal that is not the case. See scrshot
Turning on BT from settings reverts back to off.

On a few occassions bluetooth has worked as expected. Lots of options from the top panel icon. This seem to only happen, if the laptop is brough back from suspension after disuse.

```
rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

```
dmesg | grep -i bluetooth
[   20.893842] Bluetooth: Core ver 2.16
[   20.893862] Bluetooth: HCI device and connection manager initialized
[   20.893866] Bluetooth: HCI socket layer initialized
[   20.893868] Bluetooth: L2CAP socket layer initialized
[   20.893873] Bluetooth: SCO socket layer initialized
[   20.894290] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   26.157810] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   26.157815] Bluetooth: BNEP filters: protocol multicast
[   26.196447] Bluetooth: RFCOMM TTY layer initialized
[   26.196454] Bluetooth: RFCOMM socket layer initialized
[   26.196456] Bluetooth: RFCOMM ver 1.11
```

Any and all help appreciated

---

### Post by Nico-dk on 2012-10-08
No fix, but for anyone reading this in the future, here's a workaround

1) turn BT off
2) suspend your computer
3) bring it back
4) turn on BT

---

### Post by blz on 2013-10-02
Omg.. that actually worked! Isn't there a way to do that with a script without suspending the machine?

---

### Post by blz on 2013-10-02
Ok, here's what worked for me (*in Ubuntu 13.04 x64 with latest upgrades (on 03.10.2013), Lenovo Y510P*):

> sudo rmmod btusb
sudo modprobe btusb

I've added a script to do that at Ubuntu's start and it lets the bluetooth to automatically detect my mouse.
I don't have blueman installed. Nor any of the "bluetooth" results in the Software Center. (Even Bluetooth Support is not installed.)

Here are the packages I have *currently installed*:
> $ dpkg --get-selections | grep -v deinstall | grep blue

bluez						install
bluez-compat					install
bluez-cups					install
bluez-hcidump					install
bluez-tools					install
libbluetooth3:amd64				install
libgnome-bluetooth11				install
pulseaudio-module-bluetooth			install
python-bluez					install


**Source:** [http://ubuntuforums.org/showthread.php?t=1387211](http://ubuntuforums.org/showthread.php?t=1387211)

---

