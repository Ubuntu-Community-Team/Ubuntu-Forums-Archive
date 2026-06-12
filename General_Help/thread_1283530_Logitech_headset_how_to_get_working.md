---
title: "Logitech headset how to get working"
date: 2009-10-05
forum: General Help
---

### Post by BAMF1501 on 2009-10-05
Ok so i got a new headset i plugit in and it doest detect ?

---

### Post by yeeeev on 2009-10-05
Can you open a terminal and post here the output of:
lsusb
?

---

### Post by BAMF1501 on 2009-10-05
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 006: ID 046d:0a01 Logitech, Inc. USB Headset
Bus 004 Device 002: ID 045e:074f Microsoft Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 413c:2101 Dell Computer Corp. SmartCard Reader Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by BAMF1501 on 2009-10-05
bump

---

### Post by BAMF1501 on 2009-10-07
bump anyone

---

### Post by BAMF1501 on 2009-10-07
almost 3 days isnt this support forum were the hell is the support ???

---

### Post by BAMF1501 on 2009-10-07
Here is some more information 

i typed 


$ cat /proc/asound/cards

and displayed

epic1501@ubuntu:~$ cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfebf4000 irq 16
 1 [Headset        ]: USB-Audio - Logitech USB Headset
                      Logitech Logitech USB Headset at usb-0000:00:13.2-2, full speed


then tried 

$ cat /proc/asound/devices

and displayed

epic1501@ubuntu:~$ cat /proc/asound/devices
  2:        : timer
  3:        : sequencer
  4: [ 0- 4]: digital audio capture
  5: [ 0- 0]: digital audio playback
  6: [ 0- 0]: digital audio capture
  7: [ 0]   : control
  8: [ 1- 0]: digital audio playback
  9: [ 1- 0]: digital audio capture
 10: [ 1]   : control

and when i type 
arecord -l

it displays

epic1501@ubuntu:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 4: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


and when i type 

aplay -l

it diplays

epic1501@ubuntu:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 4: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
epic1501@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by dmfagan9 on 2009-10-09
Am having the same problem this is my output when i go to test the headset in sounds

gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open audio device for playback.

---

