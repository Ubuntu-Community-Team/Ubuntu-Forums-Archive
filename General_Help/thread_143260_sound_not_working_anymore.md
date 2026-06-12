---
title: "sound not working anymore"
date: 2006-03-12
forum: General Help
---

### Post by mitjab on 2006-03-12
when i use usermod -G ftpuser username sound stop working
Now in mitjab account sound not working. In root sound works fine. what is wrong? when i click on sound icon i get warning of gstreamer

when i try alsamixergui i get this error

alsamixer: function snd_ctl_open failed for efault: permission default

---

### Post by mitjab on 2006-03-12
any idea why sound stop working and in root works fine

this is my lsmod

lsmod
Module                  Size  Used by
isofs                  32824  0
udf                    75524  0
binfmt_misc            10888  1
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
cpufreq_userspace       4444  0
cpufreq_stats           5124  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
fglrx                 245412  7
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
ipv6                  217408  13
af_packet              20232  2
snd_mpu401              6344  0
snd_mpu401_uart         6784  1 snd_mpu401
snd_rawmidi            22816  1 snd_mpu401_uart
snd_seq_device          8204  1 snd_rawmidi
analog                 10528  0
gameport               14472  1 analog
floppy                 52692  0
pcspkr                  3652  0
rtc                    11832  0
ohci1394               30644  0
shpchp                 80612  0
pci_hotplug            24628  1 shpchp
snd_intel8x0           30144  0
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  10 snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq_ device,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm
i2c_nforce2             6528  0
i2c_core               19728  2 i2c_acpi_ec,i2c_nforce2
nvidia_agp              7964  1
agpgart                32328  2 fglrx,nvidia_agp
nls_cp437               5888  2
ntfs                   92016  2
dm_mod                 50364  1
tsdev                   7616  0
evdev                   9088  0
sr_mod                 15652  0
sbp2                   21128  0
ieee1394               90936  2 ohci1394,sbp2
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  1
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  1
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
8139too                23552  0
8139cp                 18432  0
mii                     5248  2 8139too,8139cp
forcedeth              19072  0
ehci_hcd               29448  0
ohci_hcd               18564  0
usbcore               104316  3 ehci_hcd,ohci_hcd
ide_cd                 36996  0
cdrom                  33952  2 sr_mod,ide_cd
ide_disk               16128  6
ide_generic             1664  0
sata_nv                 9092  0
libata                 47876  1 sata_nv
scsi_mod              124872  3 sr_mod,sbp2,libata
amd74xx                12828  1
ide_core              125268  4 ide_cd,ide_disk,ide_generic,amd74xx
unix                   24624  783
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

---

