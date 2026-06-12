---
title: "em28xx driver"
date: 2009-12-05
forum: General Help
---

### Post by Lyon on 2009-12-05
Is it possible to invert the red and blue values of the em28xx driver? I've installed the newest version so that I can capture video from my Pinnacle Dazzle DVC 100, and it seems to be working almost perfectly. In Cheese the video displays perfectly with the exception of that green bar there.

[IMG]http://i45.tinypic.com/oh4o42.png[/IMG]

However, in livestream.com's studio, it is displaying like so:

[IMG]http://i50.tinypic.com/2efotv9.png[/IMG]

It's not so much the compression that bothers me (what can you expect with live streaming video), but it seems like the red and blue channels have been inverted in the video. Is there anyway I can invert the R and B values in the terminal before sending the source?

For example, in ws4gl (webcam studio 4 gnu/linux) there is an option to invert R & B values when streaming your desktop as a source, I imagine for the purpose of a situation such as this.

I'm very glad the video and audio are both working otherwise :), in Windows it is quite a bit more of a headache to get the audio working than it was in linux.

---

### Post by Lyon on 2009-12-05
dmesg|grep em28xx

```
[   13.697794] em28xx: New device Pinnacle Systems GmbH DVC100 @ 480 Mbps (2304:021a, interface 0, class 0)
[   13.698705] em28xx #0: chip ID is em2820 (or em2710)
[   13.858984] em28xx #0: i2c eeprom 00: 1a eb 67 95 04 23 1a 02 12 00 11 03 98 10 6a 2e
[   13.858993] em28xx #0: i2c eeprom 10: 00 00 06 57 4e 00 00 00 60 00 00 00 02 00 00 00
[   13.859002] em28xx #0: i2c eeprom 20: 02 00 01 00 00 00 00 00 00 00 00 00 00 00 00 00
[   13.859010] em28xx #0: i2c eeprom 30: 00 00 20 40 20 80 02 20 10 01 00 00 00 00 00 00
[   13.859019] em28xx #0: i2c eeprom 40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   13.859027] em28xx #0: i2c eeprom 50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   13.859035] em28xx #0: i2c eeprom 60: 00 00 00 00 00 00 00 00 00 00 2e 03 50 00 69 00
[   13.859043] em28xx #0: i2c eeprom 70: 6e 00 6e 00 61 00 63 00 6c 00 65 00 20 00 53 00
[   13.859051] em28xx #0: i2c eeprom 80: 79 00 73 00 74 00 65 00 6d 00 73 00 20 00 47 00
[   13.859060] em28xx #0: i2c eeprom 90: 6d 00 62 00 48 00 00 00 10 03 44 00 56 00 43 00
[   13.859068] em28xx #0: i2c eeprom a0: 31 00 30 00 30 00 00 00 32 00 30 00 33 00 35 00
[   13.859076] em28xx #0: i2c eeprom b0: 36 00 30 00 37 00 35 00 31 00 33 00 34 00 31 00
[   13.859084] em28xx #0: i2c eeprom c0: 30 00 32 00 30 00 30 00 30 00 31 00 00 00 32 00
[   13.859093] em28xx #0: i2c eeprom d0: 33 00 31 00 32 00 33 00 00 00 00 00 00 00 00 00
[   13.859101] em28xx #0: i2c eeprom e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   13.859109] em28xx #0: i2c eeprom f0: 00 00 00 00 00 00 00 00 2f 64 ec 04 99 62 5d 0e
[   13.859118] em28xx #0: EEPROM ID= 0x9567eb1a, EEPROM hash = 0xa10d9684
[   13.859120] em28xx #0: EEPROM info:
[   13.859121] em28xx #0:	AC97 audio (5 sample rates)
[   13.859123] em28xx #0:	300mA max power
[   13.859124] em28xx #0:	Table at 0x06, strings=0x1098, 0x2e6a, 0x0000
[   13.861359] em28xx #0: Identified as Pinnacle Dazzle DVC 90/100/101/107 / Kaiser Baas Video to DVD maker / Kworld DVD Maker 2 (card=9)
[   14.952997] saa7115 0-0025: saa7113 found (1f7113d0e100000) @ 0x4a (em28xx #0)
[   16.250241] em28xx #0: Config register raw data: 0x12
[   16.290365] em28xx #0: AC97 vendor ID = 0xffffffff
[   16.310246] em28xx #0: AC97 features = 0x6a90
[   16.310249] em28xx #0: Empia 202 AC97 audio processor detected
[   17.112581] em28xx #0: v4l2 driver version 0.1.2
[   18.490142] em28xx #0: V4L2 video device registered as video1
[   18.500765] usbcore: registered new interface driver em28xx
[   18.500768] em28xx driver loaded

```

Are there any options I can call when I modprobe em28xx?

---

