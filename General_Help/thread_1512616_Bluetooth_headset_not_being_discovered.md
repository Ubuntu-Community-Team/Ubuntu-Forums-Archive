---
title: "Bluetooth headset not being discovered"
date: 2010-06-18
forum: General Help
---

### Post by Joe of loath on 2010-06-18
Hi there

I bought a bluetooth headset off ebay for skype. So far I've got it working in Ubuntu ONCE. I know I'm using the right technique to pair it to my laptop, as I can connect it in windows 7, but can't figure out how to use it there... (great job on usability Ubuntu community! You're way better than Microsoft.)

Using "sudo hcitool scan" In the terminal gives me:
```

joe@joe-laptop:~$ sudo hcitool scan
[sudo] password for joe: 
Scanning ...
	XX:XX:XX:XX:XX:XX (edited)	WEP200

```

That's the device, as that's what the manual says the name should be. However, the bluetooth manager only found it the first time, after which I connected, then tested the range and it wouldn't reconnect. After a couple of reboots it still doesn't work, no matter which order I try (dongle in then headset on, headset on then dongle in, reboot with dongle out, reboot with dongle in)

This is what lsusb says about my adaptor:
```
Bus 007 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)

```

Anyone know what's happening? It's a software problem, connecting to my mobile hasn't always worked either.

Thanks in advance
Joe

EDIT: Just my luck, seconds after I post the thread I get it working >.>

To anyone googling, I simply turned the headset on with the bluetooth on already, and it asked to pair. Not sure what was up with it...

---

