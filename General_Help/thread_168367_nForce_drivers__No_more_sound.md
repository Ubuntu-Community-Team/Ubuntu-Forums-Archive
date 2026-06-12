---
title: "nForce drivers \ No more sound"
date: 2006-04-30
forum: General Help
---

### Post by C0n5ci3n53 on 2006-04-30
I have just recently installed the nForce drivers in an attempt to make use of my 5.1 sound system but I now have no sound. I followed this guide to install the drivers:
```
http://www.ubuntuforums.org/showthread.php?t=96370&highlight=nvidia+5.1
```

"lspci | grep audio" gives:
```
0000:00:04.0 Multimedia audio controller: nVidia Corporation: Unknown device 0059 (rev a2)
```

My motherboard is a GA-K8NXP-SLI with "Realtek ALC850 Audio AC'97 Codec". Yes I use onboard sound, and it used to work before the nForce update. I have run out of ideas as of now. Any help is appreciated.

---

### Post by C0n5ci3n53 on 2006-04-30
*bump*
Already made it to page 3 >.<

---

### Post by Jason_25 on 2006-04-30
Is snd-intel8x0 still listed by lsmod?  Did you add it to the blacklist?

---

### Post by C0n5ci3n53 on 2006-05-01
It isnt listed by lsmod, I am not sure if it ever was but I added it to the blacklist just to be sure a while back. So I do not think that is the problem.

---

### Post by Jason_25 on 2006-05-01
What apps don't you have sound from?  Just the system apps?  Is nvsound listed by lsmod?

---

### Post by C0n5ci3n53 on 2006-05-01
Yes, it is listed.

```
Module                  Size  Used by
nvsound              1541816  0
soundcore               9184  1 nvsound
ipv6                  217408  8
nvidia               4540724  12
agpgart                32328  1 nvidia
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
i2c_core               19728  2 nvidia,i2c_acpi_ec
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
af_packet              20232  2
nls_utf8                2176  2
nls_cp437               5888  2
vfat                   12288  2
fat                    46492  1 vfat
dm_mod                 50364  0
evdev                   9088  0
sr_mod                 15652  0
sbp2                   21128  0
ieee1394               90936  1 sbp2
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  1
lp                     11460  0
parport                32072  2 parport_pc,lp
ext3                  115976  1
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
usbhid                 30688  0
forcedeth              19072  0
ehci_hcd               29448  0
ohci_hcd               18564  0
usbcore               104316  4 usbhid,ehci_hcd,ohci_hcd
sd_mod                 17424  0
ide_cd                 36996  0
cdrom                  33952  2 sr_mod,ide_cd
ide_disk               16128  7
ide_generic             1664  0
sata_nv                 9092  0
libata                 47876  1 sata_nv
scsi_mod              124872  4 sr_mod,sbp2,sd_mod,libata
amd74xx                12828  1
ide_core              125268  4 ide_cd,ide_disk,ide_generic,amd74xx
unix                   24624  740
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon
```

I do not have any sound at all. If I go to System --> Prefs --> Sound, there is no soundcard listed there.

EDIT: I now have sound using the OSS sink only.

---

### Post by Jason_25 on 2006-05-01
That's the way the driver is supposed to work.  No alsa but it's the only way i've ever gotten spdif out of the realtek/nvidia sound chips.

---

### Post by C0n5ci3n53 on 2006-05-02
Well the sound doesnt work when I boot but I have to manualy start the nvsound device by doing:
```
sudo modprobe nvsound
```

Then the sound works using OSS or gconfaudiosink.

---

### Post by Jason_25 on 2006-05-02
If you add this
```

alias sound-slot-0 nvsound

```
To /etc/modprobe.d/aliases
It will probably work on boot.

---

### Post by John64 on 2006-05-02
you need to switch to OSS.  the Multimedia System Selector on the system=>admin/pref menu.

---

### Post by C0n5ci3n53 on 2006-05-05
Thank you Jason, it now works from boot, and John, I have done that and that had not helped but thank you anyways.

I now have another "problem":
How can I get sound in more then just one application at a time?

---

