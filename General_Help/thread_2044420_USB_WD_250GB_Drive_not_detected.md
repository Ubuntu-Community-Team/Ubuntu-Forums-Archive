---
title: "USB WD 250GB Drive not detected"
date: 2012-08-19
forum: General Help
---

### Post by dantheman1261 on 2012-08-19
Hi,

A few days ago my WD 250GB external hdd stopped working. Up to that point there were no issues, simply unplugged from one computer, plugged into the next, and Ubuntu doesn't detect it (also tried in Windows and on other systems with no luck).

Output from 'dmesg | tail' : 
```

[  713.506966] usb 3-2: device not accepting address 11, error -71
[  713.618855] usb 3-2: new full-speed USB device number 12 using xhci_hcd
[  713.619024] usb 3-2: Device not responding to set address.
[  713.822885] usb 3-2: Device not responding to set address.
[  714.026514] usb 3-2: device not accepting address 12, error -71
[  714.138337] usb 3-2: new full-speed USB device number 13 using xhci_hcd
[  714.138504] usb 3-2: Device not responding to set address.
[  714.342292] usb 3-2: Device not responding to set address.
[  714.545986] usb 3-2: device not accepting address 13, error -71
[  714.546010] hub 3-0:1.0: unable to enumerate USB device on port 2

```

Output from 'lsusb':
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub

```

I appreciate that this might be the end of the close relationship between me and my data - thanks in advance for any help.

---

### Post by 2F4U on 2012-08-19
If it works on none of the systems you tried, chances are that the devices is damaged. Does it have an external power supply? If yes, maybe just this doesn't work. Have tried using a different USB cable?

---

### Post by Habitual on 2012-08-19
I had a similar issue, that sort of got resolved by WD support sending me a firmware upgrade for my device.

I still can't boot with it plugged in (non-bootable and NOT in boot order in BIOS), but at least now I can read/write my device.

---

### Post by dantheman1261 on 2012-08-20
> **2F4U said:**
> If it works on none of the systems you tried, chances are that the devices is damaged. Does it have an external power supply? If yes, maybe just this doesn't work. Have tried using a different USB cable?

No external power supply, and I've tried a few different cables :( - could you give me any hints on what the return of "dmesg | tail" is saying about the drive? Specifically, does "not responding to set address" give any information about what might have gone wrong?

> **Habitual said:**
> I had a similar issue, that sort of got resolved by WD support sending me a firmware upgrade for my device.

I still can't boot with it plugged in (non-bootable and NOT in boot order in BIOS), but at least now I can read/write my device.

Hopefully that might be the case here! Did you just email WD? If so, I'll certainly give it a go. As long as I can get the data off it I'll be over the moon.

Thanks for the help

---

### Post by Habitual on 2012-08-20
Dan...

I first went to [https://westerndigital.secure.force.com/a01/o](https://westerndigital.secure.force.com/a01/o) and created an account.
Then I used the this link...
[http://websupport.wdc.com/rdsfdc.asp?linktype=directemail&portaltype=wd&custtype=end&fs=&ss=&lang=en](http://websupport.wdc.com/rdsfdc.asp?linktype=directemail&portaltype=wd&custtype=end&fs=&ss=&lang=en)

Good Luck.

"simply unplugged from one computer, plugged into the next" uh, did you **safely** eject/remove it from the 1st system? "This device is now safe to remove" or similar...

---

### Post by dantheman1261 on 2012-08-21
> **Habitual said:**
> 
"simply unplugged from one computer, plugged into the next" uh, did you **safely** eject/remove it from the 1st system? "This device is now safe to remove" or similar...

I honestly can't remember. I try to do it whenever possible (though if I remember rightly, it's 'optimized for quick removal' or whatever Microsoft call it) but there's certainly a chance that I just pulled it out.

> **Habitual said:**
> Dan...

I first went to [https://westerndigital.secure.force.com/a01/o](https://westerndigital.secure.force.com/a01/o) and created an account.
Then I used the this link...
[http://websupport.wdc.com/rdsfdc.asp?linktype=directemail&portaltype=wd&custtype=end&fs=&ss=&lang=en](http://websupport.wdc.com/rdsfdc.asp?linktype=directemail&portaltype=wd&custtype=end&fs=&ss=&lang=en)

Good Luck.


Thanks! I'll certainly give that a go!

---

