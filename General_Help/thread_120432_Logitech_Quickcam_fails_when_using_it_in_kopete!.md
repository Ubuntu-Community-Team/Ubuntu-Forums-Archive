---
title: "Logitech Quickcam fails when using it in kopete!"
date: 2006-01-21
forum: General Help
---

### Post by daller on 2006-01-21
Hi There,

My sister uses a "Logitech Quickcam" webcam on her pc.

Finally I got it working in kopete!

After some minutes, kopete stalls and i can trace this with dmesg

```
[4296444.935000] quickcam: frame lost
[4296445.465000] quickcam: frame lost
[4296445.815000] quickcam: frame lost
[4296445.995000] quickcam: frame lost
[4296446.525000] quickcam: frame lost
[4296486.502000] quickcam: Control URB error -2
[4296489.602000] quickcam: qc_stv_set error -110
[4296489.702000] quickcam: Control URB error -2
[4296494.802000] quickcam: usb_set_interface error
[4296532.802000] quickcam: sensor initialization failed: -110

```

Killing kopete, and starting it up again, I can't choose the webcam in the confguration of kopete! (Only my tvtuner-card)

Is it the tvcard that messes with things, or do you have similar problems too?

Trying to debug just a little, I thought running "lsusb" would make sense...

It stalls for about 30 seconds, and then outputs:

```
nikoline@ubuntu:~$ lsusb
Bus 001 Device 009: ID 046d:0870 Logitech, Inc. QuickCam Express
Bus 001 Device 001: ID 0000:0000

```

---

