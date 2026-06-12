---
title: "Thrustmaster Formula T1 steering wheel not recognised"
date: 2010-01-31
forum: General Help
---

### Post by Lord Quinny on 2010-01-31
Hello,

I am new in Linux so please bear with me.

I have a Thrustmaster Formula T1 steering wheel and pedals connected to a Soundblaster Live gameport.

I just cannot seem to get Ubuntu to recognise it.

I know the gameport works because I can connect a sidewinder joystick to it which will work fine.
I know the steering wheel and pedals work because I can connect them to another computer I have with windows on it.

Has anyone ever got one of these working?

Here is some of the output which may help identify my system components.

$ lsmod | grep gameport

```
gameport            13712  2 emu10k1_gp
```

$ sudo lspci -vvnn

```
03:01.1 Input device controller [0980]: Creative Labs SB Live! Game Port [1102:7002] (rev 07)
       Subsystem: Creative Labs Device [1102:0020]
       Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
       Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
       Latency: 32
       Region 0: I/O ports at dc00 [size=8]
       Capabilities: [dc] Power Management version 1
               Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
               Status: D0 PME-Enable- DSel=0 DScale=0 PME-
       Kernel driver in use: Emu10k1_gameport
       Kernel modules: emu10k1-gp
```

$ uname -r

```
2.6.31-17-generic
```

I have tried modprobe tmdc but this doesn't seem to have any effect. I have tried several other modprobes for joysticks too with no apparent effect.

---

### Post by Lord Quinny on 2010-02-08
I have been emailing Vojtech Pavlik who created some of the joystick modules.

He determined that the steering wheel is using the X1 axis and the pedals are using the X2 axis.

The analog module will not work unless there is a Y1 axis.

So he gave me three options:

1. Remove this section from analog.c and recompile and it should work:
```

533         if ((port->mask & 3) != 3 && port->mask != 0xc) {
534                 printk(KERN_WARNING "analog.c: Unknown joystick device found  "
535                         "(data=%#x, %s), probably not analog joystick.\n",
536                         port->mask, port->gameport->phys);
537                 return -1;
538         }

```

I tried doing this but I am not experienced enough to get this to compile. Not sure what I need to do.

2. Solder a 47kOhm resistor across the Y1 axis.

3. Swap the pedal wire X2 with Y1 in the device.

---

### Post by Gibby13 on 2010-02-14
Did you get it working?

---

### Post by Lord Quinny on 2010-02-15
Hi,

I have not got it working yet. I tried to modify analog.c on another computer. It successfully built but I couldn't get it to create any /dev/input/js0 device. For some reason I wasn't getting any dmesg output (even for joydump) so I don't know what's going on there.

I would like to rewire it (then I could potentially use a USB adapter) but since the plug is encased in silicone I would need to get hold of another gameport plug.

---

### Post by Gibby13 on 2010-02-16
I was able to get mine working be editing the analog.c and compiling and installing the kernel again. However I have to remove and add the analog module everytime I reboot, try that.

---

### Post by Lord Quinny on 2010-02-18
Thanks for the confirmation Gibby13.

I don't really want to bloat my PC with source code but I may have to for something else I want to try.

While looking up how to modify modules I do remember seeing instructions on how to make it used upon boot up so it is possible.

Is it possible to put the change into the kernel source? It doesn't seem that the check we removed serves any purpose other than to exclude some analog devices which would otherwise work.

---

