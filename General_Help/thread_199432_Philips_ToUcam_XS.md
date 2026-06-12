---
title: "Philips ToUcam XS"
date: 2006-06-18
forum: General Help
---

### Post by marcozs on 2006-06-18
Hi guys, I have a problem with my webcam, a Philips ToUcam XS. I learned in different forums that I should compile and load the pwc driver and I did, but it seems that Ubuntu tries to load the ov51x driver as well. I get this doing a dmesg:
```

[17180418.560000] pwc Philips webcam module version 10.0.6-unofficial loaded.
[17180418.560000] pwc Supports Philips PCA645/646, PCVC675/680/690, PCVC720[40]/730/740/750 & PCVC830/840.
[17180418.560000] pwc Also supports the Askey VC010, various Logitech Quickcams, Samsung MPC-C10 and MPC-C30,
[17180418.560000] pwc the Creative WebCam 5 & Pro Ex, SOTEC Afina Eye and Visionite VCS-UC300 and VCS-UM100.
[17180418.560000] pwc Trace options: 0x00a1
[17180418.560000] usbcore: registered new driver Philips webcam
[17180432.312000] usb 2-2: USB disconnect, address 3
[17180437.404000] usb 2-2: new full speed USB device using ohci_hcd and address 4
[17180437.616000] /usr/share/EasyCam2/drivers/ov511/ov511_core.c: USB OV518 video device found
[17180437.620000] /usr/share/EasyCam2/drivers/ov511/ov511_core.c: Device revision 1
[17180437.656000] /usr/share/EasyCam2/drivers/ov511/ov511_core.c: Compression required with OV518...enabling
[17180437.808000] /usr/share/EasyCam2/drivers/ov511/ov511_core.c: Device at usb-0000:00:13.1-2 registered to minor 0
[17180437.876000] usbcore: registered new driver ov51x
[17180437.876000] /usr/share/EasyCam2/drivers/ov51x/ov51x.c: v1.65-1.12-mark : ov51x USB Camera Driver

```

Anyway the light on the webcam turns on, but there is no way to make it work... as you can see I tried with EasyCam2 as well but it's not working either...any hint?

---

### Post by marcozs on 2006-06-19
Nobody knows?

---

### Post by huygens on 2006-11-16
I guess it is a bit late to reply to you, but your camera should correctly use the ov511 module. So Dapper is correct in this regard.
Try perhaps to use the hint on the Ubuntu wiki: [https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

Huygens

---

