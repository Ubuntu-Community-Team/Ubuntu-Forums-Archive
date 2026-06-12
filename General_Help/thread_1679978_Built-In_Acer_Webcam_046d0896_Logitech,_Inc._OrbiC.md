---
title: "Built-In Acer Webcam 046d:0896 Logitech, Inc. OrbiCam"
date: 2011-02-01
forum: General Help
---

### Post by Jackarow on 2011-02-01
Can not seem to get my built-in webcam working. I am looking for some assistance in troubleshooting. 

This is the output of **lsusb**:
```
Bus 001 Device 077: ID 046d:0896 Logitech, Inc. OrbiCam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Laptop is an Acer 5610 series.

---

### Post by bryanl on 2011-02-02
Look to see if you have /dev/video0

check dmesg and see if it reports a Linux video capture interface and registered a new interface driver uvcvideo and identifies your camera

Install cheese from the repository and see if it will display the webcam or, if you have VLC installed, tell it to capture from /dev/video0

this is one of those 'it should just work' sorta' things - so when it doesn't it can be a whole lot of a challenge.

---

### Post by Jackarow on 2011-02-03
> Look to see if you have /dev/video0

/dev/video0 does indeed exist.

> check dmesg and see if it reports a Linux video capture interface and registered a new interface driver uvcvideo and identifies your camera

I'll post all of the **dmesg**'s that may be of interest:
```

