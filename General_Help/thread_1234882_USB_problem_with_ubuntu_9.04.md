---
title: "USB problem with ubuntu 9.04"
date: 2009-08-08
forum: General Help
---

### Post by ml41782 on 2009-08-08
This problem is only on the laptop setup and not the desktop. 
The laptop is an HP mini100 -1000
 
 
I plug my signalink USB device into the desktop and it shows the device as /dev/dsp0 and the device works 
 
If I plug it into the laptop I see the activity in the log..
 
 
 
[FONT=bookman old style][FONT=Arial Narrow][SIZE=2]otg1017@Michael-Lussier-K4MQF:~$ sudo tail -f /var/log/messages[/SIZE][/FONT]
[SIZE=2][FONT=bookman old style]Aug 7 08:28:01 Michael-Lussier-K4MQF kernel: [ 538.296540] usb 4-1: configuration #1 chosen from 1 choice[/FONT][/SIZE]
[SIZE=2][FONT=bookman old style]Aug 7 08:28:01 Michael-Lussier-K4MQF kernel: [ 538.411722] usbcore: registered new interface driver hiddev[/FONT][/SIZE]
[SIZE=2][FONT=bookman old style]Aug 7 08:28:01 Michael-Lussier-K4MQF kernel: [ 538.415448] input: Burr-Brown from TI USB Audio CODEC as /class/input/input8[/FONT][/SIZE]
[SIZE=2][FONT=bookman old style]Aug 7 08:28:01 Michael-Lussier-K4MQF kernel: [ 538.448493] generic-usb 0003:08BB:2904.0001: input,hidraw0: USB HID v1.00 Device [Burr-Brown from TI USB Audio CODEC ] on usb-0000:00:1d.3-1/input3[/FONT][/SIZE]
[SIZE=2][FONT=bookman old style]Aug 7 08:28:01 Michael-Lussier-K4MQF kernel: [ 538.448532] usbcore: registered new interface driver usbhid[/FONT][/SIZE]
[SIZE=2][FONT=bookman old style]Aug 7 08:28:01 Michael-Lussier-K4MQF kernel: [ 538.448539] usbhid: v2.6:USB HID core driver[/FONT][/SIZE]
[SIZE=2][FONT=bookman old style]Aug 7 08:28:01 Michael-Lussier-K4MQF kernel: [ 538.569902] usbcore: registered new interface driver snd-usb-audio[/FONT][/SIZE]
[SIZE=2][FONT=bookman old style]Aug 7 08:28:38 Michael-Lussier-K4MQF sudo: pam_sm_authenticate: Called [/FONT][/SIZE]
[SIZE=2][FONT=bookman old style]Aug 7 08:28:38 Michael-Lussier-K4MQF sudo: pam_sm_authenticate: username = [otg1017] [/FONT][/SIZE]
[SIZE=2][FONT=bookman old style]Aug 7 08:28:38 Michael-Lussier-K4MQF sudo: Warning: Using default salt value (undefined in ~/.ecryptfsrc) [/FONT][/SIZE]
 
[/FONT]
Any thoughts

---

### Post by harry2006 on 2009-08-08
what is the issue? i dont' see any error messges or anything that might render your USB un-usable. r you not able to use your removable disk?

---

### Post by ml41782 on 2009-08-08
no its not useable. 
According to the instructions the device should show as /dev/dsp* device and it doesn't . on the desktop ubuntu box I have it does show as /dev/dsp1 or 0 not sure at this moment. 
 
I also looked at the /dev directory before I plugged in the signalink device an then after to see what new devices popped up. 
 
What showed up is. 
 
crw-rw-rw-+ 1 root fuse 10, 229 2009-08-08 11:35 hidraw0
drwxr-xr-x 3 root root 100 2009-08-08 11:35 input
drwxr-xr-x 2 root root 200 2009-08-08 11:35 snd
drwxr-xr-r- 6 root root 140 2009-08-08 11:35 .udev
 
 
lrwxrwxrwx  1 root root    15 2009-08-08 11:35 116:7 -> ../snd/pcmC1D0p
lrwxrwxrwx  1 root root    15 2009-08-08 11:35 116:8 -> ../snd/pcmC1D0c
lrwxrwxrwx  1 root root    16 2009-08-08 11:35 116:9 -> ../snd/controlC1
lrwxrwxrwx  1 root root    15 2009-08-08 11:35 13:72 -> ../input/event8
lrwxrwxrwx  1 root root    18 2009-08-08 11:35 189:1 -> ../bus/usb/001/002
lrwxrwxrwx  1 root root    10 2009-08-08 11:35 252:0 -> ../hidraw0
lrwxrwxrwx  1 root root    17 2009-08-08 11:35 253:12 -> ../usbdev1.2_ep85
lrwxrwxrwx  1 root root    17 2009-08-08 11:35 253:13 -> ../usbdev1.2_ep00
root@Michael-Lussier-K4MQF:/dev/char#

---

### Post by ml41782 on 2009-08-08
Is what I'm missing is something that will attach the device to a port ? Something along that line ? 
 
I have a CAT cable for radio control that is USB and it works perfectly and it shows as /dev/ttyUSB0 in the var/log/messages. It only seems to be this device. Is this something I can modify to force it to work ?

---

