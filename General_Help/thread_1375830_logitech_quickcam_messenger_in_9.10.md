---
title: "logitech quickcam messenger in 9.10"
date: 2010-01-08
forum: General Help
---

### Post by yon2501 on 2010-01-08
i need to get my quickcam working with ubuntu since there are no windows7 drivers available, i tried this [http://www.kuhrti.de/index.php/article/logitech-quickcam-messenger-on-ubuntu-9-04/](http://www.kuhrti.de/index.php/article/logitech-quickcam-messenger-on-ubuntu-9-04/) but after i said "sudo make install" i got errors and the install quit. im guessing because that was made for 9.04 and not 9.10 but idk. also i need to get it working with more then just skype preferably id like to get it working with pidgin but working at all is just as good

---

### Post by cariboo on 2010-01-08
Your quickcam should work out of the box with no extra drivers needed, when you plug your webcam in. dmesg output should look something like this:

```
usb 1-8: new high speed USB device using ehci_hcd and address 3
[14101.619263] usb 1-8: configuration #1 chosen from 1 choice
[14102.161172] Linux video capture interface: v2.00
[14102.177670] uvcvideo: Found UVC 1.00 device <unnamed> (046d:09c1)
[14102.211041] input: UVC Camera (046d:09c1) as /devices/pci0000:00/0000:00:02.1/usb1/1-8/1-8:1.0/input/input6
[14102.211097] usbcore: registered new interface driver uvcvideo
[14102.211101] USB Video Class driver (v0.1.0)
[14102.373787] usbcore: registered new interface driver snd-usb-audio
```

I just plugged the webcam that I use on my laptop in to this computer, installed cheese. See screenshot.

---

