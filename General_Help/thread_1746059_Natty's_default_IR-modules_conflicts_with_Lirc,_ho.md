---
title: "Natty's default IR-modules conflicts with Lirc, how to turn them off?"
date: 2011-05-01
forum: General Help
---

### Post by gunnarflax on 2011-05-01
Hi! I've recently posted [this thread]("http://ubuntuforums.org/showthread.php?t=1743750") about the remote for my htpc sending keyboard input instead of the intended lirc ones. I asked why that happens in the [xbmc forum]("http://forum.xbmc.org/showthread.php?p=787084") and found out that it is because Natty has a bunch of default IR-modules which is supposed to make it all work out of the box without the need of configuring lirc. But XBMC, which is the media center I use, requires lirc and as I said I can't send the intended IR-signals. When I run **irw** I only see keyboard input (e.g. "^[[A") instead of "KEY_SOMETHING" and such.

In the XBMC thread I got some help trying to find which module which is causing the conflict but we didn't get that far. My setup is Ubuntu Server 11.04 x64 on a custom built htpc with the Antec Fusion case which includes a built in iMON LCD/IR-receiver, a volume knob on the case which uses lirc and an Antec Veris rm200 remote control.

If I run lsmod I get the following result:
```
lirc_imon
vesafb
nls_iso8859_1
nls_cp437
vfat
fat
snd_hda_codec_hdmi
snd_hda_codec_realtek
rt2860sta
arc4
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
rt2800pci
rt2800lib
crc_ccitt
ir_lirc_codec
snd_seq
lirc_dev
rt2x00pci
ir_sony_decoder
ir_jvc_decoder
ir_rc6_decoder
snd_timer
snd_seq_device
fglrx
edac_core
rc_imon_pad
rt2x00lib
edac_mce_amd
mac80211
serio_raw
ir_rc5_decoder
imon
ir_nec_decoder
rc_core
k10temp
cfg80211
eeprom_93cx6
snd
vice
sp5100_tco
i2c_piix4
soundcore
snd_page_alloc
xhci_hcd
shpchp
lp
parport
usb_storage
firewire_ohci
firewire_core
usbhid
hid
uas
crc_itu_t
para_jmicron
r8169
ahci
libahci
```

Which module could be the one causing the trouble? Or is there more than one?

---

### Post by gunnarflax on 2011-05-02
bump*

---

### Post by Triptol on 2011-05-10
Currently running into lirc problems as well, due to my natty upgrade. Not the same you are having, I guess, but nevertheless.

You could try setting up a Lircmap.xml and mapping the irw codes to the XBMC codes. Should do the trick.

---

### Post by Triptol on 2011-05-10
[http://ubuntuforums.org/showthread.php?p=10743326](http://ubuntuforums.org/showthread.php?p=10743326) is probably your solution

---

### Post by gunnarflax on 2011-05-10
> **Triptol said:**
> [http://ubuntuforums.org/showthread.php?p=10743326](http://ubuntuforums.org/showthread.php?p=10743326) is probably your solution

Thanks but I've already tried that and it didn't work. My problem isn't that it sends double keypresses, it is that instead of the lirc events that should be sent, a default ir-module conflicts and sends regular keyboard input instead.

---

### Post by gunnarflax on 2011-05-10
Please read this thread which is about the same problem and see if you can find the solution:

[http://ubuntuforums.org/showthread.php?p=10796433](http://ubuntuforums.org/showthread.php?p=10796433)

---

