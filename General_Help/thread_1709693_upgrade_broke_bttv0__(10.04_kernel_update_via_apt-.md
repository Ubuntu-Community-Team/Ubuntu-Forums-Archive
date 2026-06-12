---
title: "upgrade broke bttv0:  (10.04 kernel update via apt-get update/upgrade) broke"
date: 2011-03-18
forum: General Help
---

### Post by anewbie on 2011-03-18
I have an old tvtuner (details below) that worked fine in 8.04 and 10.04. I'd been holding off on the kernel upgrade because it requires a reboot but did so today. The new kernel is 
2.6.32-30-generic
-
With this update the tvturner ceased to work:

Mar 18 16:42:17 pc1 kernel: [   12.102754] bttv0: Bt878 (rev 2) at 0000:05:02.0, irq: 23, latency: 64, mmio: 0xdfefe000
Mar 18 16:42:17 pc1 kernel: [   12.102786] bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb
Mar 18 16:42:17 pc1 kernel: [   12.102789] bttv0: using: Hauppauge (bt878) [card=10,autodetected]
Mar 18 16:42:17 pc1 kernel: [   12.102792] IRQ 23/bttv0: IRQF_DISABLED is not guaranteed on shared IRQs
Mar 18 16:42:17 pc1 kernel: [   12.105304] bttv0: Hauppauge/Voodoo msp34xx: reset line init [5]
Mar 18 16:42:17 pc1 kernel: [   12.136381] bttv0: Hauppauge eeprom indicates model#61381
Mar 18 16:42:17 pc1 kernel: [   12.136384] bttv0: tuner absent
Mar 18 16:42:17 pc1 kernel: [   12.137599] bttv0: registered device video0
Mar 18 16:42:17 pc1 kernel: [   12.137703] bttv0: registered device vbi0
Mar 18 16:42:17 pc1 kernel: [   12.137800] bttv0: registered device radio0
Mar 18 16:42:17 pc1 kernel: [   12.137821] bttv0: PLL: 28636363 => 35468950 .. ok
Mar 18 16:46:01 pc1 kernel: [  265.098690] bttv0: PLL can sleep, using XTAL (28636363).
Mar 18 16:51:14 pc1 kernel: [  577.904509] bttv0: timeout: drop=2087 irq=25804/26452, risc=2f50c044, bits: HSYNC OFLOW FDSR
Mar 18 16:52:52 pc1 kernel: [  676.472508] bttv0: timeout: drop=2809 irq=34069/34717, risc=2f50b06c, bits: HSYNC OFLOW FDSR
Mar 18 16:54:41 pc1 kernel: [  784.640876] bttv0: reset, reinitialize
Mar 18 16:54:41 pc1 kernel: [  784.640903] bttv0: PLL can sleep, using XTAL (28636363).
Mar 18 16:54:41 pc1 kernel: [  785.140684] bttv0: timeout: drop=3618 irq=43182/43830, risc=338b903c, bits: HSYNC OFLOW
Mar 18 16:57:03 pc1 kernel: [  926.688512] bttv0: timeout: drop=4749 irq=55100/55748, risc=2973804c, bits: HSYNC OFLOW FDSR
Mar 18 16:59:47 pc1 kernel: [ 1091.044510] bttv0: timeout: drop=6046 irq=68956/69604, risc=2c45703c, bits: HSYNC OFLOW FDSR
Mar 18 17:01:22 pc1 kernel: [ 1186.000509] bttv0: timeout: drop=6772 irq=76950/77598, risc=338b903c, bits: HSYNC OFLOW FBUS FDSR
Mar 18 17:01:39 pc1 kernel: [ 1202.980021] bttv0: timeout: drop=6934 irq=78392/79040, risc=338b903c, bits: HSYNC OFLOW FBUS FDSR
Mar 18 17:01:43 pc1 kernel: [ 1206.676511] bttv0: timeout: drop=6964 irq=78700/79348, risc=2bd6804c, bits: HSYNC OFLOW FDSR
--
Any idea for a quick fix ?

---

### Post by anewbie on 2011-03-18
When I run tvtime this is the error it prints

videoinput: Can't read frame. Error was: Invalid argument (0).
videoinput: Driver refuses to stop streaming: Invalid argument.
videoinput: Can't free frame 0: Device or resource busy
videoinput: Can't free frame 1: Device or resource busy
videoinput: Can't free frame 2: Device or resource busy
videoinput: Can't free frame 3: Device or resource busy
videoinput: Driver refuses to start streaming: Device or resource busy.
--
basically device /dev/video0 is busy or hung.

---

### Post by Rod J on 2011-04-29
I'm having similar problems with my old TV card too. This is an example of the messages I find in my logs:

```
Apr 29 17:34:38 core2-duo kernel: [13977.548981] bttv0: timeout: drop=0 irq=108/216299, risc=ffffffff, bits: FMTCHG VSYNC HSYNC OFLOW HLOCK VPRES 6 7 I2CDONE GPINT 10 RISCI FBUS FTRGT FDSR PPERR RIPERR PABORT OCERR SCERR
Apr 29 17:34:38 core2-duo kernel: [13978.048513] bttv0: timeout: drop=0 irq=108/216299, risc=ffffffff, bits: FMTCHG VSYNC HSYNC OFLOW HLOCK VPRES 6 7 I2CDONE GPINT 10 RISCI FBUS FTRGT FDSR PPERR RIPERR PABORT OCERR SCERR
Apr 29 17:34:39 core2-duo kernel: [13978.548511] bttv0: timeout: drop=0 irq=108/216320, risc=ffffffff, bits: FMTCHG VSYNC HSYNC OFLOW HLOCK VPRES 6 7 I2CDONE GPINT 10 RISCI FBUS FTRGT FDSR PPERR RIPERR PABORT OCERR SCERR
Apr 29 17:34:39 core2-duo kernel: [13979.048013] bttv0: timeout: drop=0 irq=108/216320, risc=ffffffff, bits: FMTCHG VSYNC HSYNC OFLOW HLOCK VPRES 6 7 I2CDONE GPINT 10 RISCI FBUS FTRGT FDSR PPERR RIPERR PABORT OCERR SCERR
Apr 29 17:34:40 core2-duo kernel: [13979.431276] bttv0: SCERROCERR @ ffffffff,bits: FMTCHG* VSYNC* HSYNC* OFLOW* HLOCK* VPRES* 6* 7* I2CDONE* GPINT* 10* RISCI* FBUS* FTRGT* FDSR* PPERR* RIPERR* PABORT* OCERR* SCERR*
Apr 29 17:34:40 core2-duo kernel: [13979.928081] bttv0: timeout: drop=0 irq=109/216330, risc=ffffffff, bits: FMTCHG VSYNC HSYNC OFLOW HLOCK VPRES 6 7 I2CDONE GPINT 10 RISCI FBUS FTRGT FDSR PPERR RIPERR PABORT OCERR SCERR
Apr 29 17:34:41 core2-duo kernel: [13980.428009] bttv0: timeout: drop=0 irq=109/216333, risc=ffffffff, bits: FMTCHG VSYNC HSYNC OFLOW HLOCK VPRES 6 7 I2CDONE GPINT 10 RISCI FBUS FTRGT FDSR PPERR RIPERR PABORT OCERR SCERR
Apr 29 17:34:41 core2-duo kernel: [13980.434802] bttv0: SCERROCERR @ ffffffff,bits: FMTCHG* VSYNC* HSYNC* OFLOW* HLOCK* VPRES* 6* 7* I2CDONE* GPINT* 10* RISCI* FBUS* FTRGT* FDSR* PPERR* RIPERR* PABORT* OCERR* SCERR*
Apr 29 17:34:41 core2-duo kernel: [13980.434867] bttv0: SCERROCERR @ ffffffff,bits: FMTCHG* VSYNC* HSYNC* OFLOW* HLOCK* VPRES* 6* 7* I2CDONE* GPINT* 10* RISCI* FBUS* FTRGT* FDSR* PPERR* RIPERR* PABORT* OCERR* SCERR*
Apr 29 17:34:41 core2-duo kernel: [13980.434919] bttv0: SCERROCERR @ ffffffff,bits: FMTCHG* VSYNC* HSYNC* OFLOW* HLOCK* VPRES* 6* 7* I2CDONE* GPINT* 10* RISCI* FBUS* FTRGT* FDSR* PPERR* RIPERR* PABORT* OCERR* SCERR*
Apr 29 17:34:41 core2-duo kernel: [13980.434971] bttv0: SCERROCERR @ ffffffff,bits: FMTCHG* VSYNC* HSYNC* OFLOW* HLOCK* VPRES* 6* 7* I2CDONE* GPINT* 10* RISCI* FBUS* FTRGT* FDSR* PPERR* RIPERR* PABORT* OCERR* SCERR*
Apr 29 17:34:41 core2-duo kernel: [13980.932081] bttv0: timeout: drop=0 irq=110/216351, risc=ffffffff, bits: FMTCHG VSYNC HSYNC OFLOW HLOCK VPRES 6 7 I2CDONE GPINT 10 RISCI FBUS FTRGT FDSR PPERR RIPERR PABORT OCERR SCERR
Apr 29 17:34:42 core2-duo kernel: [13981.432015] bttv0: timeout: drop=0 irq=110/216357, risc=ffffffff, bits: FMTCHG VSYNC HSYNC OFLOW HLOCK VPRES 6 7 I2CDONE GPINT 10 RISCI FBUS FTRGT FDSR PPERR RIPERR PABORT OCERR SCERR

```I also use tvtime and it was working with the card just fine ... but I only use the card as a capture device for the output from my satellite box. Now when I start tvtime I get this in the syslog.log:

```
Apr 29 17:48:48 core2-duo kernel: [  708.289557] tvtime[2083]: segfault at 6b0 ip 0804d824 sp bfdcae4c error 4 in tvtime[8048000+76000]
Apr 29 17:49:51 core2-duo kernel: [  772.189227] tvtime[2089]: segfault at 6b0 ip 0804d824 sp bfedd11c error 4 in tvtime[8048000+76000]
Apr 29 17:49:53 core2-duo kernel: [  774.246151] tvtime[2094]: segfault at 6b0 ip 0804d824 sp bf93d59c error 4 in tvtime[8048000+76000]
Apr 29 17:52:51 core2-duo kernel: [  951.824372] tvtime[2096]: segfault at 6b0 ip 0804d824 sp bff0cecc error 4 in tvtime[8048000+76000]
```What complicates matters with mine is that it has been doing this since I  replaced the power supply in the PC. Sometimes everything works fine,  then other times it's like this.

I'm baffled with it so far. I'll boot into Windows XP and see what happens there because it's looking like a hardware failure to me.

---

### Post by anewbie on 2011-04-29
My problem went away when I plugged the cable in the vga port of my nvidia card (ge 7300) and rebooted. I had upgraded my monitor to one that had a working dvi cable - so my wild guess is that there is a conflict between the ge 7300 and the tv card; but no clue why it would only occur when using the dvi port (now that the tv card is working the dvi port won't work)

---

### Post by Rod J on 2011-04-29
I booted twice into WinXP, and then into my other Linux (UserOS Select 10.04 - same as Ubuntu 10.04 with Xfce desktop and currently using kernel 2.6.32-27-generic) and there were no problems with the card. Everything ran fine in both systems. Then I booted back into my regular Ubuntu 10.04 system and again everything was 100% OK! It's a weird intermittent problem ... I'm going to upgrade to the new kernel that is available now (I'm also using 2.6.32-30-generic in this OS at the moment) and maybe that will fix it. 

I have difficulty believing it's a kernel problem though because it definitely started having this problem as soon as I replaced the power supply (my old PSU was dying ... had leaking capacitors in it). I posted on another forum about that saga, you can read it here: [http://forums.pcworld.co.nz/showthread.php?t=116900](http://forums.pcworld.co.nz/showthread.php?t=116900)

---

### Post by anewbie on 2011-04-29
Well I have to think it is a kernel issue; but probably not specific to the recent upgrade. Vaguely I think this happened before; perhaps it is some sort of device conflict or ordering of devices seen during pci scan ?
-
Next time I update the kernel (have to reboot) I will try to the dvi port again and see if it is a consistent issue (use vga things work use dvi things don't work). My guess is that it won't be consistent but i actually don't know if dvi port causes the video card to use different i/o addresses or irq or whatever.

---

### Post by Rod J on 2011-05-22
Well I have to agree with you that it probably was a kernel issue as since I updated mine (now running 2.6.32-31-generic) for the last three weeks or so I have had no problems with the TV card at all. 

It must have just been an odd coincidence that it began playing up very soon after I replaced my PSU. But the kernel update seems to have fixed the problem, thankfully.
[B]
Update:[/B] OK, scratch what I said above. Everything had been funning fine until I moved the PC the other day and straight away the card started playing up again ... filled my kernel.log and syslog with so many entries like above that they ballooned to about 1.8Gb each! I rebooted into my Natty 11.04 install and tried TVTime there. No go, checked the kernel.log and it showed a segfault message. So I shutdown the PC, pulled the card out, inspected it thoroughly for dry solder joints, etc and reinserted it firmly. Haven't had any problems since then ... so I think my problem was hardware after all.

---

