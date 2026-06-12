---
title: "Very large keyboard lag in terminal for console and remote connections - Lucid 10.04"
date: 2010-12-18
forum: General Help
---

### Post by sheddenizen on 2010-12-18
I've got a Samsung R20 laptop which I want to run a MythTv back end on. At some point in the process of setting it up it has started exhibiting a very slow response time to key presses in terminal windows, i.e. when you hit a key it might take a number of seconds before you see the character appearing in the terminal. If I hit a number of keys quickly, there will be delay before they all appear at once.

If I type in gedit or the address bar in firefox there's no lag at all, but The Myth back end setup application shows it consistently and I've noticed it some of the time when typing into forms in various web pages, but not always.

Running top shows nothing out of the ordinary; CPU utilization is down at <2% and shows no peaking when I type.

The problem is not limited to the console; when I connect from another box via ssh -X I have exactly the same problems in the ssh terminal window as well as any other gnome-terminals or xterms I spawn from it.

Googling for this sort of problem has turned up a few similar results, but no consistent fixes or explanations. Does anybody know what this might be; it's driving me mad...

---

### Post by sheddenizen on 2010-12-26
Okay, seems this problem is being caused by the USB DVB-S receivers I'm using; when they're unplugged there's no problem, when one's plugged in the lag is noticeable, with two plugged in its horrendous. The receivers are "Q Box S2" made by TBS. The kernel modules were built from source supplied by the manufacturer with no issues and the receivers seem to working okay otherwise (scan reports plenty of received channels.) dmesg reports:

```
[  813.420104] usb 1-2: new high speed USB device using ehci_hcd and address 3
[  813.552450] usb 1-2: config 1 interface 0 altsetting 0 bulk endpoint 0x81 has invalid max
packet 2
[  813.553100] usb 1-2: configuration #1 chosen from 1 choice
[  813.663055] dvb-usb: found a 'TBS QBOXS2 DVBS2 USB2.0' in cold state, will try to load a firmware
[  813.663065] usb 1-2: firmware: requesting dvb-usb-tbsqbox-id5928.fw
[  813.758192] dvb-usb: downloading firmware from file 'dvb-usb-tbsqbox-id5928.fw'
[  813.758204] usb 1-2: firmware: requesting dvb-usb-tbsqbox-id5928.fw
[  813.763756] tbsqboxs2: start downloading TBSQBOX firmware
[  813.884071] dvb-usb: found a 'TBS QBOXS2 DVBS2 USB2.0' in warm state.
[  813.884189] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[  813.884926] DVB: registering new adapter (TBS QBOXS2 DVBS2 USB2.0)
[  814.056026] dvb-usb: MAC address: 00:22:ab:c0:13:6a
[  814.056031] 
[  814.145281] QBOXS2: CX24116 attached.
[  814.145536] DVB: registering adapter 0 frontend 0 (Conexant CX24116/CX24118)...
[  814.146194] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:13.5/usb1/1-2/input/input9
[  814.146290] dvb-usb: schedule remote query interval to 150 msecs.
[  814.146299] dvb-usb: TBS QBOXS2 DVBS2 USB2.0 successfully initialized and connected.
[  814.146362] usbcore: registered new interface driver tbsqboxs2

```

Xorg was treating the IR receiver as a keyboard so, suspecting that had something to do with it, I added a file in /usr/lib/X11/xorg.conf.d/ to ignore it, but that had no effect on the lag.

Any suggestions? Anyone?

---

### Post by dcstar on 2010-12-27
> **sheddenizen said:**
> Okay, seems this problem is being caused by the USB DVB-S receivers I'm using; when they're unplugged there's no problem, when one's plugged in the lag is noticeable, with two plugged in its horrendous.
............
Any suggestions? Anyone?

I shudder to think of the Interrupts one device (let alone two) that streams constant digital data via a USB port would flood the CPU with. As well, a laptop may not have the best hardware support for this sort of application compared to a normal motherboard.

One suggestion I would make is to manually set your CPU clocking to maximum and see if that helps - otherwise it is just poorly written software that just doesn't work that well in practice. Another option may be to experiment with different kernels.

---

### Post by sheddenizen on 2010-12-28
Thanks for the suggestions. The only setting I could find regarding the clock speed was the CPU power saving option in the bios which I turned off with no noticeable effect. 

I've just tried installing the receiver and its driver on my linux desktop - an Atom 330 running Maverick. There were no problems with keyboard response on that despite the slower CPU (compared with the laptop's Core Duo.) In case it was problem with that kernel version, I upgraded the distro on the the laptop to Maverick/10.10 with no improvement. 

Bear in mind this problem is occurring almost as soon as I plug the receiver in; it is not actually streaming any DVB data at this stage. (Typically, a good quality standard definition DVB stream comes in at 4Mbps - well below the sort of throughput you might expect from a USB flash stick or Ethernet adapter)

---

