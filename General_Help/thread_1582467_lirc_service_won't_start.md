---
title: "lirc service won't start"
date: 2010-09-26
forum: General Help
---

### Post by JayOui on 2010-09-26
I have been working to try and get lirc to work with my Winfast 2000/XP. I keep getting an error that the kernel module isn't loaded. This is on Ubuntu 10.04 x64. When I try to start the service, I get the following:

```

jason@jason-desktop:~$ sudo service lirc start
 * Loading LIRC modules                                                  [ OK ] 
 * Unable to load LIRC kernel modules. Verify your
 * selected kernel modules in /etc/lirc/hardware.conf

```Here is the output of /etc/lirc/hardware.conf

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Winfast TV2000/XP (card=34)"
REMOTE_MODULES="devinput"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="leadtek/lircd.conf.RM-0010"
REMOTE_LIRCD_ARGS=""
```Excerpt from lspci output
```
04:06.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
04:06.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)

```I can see it find the card in dmesg as well:
```
[   11.603047] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   11.604228] bttv: Bt8xx card found (0).
[   11.604244] bttv 0000:04:06.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   11.604255] bttv0: Bt878 (rev 17) at 0000:04:06.0, irq: 21, latency: 64, mmio: 0xfbfff000
[   11.604289] bttv0: detected: Leadtek WinFast TV 2000 [card=34], PCI subsystem ID is 107d:6606
[   11.604291] bttv0: using: Leadtek WinFast 2000/ WinFast 2000 XP [card=34,autodetected]
[   11.604293] IRQ 21/bttv0: IRQF_DISABLED is not guaranteed on shared IRQs
[   11.604325] bttv0: gpio: en=00000000, out=00000000 in=00bf7707 [init]
[   11.604447] bttv0: tuner type=5
[   11.605630] ppdev: user-space parallel port driver
[   11.624270] bttv0: audio absent, no audio device found!
[   11.633340] tuner 0-0061: chip found @ 0xc2 (bt878 #0 [sw])
[   11.639209] tuner-simple 0-0061: creating new instance
[   11.639212] tuner-simple 0-0061: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
[   11.640058] bttv0: registered device video0
[   11.640074] bttv0: registered device vbi0
[   11.640088] bttv0: registered device radio0
[   11.640117] bttv0: PLL: 28636363 => 35468950 ..
```Thanks for any help.

---

### Post by JayOui on 2010-09-26
I found another thread that indicated that you needed to disable LOAD_MODULES=false in /etc/lirc/hardware.conf and that got lirc started. Now I just need to see how to get it to recognize all of the keys on the remote.

[http://ubuntuforums.org/showthread.php?t=1010402](http://ubuntuforums.org/showthread.php?t=1010402)

---

