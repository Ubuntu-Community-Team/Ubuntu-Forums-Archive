---
title: "cat /dev/video0 &gt; /tmp/test.mpg freezes computer"
date: 2006-04-19
forum: General Help
---

### Post by water on 2006-04-19
i'm working my way through the wonderfull mythtv how to : [http://s91928265.onlinehome.us/hfamily/mythtv/myth_ubuntu.html]("http://s91928265.onlinehome.us/hfamily/mythtv/myth_ubuntu.html")

when i get to ```
cat /dev/video0 > /tmp/test.mpg
``` to verify the ivtv drivers the computer freezes up.

when i run :
```

depmod
modprobe ivtv
dmesg

``` 
it returns no errors as far as i'm able to tell (i've pasted the output below) and idicates that my pvr500 is correctly identified by the system.

has anybody got any idea on how i should aproach this issue?

:water



```

[4294703.081000] ivtv:  ==================== START INIT IVTV =================== =
[4294703.081000] ivtv:  version 0.4.4 (tagged release) loading
[4294703.081000] ivtv:  Linux version: 2.6.12-10-686 686 gcc-3.4
[4294703.081000] ivtv:  In case of problems please include the debug info betwee n
[4294703.081000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[4294703.081000] ivtv:  any module options, when mailing the ivtv-users mailingl ist.
[4294703.092000] ivtv0: Autodetected WinTV PVR 150 card (cx23416 based)
[4294703.100000] ACPI: PCI Interrupt 0000:02:08.0[A] -> GSI 19 (level, low) -> I RQ 19
[4294703.100000] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[4294703.159000] tveeprom: Second (radio) tuner idx 101
[4294703.159000] tveeprom: ivtv version
[4294703.159000] tveeprom: Hauppauge: model = 23559, rev = D591, serial# = 82018 12
[4294703.159000] tveeprom: tuner = Philips FQ1216AME MK4 (idx = 91, type = 56)
[4294703.159000] tveeprom: tuner fmt = PAL(B/G) PAL(I) SECAM(L/L') PAL(D/K) (eep rom = 0x74, v4l2 = 0x00400e17)
[4294703.159000] tveeprom: audio processor = CX25843 (type = 25)
[4294703.159000] tveeprom: decoder processor = CX25843 (type = 1e)
[4294703.159000] ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
[4294703.201000] ivtv0: This is the first unit of a PVR500
[4294703.215000] tuner (ivtv): chip found at addr 0xc0 i2c-bus ivtv i2c driver # 0
[4294703.216000] TEA5767 detected.
[4294703.216000] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=60]
[4294703.219000] tuner: type set to 62 (Philips TEA5767HN FM Radio) by autodetec t
[4294703.219000] type set to 62 (Philips TEA5767HN FM Radio)
[4294703.219000] tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c driver # 0
[4294703.219000] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61]
[4294703.402000] cx25840 0-0044: ivtv driver
[4294703.403000] cx25840 0-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[4294706.757000] cx25840 0-0044: loaded v4l-cx25840.fw firmware (14264 bytes)
[4294706.821000] ivtv0: i2c attach to card #0 ok [client=cx25840, addr=44]
[4294706.894000] wm8775 0-001b: ivtv driver
[4294706.895000] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[4294706.903000] ivtv0: i2c attach to card #0 ok [client=wm8775, addr=1b]
[4294706.929000] tda9887 0-0043: (ivtv) chip found @ 0x86 (ivtv i2c driver #0)
[4294706.930000] ivtv0: i2c attach to card #0 ok [client=tda9887, addr=43]
[4294706.985000] ivtv0: Detected a TEA5767 radio tuner. Enabling radio support.
[4294707.097000] input: PS2++ Logitech Wheel Mouse on isa0060/serio1
[4294707.310000] ts: Compaq touchscreen protocol output
[4294707.825000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[4294708.035000] ivtv0: Encoder revision: 0x02050032
[4294708.037000] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4 096KB total)
[4294708.040000] ivtv0: Allocate DMA encoder YUV stream: 161 x 12960 buffers (20 48KB total)
[4294708.043000] ivtv0: Allocate DMA encoder VBI stream: 80 x 26208 buffers (204 8KB total)
[4294708.046000] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffer s (2048KB total)
[4294708.049000] ivtv0: Create encoder radio stream
[4294708.049000] tuner: type set to 56 (Philips PAL/SECAM multi (FQ1216AME MK4))  by ivtv i2c driver #0
[4294708.267000] ivtv0: Initialized WinTV PVR 500 (unit #1), card #0
[4294708.267000] ivtv:  ======================  NEXT CARD  ===================== =
[4294708.267000] ivtv1: Autodetected WinTV PVR 150 card (cx23416 based)
[4294708.268000] ACPI: PCI Interrupt 0000:02:09.0[A] -> GSI 18 (level, low) -> I RQ 18
[4294708.268000] ivtv1: Unreasonably low latency timer, setting to 64 (was 32)
[4294708.311000] tveeprom: Second (radio) tuner idx 101
[4294708.311000] tveeprom: ivtv version
[4294708.311000] tveeprom: Hauppauge: model = 23559, rev = D591, serial# = 82018 12
[4294708.311000] tveeprom: tuner = Philips FQ1216AME MK4 (idx = 91, type = 56)
[4294708.311000] tveeprom: tuner fmt = PAL(B/G) PAL(I) SECAM(L/L') PAL(D/K) (eep rom = 0x74, v4l2 = 0x00400e17)
[4294708.311000] tveeprom: audio processor = CX25843 (type = 25)
[4294708.311000] tveeprom: decoder processor = CX25843 (type = 1e)
[4294708.312000] ivtv1: i2c attach to card #1 ok [client=tveeprom, addr=50]
[4294708.326000] tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c driver # 1
[4294708.326000] ivtv1: i2c attach to card #1 ok [client=(tuner unset), addr=61]
[4294708.497000] cx25840 1-0044: ivtv driver
[4294708.497000] cx25840 1-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #1)
[4294711.571000] cx25840 1-0044: loaded v4l-cx25840.fw firmware (14264 bytes)
[4294711.635000] ivtv1: i2c attach to card #1 ok [client=cx25840, addr=44]
[4294711.857000] wm8775 1-001b: ivtv driver
[4294711.857000] wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #1)
[4294711.866000] ivtv1: i2c attach to card #1 ok [client=wm8775, addr=1b]
[4294711.879000] tda9887 1-0043: (ivtv) chip found @ 0x86 (ivtv i2c driver #1)
[4294711.879000] ivtv1: i2c attach to card #1 ok [client=tda9887, addr=43]
[4294711.898000] ivtv1: This is the second unit of a PVR500
[4294711.898000] ivtv1: Correcting tveeprom data: no radio present on second uni t
[4294712.878000] ivtv1: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[4294713.241000] ivtv1: Encoder revision: 0x02050032
[4294713.243000] ivtv1: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4 096KB total)
[4294713.246000] ivtv1: Allocate DMA encoder YUV stream: 161 x 12960 buffers (20 48KB total)
[4294713.249000] ivtv1: Allocate DMA encoder VBI stream: 80 x 26208 buffers (204 8KB total)
[4294713.251000] ivtv1: Allocate DMA encoder PCM audio stream: 455 x 4608 buffer s (2048KB total)
[4294713.252000] tuner: type set to 56 (Philips PAL/SECAM multi (FQ1216AME MK4))  by ivtv i2c driver #1
[4294713.470000] ivtv1: Initialized WinTV PVR 500 (unit #2), card #1
[4294713.470000] ivtv:  ====================  END INIT IVTV  =================== =

```

---

### Post by michaelboord on 2008-01-02
Same problem here :(

---

