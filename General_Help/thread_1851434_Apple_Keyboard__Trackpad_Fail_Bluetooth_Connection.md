---
title: "Apple Keyboard / Trackpad Fail Bluetooth Connection (11.04)"
date: 2011-09-28
forum: General Help
---

### Post by ahhughes on 2011-09-28
Hi All,

First time poster... I am running Mythbuntu, but apparently this is Ubuntu 11.04:

[FONT="Courier New"]$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	**Ubuntu 11.04**
Release:	11.04
Codename:	natty[/FONT]

I have been following [the official guide]("https://help.ubuntu.com/community/BluetoothSetup#Ubuntu_11.04_Install_via_the_command_line") with limited success to install an apple magic trackpad and slim keyboard.

I can see the dongle:
[FONT="Courier New"]$ hcitool dev
Devices:
	hci0	00:1A:7D:XX:XX:XX[/FONT]

I can scan for the trackpad/keyboard:
[FONT="Courier New"]$ hcitool scan
Scanning ...
	40:30:04:0D:F0:XX	Apple Wireless Keyboard
	70:CD:60:FE:39:XX	Apple Wireless Trackpad[/FONT]

...from this point forward I will just deal with the Keyboard...

Then I can add the bluetooth device

[FONT="Courier New"]$ sudo bluez-simple-agent hci0 40:30:04:0D:F0:XX
RequestPinCode (/org/bluez/4527/hci0/dev_40_30_04_0D_F0_XX)
Enter PIN Code: 1234
Release  <----PIN Code + Return hit on keyboard. So this passes!
New device (/org/bluez/4527/hci0/dev_40_30_04_0D_F0_XX)[/FONT]

Then I can set the device to be trusted (without error)
[FONT="Courier New"]$ sudo bluez-test-device trusted 40:30:04:0D:F0:XX yes[/FONT] *<--- has not output.*

Restart Bluetooth
[FONT="Courier New"]$ sudo /etc/init.d/bluetooth restart
 * Stopping bluetooth                                                    [ OK ] 
 * Starting bluetooth                                                    [ OK ] 
[/FONT]

Now the problems start.
[LIST]
[*]dmesg|tail is supposed to show me the devices was added. I see nothing to suggest this.
[*]gnome-bluetooth `bluetooth-properties` lists the keyboard (and trackpad) as a known device(s).
[*]gnome-bluetooth `bluetooth-properties` can see the device(s) and says 'disconnected'.
[*]gnome-bluetooth gives me the option to connect, when I do this, it connects for a ~10sec then reports 'disconnected' again. No logs, no error e.t.c.
[/LIST]

I can't find any logs as to what might be going wrong here. Considering Im a bit out of touch with ubuntu now days I'm pretty much up the creek right now. So anyone who can help me, I'd be very greatful :)

---

### Post by ahhughes on 2011-09-30
UPDATE: Still NOT Fixed

For some reason after several reboots and running the exact same commands cut/pasted from above the keyboard worked! However, as soon as I tried to add the trackpad the keyboard stopped working, and the trackpad does not connect (without error as descibed above).

Could the trackpad have the ability to crash/disconnect the keyboard? It would appear to be the case :'( Someone can hopefully help me diagnose what might be going one, because right now I have no logs, no errors and thus no visibility.

Cheers in advance :)

---

### Post by ahhughes on 2011-09-30
UPDATE: Still not fixed.

Seems as tho the trackpad was connecting, but would only react to a click. Until installing the latest uTouch, then Touchegg. Now it appears to operate with as a normal mouse, with two finger srolling. So still not fully functional.

BUT: The trackpad still disconnects the keyboard and vice versa. I can only have one functioning at any time :'(

---

### Post by ahhughes on 2011-12-04
> **ahhughes said:**
> UPDATE: Still not fixed.

Seems as tho the trackpad was connecting, but would only react to a click. Until installing the latest uTouch, then Touchegg. Now it appears to operate with as a normal mouse, with two finger srolling. So still not fully functional.

BUT: The trackpad still disconnects the keyboard and vice versa. I can only have one functioning at any time :'(

I tried a new usb bluetooth dongle, both work concurrently. Be warned, this bluetooth dongle has trouble > 3 meters!

[http://www.dealextreme.com/p/super-mini-bluetooth-2-0-adapter-dongle-vista-compatible-11866]("http://www.dealextreme.com/p/super-mini-bluetooth-2-0-adapter-dongle-vista-compatible-11866")

Touchegg is still not working like a native apple trackpad tho (but it looks promising). :)

---