[   22.689343] Linux video capture interface: v2.00
[   22.698963] ACPI: EC: GPE storm detected, transactions will use polling mode
[   22.701373] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input5
[   22.701454] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   23.130151] usbcore: registered new interface driver uvcvideo
[   23.130156] USB Video Class driver (v0.1.0)
[   23.133982] gspca: main v2.9.0 registered
[   23.146454] gspca: probing 046d:0896
[   23.146458] vc032x: Sensor POxxxx
[   23.148494] gspca: video0 created
[   23.148537] usbcore: registered new interface driver vc032x
[   23.148542] vc032x: registered
[ 5899.811535] usb 1-4: USB disconnect, address 2
[ 5899.811641] gspca: video0 disconnect
[ 5899.811789] gspca: video0 released
[ 5900.148112] usb 1-4: new high speed USB device using ehci_hcd and address 3
[ 5900.324612] gspca: probing 046d:0896
[ 5900.324623] vc032x: Sensor POxxxx
[ 5900.326642] gspca: video0 created
[ 5931.237488] usb 1-4: USB disconnect, address 3
[ 5931.237590] gspca: video0 disconnect
[ 5931.237731] gspca: video0 released
[ 5933.016195] usb 1-4: new high speed USB device using ehci_hcd and address 4
[ 5933.192229] gspca: probing 046d:0896
[ 5933.192240] vc032x: Sensor POxxxx
[ 5933.194436] gspca: video0 created
[ 5986.860530] usb 1-4: USB disconnect, address 4
[ 5986.860637] gspca: video0 disconnect
[ 5986.860777] gspca: video0 released
[ 5987.164219] usb 1-4: new high speed USB device using ehci_hcd and address 5
[ 5987.340573] gspca: probing 046d:0896
[ 5987.340583] vc032x: Sensor POxxxx
[ 5987.342788] gspca: video0 created
[ 6033.055299] usb 1-4: USB disconnect, address 5
[ 6033.055406] gspca: video0 disconnect
[ 6033.055548] gspca: video0 released
[ 6033.324212] usb 1-4: new high speed USB device using ehci_hcd and address 6
[ 6033.392490] hub 1-0:1.0: unable to enumerate USB device on port 4
[ 6033.661219] usb 3-2: new full speed USB device using uhci_hcd and address 2
[ 6033.815234] usb 3-2: not running at top speed; connect to a high speed hub
[ 6033.869428] gspca: probing 046d:0896
[ 6033.869438] vc032x: Sensor POxxxx
[ 6033.875344] gspca: video0 created
[ 6036.240224] usb 3-2: USB disconnect, address 2
[ 6036.240329] gspca: video0 disconnect
[ 6036.240467] gspca: video0 released
[ 6036.512169] usb 1-4: new high speed USB device using ehci_hcd and address 7
[ 6036.688775] gspca: probing 046d:0896
[ 6036.688785] vc032x: Sensor POxxxx
[ 6036.690863] gspca: video0 created
[ 6037.576519] usb 1-4: USB disconnect, address 7
[ 6037.576622] gspca: video0 disconnect
[ 6037.576750] gspca: video0 released
[ 6037.944225] usb 1-4: new high speed USB device using ehci_hcd and address 8
[ 6038.120469] gspca: probing 046d:0896
[ 6038.120479] vc032x: Sensor POxxxx
[ 6038.122818] gspca: video0 created
[ 6109.406359] usb 1-4: USB disconnect, address 8
[ 6109.406468] gspca: video0 disconnect
[ 6109.406608] gspca: video0 released
[ 6132.661172] usb 1-4: new high speed USB device using ehci_hcd and address 9
[ 6132.836302] gspca: probing 046d:0896
[ 6132.836312] vc032x: Sensor POxxxx
[ 6132.838420] gspca: video0 created
[ 6134.193923] usb 1-4: USB disconnect, address 9
[ 6134.194030] gspca: video0 disconnect
[ 6134.194172] gspca: video0 released
[ 6151.912214] gspca: probing 046d:0896
[ 6151.912224] vc032x: Sensor POxxxx
[ 6151.914181] gspca: video0 created
[ 6152.243601] usb 1-4: USB disconnect, address 15
[ 6152.243708] gspca: video0 disconnect
[ 6152.243850] gspca: video0 released
[ 6244.996182] usb 1-4: new high speed USB device using ehci_hcd and address 16
[ 6245.172621] gspca: probing 046d:0896
[ 6245.172631] vc032x: Sensor POxxxx
[ 6245.174827] gspca: video0 created
[13329.639231] usb 1-4: USB disconnect, address 16
[13329.639338] gspca: video0 disconnect
[13329.639479] gspca: video0 released
[13329.908221] usb 1-4: new high speed USB device using ehci_hcd and address 17
[13330.084650] gspca: probing 046d:0896
[13330.084660] vc032x: Sensor POxxxx
[13330.086864] gspca: video0 created
[13757.067609] usb 1-4: USB disconnect, address 17
[13757.067715] gspca: video0 disconnect
[13757.067856] gspca: video0 released
[13757.404397] usb 1-4: new high speed USB device using ehci_hcd and address 18
[13757.563537] gspca: probing 0ac8:0321
[1207308.504171] usb 1-4: new high speed USB device using ehci_hcd and address 93
[1207308.680608] gspca: probing 046d:0896
[1207308.680619] vc032x: Sensor POxxxx
[1207308.682821] gspca: video0 created
[1207364.378585] usb 1-4: USB disconnect, address 93
[1207364.378691] gspca: video0 disconnect
[1207364.378838] gspca: video0 released
[1207369.952564] hub 1-0:1.0: unable to enumerate USB device on port 4
[1207370.196206] usb 1-4: new high speed USB device using ehci_hcd and address 95
[1207370.372539] gspca: probing 046d:0896
[1207370.372549] vc032x: Sensor POxxxx
[1207370.374862] gspca: video0 created
[1207396.966956] usb 1-4: USB disconnect, address 95
[1207396.967062] gspca: video0 disconnect
[1207396.967210] gspca: video0 released
[1207397.236205] usb 1-4: new high speed USB device using ehci_hcd and address 96
[1207397.412529] gspca: probing 046d:0896
[1207397.412539] vc032x: Sensor POxxxx
[1207397.419244] gspca: video0 created

```

Appears I have some sort of error occurring. Is it due to the presence of uvcvideo and gspca? Would unloading one of these modules via **modprobe -r <module>** be effective?

> Install cheese from the repository and see if it will display the webcam or, if you have VLC installed, tell it to capture from /dev/video0

Neither Cheese nor VLC were about to produce a video stream. It is worth noting that I do recall using cheese with success on this machine in the past. However, I don not recall how I got it to work.

Now that we have a starting point, I am hoping that forums users will continue to provide incite into my dilemma. 

Thankyou

---

