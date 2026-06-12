---
title: "Samsung Freeform Help"
date: 2010-01-24
forum: General Help
---

### Post by amtobscene on 2010-01-24
So, I have this New Samsung Freeform phone and I want to add music files to it.
One problem. It's a Window's Cd. I have wine and have tried installing that and I got no where.
Is there any way around this issue?

---

### Post by blueshiftoverwatch on 2010-01-24
I have an LG Chocolate 3 that can't be accessed unless I install a Windows only driver. Why a company would do something like that I don't know. You would think they'd set it up so it'd show up as a USB mass storage device. But anyway, the only work around I found was to buy a microSD card and transfer my music onto the phone using that.

---

### Post by danastasio on 2010-01-24
did you try running the CD in WINE?

---

### Post by scruff on 2010-03-10
I just got one too and am having this problem, though I expect to have a solution soon. It's not a question of your install CD, its just a mass USB storage device, its that udev seems to bug out while scanning the device. 

I see this in dmesg:

```

root@sean-sullivan:/home/sean# dmesg

[176839.001237] usb 4-2: configuration #1 chosen from 1 choice
[176839.014489] scsi11 : SCSI emulation for USB Mass Storage devices
[176839.014754] usb-storage: device found at 25
[176839.014759] usb-storage: waiting for device to settle before scanning

```

I'm working on the solution now (instead of working like I should be ;) ) and will post back when I figure it out.

[EDIT] just FYI, you won't need that install CD - the linux kernel has support for usb storage, there's just something buggy about this device. It's *possible* that it's bugged out because this phone also charges while plugged into USB and some motherboards+linux might have issues with that combo.

---

### Post by scruff on 2010-03-10
In case anyone else is searching for answers, it seems there are a lot of people having issues with this type of device. Not just this phone in particular, but the Qualcomm usb interface it uses. 

lsusb shows:
Bus 004 Device 027: ID 05c6:1000 Qualcomm, Inc. 

If you google "05c6:1000" you'll see a lot of threads related to this.

---

### Post by scruff on 2010-03-10
Ok, so I think I found the solution. These devices *used* to work in Ubuntu without any help and hopefully will again with this bug report:  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/477031](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/477031)

It seems that "0x05c6:0x1000" (which is the {$vendorID}:{$productID}) is one single USB ID that is used for a bunch of different devices. Some of which are cellphones and some are wireless modems. The wireless modems require different options when udev brings them on board. So the fact that they are using one productID seems pretty stupid, but anyway...


The solution:
Unplug your phone from the machine.

As root, edit /lib/udev/rules.d/61-option-modem-modeswitch.rules 
and comment out this line:

```

ATTRS{idVendor}=="05c6", ATTRS{idProduct}=="1000", RUN+="modem-modeswitch -v 0x%s{idVendor} -p 0x%s{idProduct} -t option-zerocd"

```

Now, also as root: 

```

root@sean-sullivan:/home/sean# modprobe -r usb-storage
root@sean-sullivan:/home/sean# modprobe -v usb-storage option_zero_cd=2

```

Now try hooking the phone back up. If it doesn't work, please include the output of commands "lsusb" and "dmesg | tail -n20" in your response.


I'm still at work (and actually busy) and can't test right now, so if you try it, and it works, let me know!!

---

### Post by alerum68 on 2010-11-22
Been lurking on the form for years, and finally had to break the silence.

Sorry for bring up an old thread, but I think this one will get some more interest with the release of the Freeform II.  Had the same issue as the poster, and this fix worked perfectly.  Just wanted to respond and say that the issue is still around, and the fix is still working.

Thanks, and sorry the original poster didn't reply.


> **scruff said:**
> Ok, so I think I found the solution. These devices *used* to work in Ubuntu without any help and hopefully will again with this bug report:  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/477031](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/477031)

It seems that "0x05c6:0x1000" (which is the {$vendorID}:{$productID}) is one single USB ID that is used for a bunch of different devices. Some of which are cellphones and some are wireless modems. The wireless modems require different options when udev brings them on board. So the fact that they are using one productID seems pretty stupid, but anyway...


The solution:
Unplug your phone from the machine.

As root, edit /lib/udev/rules.d/61-option-modem-modeswitch.rules 
and comment out this line:

```

ATTRS{idVendor}=="05c6", ATTRS{idProduct}=="1000", RUN+="modem-modeswitch -v 0x%s{idVendor} -p 0x%s{idProduct} -t option-zerocd"

```Now, also as root: 

```

root@sean-sullivan:/home/sean# modprobe -r usb-storage
root@sean-sullivan:/home/sean# modprobe -v usb-storage option_zero_cd=2

```Now try hooking the phone back up. If it doesn't work, please include the output of commands "lsusb" and "dmesg | tail -n20" in your response.


