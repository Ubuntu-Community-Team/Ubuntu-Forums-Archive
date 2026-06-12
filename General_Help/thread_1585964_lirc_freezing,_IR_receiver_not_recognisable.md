---
title: "lirc freezing, IR receiver not recognisable"
date: 2010-10-01
forum: General Help
---

### Post by jampe on 2010-10-01
I've been using the apple remote (A1156) with xbmc, and it's been working out great until yesterday, where it just stopped responding out of nowhere.

**gnome-lirc-properties**
When I open the gnome-lirc-properties app, the terminal responds as following:
```

WARNING:root:/usr/share/lirc/remotes: Remote Antec_Veris_Premiere listed twice in imon/lircd.conf.imon-mceusb and imon/lircd.conf.imon-antec-veris.
WARNING:root:/usr/share/lirc/remotes: Remote iMON-PAD listed twice in imon/lircd.conf.imon-pad and imon/lircd.conf.imon-pad.
WARNING:root:/usr/share/lirc/remotes: Remote PVR2000 listed twice in leadtek/lircd.conf.PVR2000 and leadtek/lircd.conf.PVR2000.
WARNING:root:/usr/share/lirc/remotes: Remote Hauppauge listed twice in hauppauge/lircd.conf.hauppauge and hauppauge/lircd.conf.hauppauge.
WARNING:root:/usr/share/lirc/remotes: Remote BESTBUY listed twice in bestbuy/lircd.conf.bestbuy and bestbuy/lircd.conf.bestbuy2.
WARNING:root:/usr/share/lirc/remotes: Remote Medion_X10 listed twice in atiusb/lircd.conf.atiusb and atiusb/lircd.conf.atiusb.
WARNING:root:/usr/share/lirc/remotes: Remote Medion_X10 listed twice in atiusb/lircd.conf.atiusb and atiusb/lircd.conf.atiusb.
WARNING:root:/usr/share/lirc/remotes: Remote DVICO_MCE listed twice in dvico/lircd.conf.fusionHDTV and dvico/lircd.conf.fusionHDTV.
WARNING:root:/usr/share/lirc/remotes: Remote NEC listed twice in generic/NEC-pulse.conf and generic/NEC-short-pulse.conf.
WARNING:root:/usr/share/lirc/remotes: Remote SONY listed twice in generic/SONY20.conf and generic/SONY12.conf.
WARNING:root:/usr/share/lirc/remotes: Remote NEC listed twice in generic/NEC.conf and generic/NEC-short-pulse.conf.

```

And whenever I press "autodetect" or try to select the correct IR receiver (0x8242), the application hangs and doesn't give me any more information.

**irw**
irw doesn't give me any feedback at all.

**dmesg**
dmesg gives me this on the IR receiver:
```

[    9.971849] apple 0003:05AC:8242.0001: hiddev97,hidraw6: USB HID v1.11 Device [Apple Computer, Inc. IR Receiver] on usb-0000:00:1d.2-1/input0

```

**My suspicions**
I think the IR receiver (0x8242) is no longer recognised by lirc, but I haven't been able to figure out why or how to fix it.
In a desperate attempt to correct things, I did try to purge lirc and delete the configuration files before installing it again, but to no avail.

I could really use some help on this.
----------
PC: MacBook Pro 4.1/early 2008 (curse you)
OS: Ubuntu 10.04 Lucid Lynx
IR remote: Apple A1156
IR receiver: Internal 0x8242

---

### Post by jampe on 2010-10-03
bump.

---

### Post by jampe on 2010-10-19
Could someone just let me know if I'm providing the wrong info, asking the wrong questions or posting in the wrong forum?

I haven't been getting answers in any of posts, it's a bit frustrating :P

---

### Post by Superdude_123 on 2010-12-16
So I think I was having a similar problem with LIRC on a  my Ubuntu 9.10.

When doing "sudo dmesg", I would see the following for my remote

 lirc_mceusb[2]: Topseed Technology Corp. eHome Infrared Transceiver on usb3:2

My problem was that after some time, the remote receiver wasn't responding anymore, and I had to reboot the system. After reading [http://ubuntuforums.org/archive/index.php/t-980797.html](http://ubuntuforums.org/archive/index.php/t-980797.html), it basically said to modify /etc/lirc/hardware.conf with the following changes:

REMOTE_MODULES="false"

LOAD_MODULES="lirc_dev lirc_mceusb"

Then restart lirc

sudo /etc/init.d/lirc restart

Also, if you want to see what your PC is receiving for commands from the remote, just run "irw" incase this doesn't work for you.

---

### Post by jampe on 2010-12-16
Thanks, I'll keep that in mind if it messes up again. I have reinstalled Lucid for other reasons in the meantime, so the problem solved itself.

---

