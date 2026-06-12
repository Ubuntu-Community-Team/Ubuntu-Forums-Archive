---
title: "How are modules loaded?"
date: 2006-06-28
forum: General Help
---

### Post by s10case on 2006-06-28
Hi,

I am trying to not load one module, and to load another, but am not succeeding at either  :(

So, here is the situation:

I want to NOT load "snd_hda_intel" at bootup but I can not find where or how it is being loaded. The only place I know to look is in the files under /etc/modprobe.d/

When I look in the files in there, I have been unable to figure out where that module is being loaded...what am I missing?

I want TO load the nvsound module at bootup. To achieve this, I followed the directions on the release notes that came with my motherboard driver disk. Eventually, I ended up with a successfully installed nvsound driver, and a file in /etc/modprobe.d/ which I called "nforce" with the following contents:

```

alias sound-slot-0 nvsound
alias snd-intel8x0 off
alias i810_audio off

install nvsound /sbin/modprobe --ignore-install nvsound ; sleep 1; /usr/bin/nvmix-reg -f /etc/nvmixrc -L >/dev/null 2>&1 || :
remove nvsound { /usr/bin/nvmix-reg -f /etc/nvmixrc -S >/dev/null 2>&1 || : ; }; /sbin/modprobe -r --ignore-remove nvsound

```

If I load the nforce module by hand using

```
modprobe nvsound
```

the module loads just fine, however I suspect it is not being used because of the intel driver.

So, to summarize my questions,

1. How do I stop snd_hda_intel from loading?
2. How do I make nvsound load at bootup?

Here is some information that may be useful:

```

s10case@Armand:~$ lsmod
Module                  Size  Used by
rfcomm                 45600  0
l2cap                  30464  5 rfcomm
bluetooth              59268  4 rfcomm,l2cap
ppdev                  11400  0
cpufreq_userspace       9184  0
cpufreq_stats           8264  0
freq_table              6464  1 cpufreq_stats
cpufreq_powersave       3328  0
cpufreq_ondemand        9768  0
cpufreq_conservative    10984  0
video                  18824  0
tc1100_wmi              9096  0
sony_acpi               7188  0
pcc_acpi               16128  0
hotkey                 13768  0
dev_acpi               15364  0
container               6272  0
button                  8864  0
acpi_sbs               24600  0
battery                12296  1 acpi_sbs
ac                      7176  1 acpi_sbs
i2c_acpi_ec             7040  1 acpi_sbs
i2c_core               26624  1 i2c_acpi_ec
af_packet              28172  0
dm_mod                 63176  1
md_mod                 76792  0
sr_mod                 19748  0
sbp2                   27908  0
lp                     15040  0
snd_hda_intel          21664  1
snd_hda_codec         175048  1 snd_hda_intel
analog                 13024  0
snd_pcm_oss            59424  0
snd_mixer_oss          20608  1 snd_pcm_oss
gameport               19216  1 analog
snd_pcm               104584  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              29064  1 snd_pcm
snd_page_alloc         13968  2 snd_hda_intel,snd_pcm
snd_mpu401              9608  0
snd_mpu401_uart        10368  1 snd_mpu401
snd_rawmidi            31648  1 snd_mpu401_uart
snd_seq_device         11280  1 snd_rawmidi
snd                    68576  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore              13216  1 snd
floppy                 74120  0
parport_pc             40816  1
parport                44172  3 ppdev,lp,parport_pc
nvnet                  78504  0
pcspkr                  3592  0
psmouse                40324  0
serio_raw               9732  0
ipv6                  300416  8
shpchp                 51360  0
pci_hotplug            33168  1 shpchp
sg                     43696  0
evdev                  14464  1
tsdev                  10240  0
ext3                  145936  1
jbd                    70952  1 ext3
usbhid                 43040  0
ide_generic             2816  0
ohci1394               37324  0
forcedeth              27908  0
ieee1394              369048  2 sbp2,ohci1394
ehci_hcd               36232  0
ohci_hcd               23684  0
usbcore               147004  4 usbhid,ehci_hcd,ohci_hcd
ide_cd                 35744  0
cdrom                  41144  2 sr_mod,ide_cd
generic                 7300  0
amd74xx                16944  0 [permanent]
sd_mod                 21504  3
sata_nv                12420  4
libata                 85536  1 sata_nv
scsi_mod              160504  5 sr_mod,sbp2,sg,sd_mod,libata
thermal                16524  0
processor              29224  1 thermal
fan                     6408  0
capability              7176  0
commoncap               9728  1 capability
vga16fb                15120  1
cfbcopyarea             5120  1 vga16fb
vgastate               10368  1 vga16fb
cfbimgblt               4224  1 vga16fb
cfbfillrect             5760  1 vga16fb
fbcon                  43136  72
tileblit                4096  1 fbcon
font                    9984  1 fbcon
bitblit                 7424  1 fbcon
softcursor              3712  1 bitblit

```

```

s10case@Armand:~$ lspci
0000:00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
0000:00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
0000:00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
0000:00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
0000:00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
0000:00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
0000:00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
0000:00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
0000:00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
0000:00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
0000:00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
0000:00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2)
0000:00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
0000:00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
0000:00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
0000:00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
0000:00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
0000:00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
0000:00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
0000:00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
0000:00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
0000:00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
0000:00:10.1 0403: nVidia Corporation MCP51 High Definition Audio (rev a2)
0000:00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:04:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)

```

Thanks for your help!!

Mike

---

### Post by jocko on 2006-06-28
Add this line to /etc/modprobe.d/blacklist:
```
blacklist snd_hda_intel
```

---

### Post by s10case on 2006-06-28
[QUOTE=jocko]Add this line to /etc/modprobe.d/blacklist:
```
blacklist snd_hda_intel
```[/QUOTE]


I tried that, and it stopped the driver from loading, but sound just stopped working. nvsound still didn't load.

Also, I am curious about how it is loaded, nut just how to stop it from loading...

---

### Post by az on 2006-06-28
[QUOTE=s10case]how it is loaded, nut just how to stop it from loading...[/QUOTE]

Hotplug has been replcaced by udev and HAL.  They autodetect your hardware and make it work.

Some other modules are loaded by the initrd (ram disk at boot time) and still use discover.  But not your sound modules.

---