I'm still at work (and actually busy) and can't test right now, so if you try it, and it works, let me know!!

---

### Post by scruff on 2010-11-22
Right on! Thanks for the confirmation!

---

### Post by mosr on 2010-12-30
So, I followed the instructions in the thread and nothing happened. So, here are the details from the  "lsusb" and "dmesg | tail -n20".

edit: I have a Samsung Freeform II.

```
justin@justin-desktop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 011: ID 04e8:6640 Samsung Electronics Co., Ltd Usb Modem Enumerator
Bus 003 Device 002: ID 046d:c03e Logitech, Inc. Premium Optical Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
justin@justin-desktop:~$ 

```and

```
justin@justin-desktop:~$ dmesg | tail -n20
[1473754.339737] ath5k phy0: noise floor calibration timeout (2457MHz)
[1473755.249553] ath5k phy0: noise floor calibration timeout (2462MHz)
[1473994.511005] ath5k phy0: noise floor calibration timeout (2462MHz)
[1474114.343154] ath5k phy0: noise floor calibration timeout (2462MHz)
[1474228.638560] ath5k phy0: noise floor calibration timeout (2412MHz)
[1474348.638528] ath5k phy0: noise floor calibration timeout (2412MHz)
[1474468.634600] ath5k phy0: noise floor calibration timeout (2412MHz)
[1474588.643216] ath5k phy0: noise floor calibration timeout (2412MHz)
[1474708.638764] ath5k phy0: noise floor calibration timeout (2412MHz)
[1474711.301907] ath5k phy0: noise floor calibration timeout (2432MHz)
[1474803.840060] usb 3-1: USB disconnect, address 10
[1474828.638917] ath5k phy0: noise floor calibration timeout (2412MHz)
[1474877.418054] usbcore: deregistering interface driver usb-storage
[1474881.652178] Initializing USB Mass Storage driver...
[1474881.652269] usbcore: registered new interface driver usb-storage
[1474881.659526] USB Mass Storage support registered.
[1474893.112045] usb 3-1: new full speed USB device using uhci_hcd and address 11
[1474893.276113] usb 3-1: configuration #1 chosen from 1 choice
[1474893.280183] cdc_acm 3-1:1.0: ttyACM0: USB ACM device
[1474948.638979] ath5k phy0: noise floor calibration timeout (2412MHz)
justin@justin-desktop:~$ 

```

---

### Post by scruff on 2011-01-02
Looks like your vendor/productID is different from mine and your output suggests udev is trying to bring it online as a modem. Search that same udev file for a line that matches yours: 04e8:6640 and comment that one out. Then reload the module as I showed before. 

God luck!

---

### Post by mosr on 2011-01-02
So, I spent a while looking through everything in the modemswitch.rules file and didn't see anything with either of the strings (04e8:6640) you mentioned. Any ideas of what I could do? It says not to add anything not made by Option NV, so I don't want to make one and stick it in there.

---

### Post by scruff on 2011-01-02
> **mosr said:**
> So, I spent a while looking through everything in the modemswitch.rules file and didn't see anything with either of the strings (04e8:6640) you mentioned. Any ideas of what I could do? It says not to add anything not made by Option NV, so I don't want to make one and stick it in there.

Yea, I don't see it either: 

```
[sean.bitwise: /home/sean]$ grep -i '04e8:6640' /lib/udev/rules.d/61-option-modem-modeswitch.rules
[sean.bitwise: /home/sean]$ 
```

But, I didn't read your dmesg carefully and it looks like it's actually recognized properly:
 
```
[1474881.652178] Initializing USB Mass Storage driver...
[1474881.652269] usbcore: registered new interface driver usb-storage
[1474881.659526] USB Mass Storage support registered.
[1474893.112045] usb 3-1: new full speed USB device using uhci_hcd and address 11
```

You sure you don't see an icon on your desktop for this device? Or something under "Places"?
[1474893.276113] usb 3-1: configuration #1 chosen from 1 choice

---

### Post by mosr on 2011-01-02
Yeah, I'm sure. There isn't anything happening on my computer with it visibly. I checked the phone settings to make sure it was set to mass storage, but still nothing.

edit: I don't see anything in "computer" either.

---

### Post by nolesce on 2011-02-14
New Samsung Freeform II
Not showing in places. Not seeing it anywhere.

LSUSB:
```

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 028: ID 05c6:1000 Qualcomm, Inc. 
Bus 001 Device 002: ID 04fc:05d8 Sunplus Technology Co., Ltd 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

Dmesg (last bit)
```

8
[1629324.612090] usb 1-2: configuration #1 chosen from 1 choice
[1629324.620951] scsi19 : SCSI emulation for USB Mass Storage devices
[1629324.621293] usb-storage: device found at 28
[1629324.621296] usb-storage: waiting for device to settle before scanning

```

---

