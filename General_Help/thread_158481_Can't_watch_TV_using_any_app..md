---
title: "Can't watch TV using any app."
date: 2006-04-11
forum: General Help
---

### Post by chris_andrew on 2006-04-11
Hi,

I have just installed a bttv TV card in my PC.  I am running Breezy and want to use an app to watch TV.  I tried KDETV and XawTV, but as yet, have been unable to pick-up any channels.  I have an internal aerial plugged into the card, and live in a 'good' signal area.

BTW, I am in the UK, so assumed I should be selecting Europe-West.

Can anybody help?

Many thanks,

Chris.

---

### Post by easyease on 2006-04-11
is it a anolologue or digital card? if digital maybe kaffeine player is worth a try....see my post.
 [http://www.ubuntuforums.org/showthread.php?t=158459](http://www.ubuntuforums.org/showthread.php?t=158459)

---

### Post by chris_andrew on 2006-04-11
Hi,

To the best of my knowledge, it's analogue.  Was given it 2 years ago, and it doesn't look "ground breaking", so would say analogue.

Thanks,

Chris.

---

### Post by easyease on 2006-04-11
aw ok well im not sure what to suggest, i never had much luck with analogue cards and linux in the past either. take a look at my post anyway if you got £20-30 pound going spare and want all the freeview channels and to use pc as a video recorder.

---

### Post by mlind on 2006-04-11
tried MythTV?

---

### Post by Christmas on 2006-04-11
I use TVTime on my Leadtek TV2000 XP and it's working perfect.

---

### Post by chris_andrew on 2006-04-11
Just installing it now, following your recommendation.

Thanks,

Chris.

Thought MythTV was used to bulid PVR's, not to watch TV at your desk.  A PVR is on my list of things to do, but  don't have the spare hardware at the mo.

---

### Post by chris_andrew on 2006-04-11
Looks very good, but I get "No Signal".  Will check my aerial lead.  How do I confirm the card is definitely seen, and the correct module loaded?

Thanks,

Chris.

---

### Post by chris_andrew on 2006-04-11
Aerial looks fine, I think it may be a module problem.  The card is a bt878, and the following is the output from dmesg:

[4294697.351000] bttv: driver version 0.9.15 loaded
[4294697.351000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[4294697.356000] bttv: Bt8xx card found (0).
[4294697.356000] bttv0: Bt878 (rev 17) at 0000:00:0c.0, irq: 16, latency: 32, mmio: 0xdfdfe000
[4294697.356000] bttv0: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]
[4294697.356000] bttv0: gpio: en=00000000, out=00000000 in=003fffff [init]
[4294697.371000] tveeprom(bttv internal): Huh, no eeprom present (err=-121)?
[4294697.371000] bttv0: using tuner=-1
[4294697.371000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[4294697.373000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[4294697.375000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[4294697.377000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[4294697.388000] bttv0: registered device video0
[4294697.394000] bttv0: registered device vbi0
[4294697.551000] bt878: AUDIO driver version 0.0.0 loaded
[4294697.556000] bt878: Bt878 AUDIO function found (0).
[4294697.556000] bt878(0): Bt878 (rev 17) at 00:0c.1, irq: 16, latency: 32, memory: 0xdfdff000
[4295206.938000] bttv0: timeout: drop=21 irq=3001/44990, risc=1313b07c, bits: HSYNC FDSR
[4295206.938000] bttv0: reset, reinitialize
[4306306.824000] bttv0: timeout: drop=116 irq=20709/1095298, risc=2227403c, bits: HSYNC OFLOW FBUS FDSR
[4306306.827000] bttv0: reset, reinitialize
[4307239.561000] bttv0: timeout: drop=491 irq=61010/1214812, risc=0dd600e4, bits: HSYNC OFLOW FDSR
[4307239.561000] bttv0: reset, reinitialize
[4307295.163000] bttv0: timeout: drop=608 irq=61618/1220146, risc=091c706c, bits: VSYNC HSYNC OFLOW FBUS FDSR
[4307295.163000] bttv0: reset, reinitialize
[4307381.245000] bttv0: timeout: drop=782 irq=62567/1228411, risc=2227403c, bits: VSYNC HSYNC OFLOW FBUS FDSR
[4307381.245000] bttv0: reset, reinitialize

---

