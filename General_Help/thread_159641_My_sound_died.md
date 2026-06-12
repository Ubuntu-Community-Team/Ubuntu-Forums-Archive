---
title: "My sound died"
date: 2006-04-13
forum: General Help
---

### Post by psiko on 2006-04-13
I tried to get a joystick working on my amd64. It had sound. I tried to follow [this howto]("http://gentoo-wiki.com/HOWTO_Joystick_Setup") without the part of kernel compiling. I have unplugged the joystick and I rebooted two times and the sound remains off. Alsa, esd, artsd don't work, so I think It's a hardware problem.
Can you help me ?

> # lsmod
Module                  Size  Used by
binfmt_misc            13004  1
rfcomm                 39856  0
l2cap                  25672  5 rfcomm
bluetooth              52036  4 rfcomm,l2cap
cpufreq_userspace       5456  0
cpufreq_stats           6088  0
freq_table              5320  1 cpufreq_stats
cpufreq_powersave       2240  0
cpufreq_ondemand        7340  0
cpufreq_conservative     8364  0
video                  17288  0
tc1100_wmi              8008  0
sony_acpi               6104  0
pcc_acpi               13568  0
hotkey                 10568  0
dev_acpi               14788  0
i2c_acpi_ec             6400  0
button                  7776  0
battery                10568  0
container               5120  0
ac                      5640  0
ipv6                  266176  8
af_packet              23692  2
analog                 11616  0
gameport               16840  1 analog
snd_mpu401              8328  0
snd_mpu401_uart         8128  1 snd_mpu401
snd_rawmidi            28384  1 snd_mpu401_uart
snd_seq_device          9872  1 snd_rawmidi
floppy                 66616  0
pcspkr                  4048  0
ohci1394               34252  0
snd_intel8x0           35968  2
snd_ac97_codec         92376  1 snd_intel8x0
snd_pcm_oss            55008  1
snd_mixer_oss          18880  1 snd_pcm_oss
snd_pcm                97036  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25352  1 snd_pcm
snd                    59560  12 snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  2 snd
snd_page_alloc         11856  2 snd_intel8x0,snd_pcm
i2c_nforce2             7936  0
i2c_core               24152  2 i2c_acpi_ec,i2c_nforce2
reiserfs              239088  1
nls_iso8859_1           5568  2
nls_cp437               7296  2
vfat                   14720  2
fat                    54000  1 vfat
dm_mod                 59128  1
evdev                  11008  0
tsdev                   9152  0
nvidia               4384100  12
sr_mod                 18468  0
sbp2                   25416  0
ieee1394              366584  2 ohci1394,sbp2
rtc                    13960  0
psmouse                29572  0
mousedev               13220  1
parport_pc             37736  1
lp                     13960  0
parport                40460  2 parport_pc,lp
md                     46272  0
ext3                  135888  3
jbd                    58480  1 ext3
mbcache                10824  1 ext3
thermal                14992  0
processor              25556  1 thermal
fan                     5256  0
skge                   38736  0
sata_sil               11332  0
forcedeth              23360  0
ehci_hcd               33864  0
ohci_hcd               21252  0
sd_mod                 19480  8
ide_cd                 43296  0
cdrom                  39400  2 sr_mod,ide_cd
ide_generic             1792  0
sata_nv                10884  14
libata                 56072  2 sata_sil,sata_nv
scsi_mod              151920  4 sr_mod,sbp2,sd_mod,libata
amd74xx                15280  1
ide_core              157188  3 ide_cd,ide_generic,amd74xx
unix                   30072  656
vesafb                  9252  0
capability              6088  0
commoncap               8576  1 capability
vga16fb                12864  1
vgastate                9344  1 vga16fb
softcursor              2880  2 vesafb,vga16fb
cfbimgblt               3264  2 vesafb,vga16fb
cfbfillrect             4864  2 vesafb,vga16fb
cfbcopyarea             4352  2 vesafb,vga16fb
fbcon                  38272  72
tileblit                2880  1 fbcon
font                    9024  1 fbcon
bitblit                 6080  1 fbcon


---

