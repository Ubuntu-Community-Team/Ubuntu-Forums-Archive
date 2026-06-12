---
title: "Blacklisting Kernel Modules In Virtualbox For Livecd"
date: 2011-03-17
forum: General Help
---

### Post by dodo3773 on 2011-03-17
I would like to speed up a live cd that I am creating. I would like to blacklist some kernel modules from loading. It is based off of the new Debian. Here are the ones that load now. 


```
vboxsf
loop
snd_intel8x0
snd_ac97_codec
ac97_bus
snd_pcsp
parport
snd_timer
psmouse
snd
_timer
i2c_piix4
joydev
ac
battery
soundcore
serio_raw
evdev
i2c_core
snd_page_alloc
button
vboxguest
ext3
jbd
mbcache
usbhid
hid
sg
sd_mod
crc_t10dif
sr_mod
cdrom
ata_generic
ata_piix
ohci_hcd
ahci
ehci_hcd
thermal
libata
usbcore
thermal_sys
nls_base
scsi_mod
e1000
```The output is from the "lsmod" command.

I am assuming that I can blacklist
vboxsf
vboxguest

and have the operating system still load. If I am wrong please let me know. I really do not want to start over. A lot of time has been put into it so far.

But other than that I am not sure. The livecd is all console based and all wireless. The wireless is a usb dongle. So, I need usb but I do not need a mouse, sound, or ethernet. I understand that I will have to re-enable the vboxsf and / or vboxguest to share a folder to copy my remastersys iso. Any help would be greatly appreciated. Thanks in advance.

---

