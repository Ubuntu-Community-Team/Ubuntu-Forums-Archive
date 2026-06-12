---
title: "screen resolution is low"
date: 2006-06-29
forum: General Help
---

### Post by Lster on 2006-06-29
I haven't yet been able to fix my screen resolution for my laptop. It has a native 1280x800 resolution but ubuntu only allows resolutions up to 1024x768.

I need to change some integral setting probably...

---

### Post by Maggot on 2006-06-29
What video card you have and are the drivers for it working?

---

### Post by Lster on 2006-06-29
I have an ATI mobility radeon 1400 (I think it has 256MB of GDDR2). I think the driver works - how do I know?

---

### Post by Maggot on 2006-06-29
Hmmmm...I have nvidia but I think if you do:

lsmod | grep fglrx

You should get an output of something.

---

### Post by x64Jimbo on 2006-06-29
Not everyone's running the fglrx driver. There's a free one too. The way you can tell if your 3d drivers are installed is if your OpenGL screensavers work. Try opening up kcontrol and "test" one of the OpenGL screensavers. If it works, your 3d driver is installed.

---

### Post by Lster on 2006-06-29
"lsmod" outputs:

Module                  Size  Used by
nls_utf8                2176  1
nls_cp437               5888  1
vfat                   13440  1
fat                    53020  1 vfat
usb_storage            74176  1
ipv6                  265600  6
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
ppdev                   9220  0
speedstep_centrino      8400  1
cpufreq_userspace       4696  1
cpufreq_stats           5636  0
freq_table              4740  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
video                  16260  0
tc1100_wmi              6916  0
sony_acpi               5644  0
pcc_acpi               12416  0
hotkey                 11556  0
dev_acpi               11140  0
container               4608  0
button                  6672  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
i2c_core               21904  1 i2c_acpi_ec
ac                      5252  1 acpi_sbs
dm_mod                 58936  1
md_mod                 72532  0
sbp2                   24196  0
parport_pc             35780  0
lp                     11844  0
parport                36296  3 ppdev,parport_pc,lp
af_packet              22920  2
pcmcia                 40508  0
yenta_socket           28428  1
rsrc_nonstatic         13440  1 yenta_socket
pcmcia_core            42640  3 pcmcia,yenta_socket,rsrc_nonstatic
joydev                 10048  0
tsdev                   8000  0
ipw3945               126492  1
ieee80211              37064  1 ipw3945
ieee80211_crypt         6272  1 ieee80211
usbhid                 38368  0
rtc                    13492  0
tg3                   102020  0
hw_random               5652  0
snd_hda_intel          18964  1
snd_hda_codec         142640  1 snd_hda_intel
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
psmouse                36228  0
snd                    55268  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
serio_raw               7300  0
snd_page_alloc         10632  2 snd_hda_intel,snd_pcm
intel_agp              22940  1
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
agpgart                34888  1 intel_agp
sg                     37920  0
evdev                   9856  1
ext3                  135688  1
jbd                    58772  1 ext3
ide_generic             1536  0
ohci1394               35124  0
ieee1394              299832  2 sbp2,ohci1394
ehci_hcd               32008  0
uhci_hcd               33680  0
usbcore               129668  5 usb_storage,usbhid,ehci_hcd,uhci_hcd
sr_mod                 16932  0
cdrom                  38560  1 sr_mod
sd_mod                 19984  5
generic                 5124  0
ata_piix               11012  6
libata                 78992  1 ata_piix
scsi_mod              139496  6 usb_storage,sbp2,sg,sr_mod,sd_mod,libata
thermal                13576  0
processor              23360  2 speedstep_centrino,thermal
fan                     4868  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit

"grep fglrx" does nothing for about a minute. I pressed Ctrl+C after a while!

---

### Post by Lster on 2006-06-29
By the way, when I try screen savers the 3d ones appear very jerky at about 2fps! Is the driver bad then?

---

### Post by Lster on 2006-06-29
Anyone with any idea?

---

### Post by ahaslam on 2006-06-29
[QUOTE=Lster]Anyone with any idea?[/QUOTE]
Looks like you're running the 'vesa' driver, this limits resoloutions to 1024x768 and you wont have hardware acceleration. Do a search for installing the ATI drivers, I've seen a couple of HOW-TO'S out there.

Good luck.

---

### Post by jnev on 2006-06-29
it'd be easier to know what driver you're using if we can see your xorg.conf.

```
gedit  /etc/X11/xorg.conf
```

---

