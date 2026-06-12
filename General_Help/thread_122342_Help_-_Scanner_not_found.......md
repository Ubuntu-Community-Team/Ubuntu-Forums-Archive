---
title: "Help - Scanner not found...... ??"
date: 2006-01-27
forum: General Help
---

### Post by MJSOnline on 2006-01-27
Hi all.

How do I make Ubuntu detect my scanner, part of the HP 3320 printer I have? I went to Xsane to scan a document. but it says no device found..

---

### Post by MJSOnline on 2006-01-27
Anyone? Matthew

---

### Post by Tibor60 on 2006-01-27
I have the same problem, with my HP Scanjet 6300C SCSI scanner, Ubuntu can not find. It works on Windows, and SUSE and UHU linux on the same PC. Help please!

---

### Post by Rumpty on 2006-01-28
I had to change permissions of the file /dev/sg0. Try giving rw permission to "others". That might work for you, but I am far from being an expert!

---

### Post by Tibor60 on 2006-01-28
There is no "sg0" file in my /dev directory:(

---

### Post by Tibor60 on 2006-01-28
My scanner can connect by USB or SCSI, but to this time only in WINDOWS.In Ubuntu I tried both, the scanner is not detected, not in USB and not in SCSI.
In boot the BIOS detects the SCSI card, and the scanner, too. But in ubuntu both is invisible.I think firts I should solve the problem to detect the SCSI card... but how to do this?

---

### Post by installer on 2006-01-28
My Agfa scanner either was not detected or gave errors when trying to use Xsane, installing the shareware program VueScan solved my problems and although the trial period has gone (I left Vuescan installed) and XSane continues to work fine.

---

### Post by MJSOnline on 2006-01-28
hm.. Tried that.  My HP 3320 is a MFD that conets to my pc via ethernet, thro my router. Still cant figuire it out. Matthew

---

### Post by lsiden on 2006-06-25
[QUOTE=Tibor60]There is no "sg0" file in my /dev directory:([/QUOTE]

I have the exact same problem - unless I boot with the scanner on.  I have the modules sg and scsi_mod loaded.  FWIW, here's a sorted dump of lsmod on my system.  Does anyone have a clue what I need to do to let xsane find the scanner without having to first reboot the system?

ac                      5252  1 acpi_sbs
acpi_sbs               19980  0
agpgart                34888  2 nvidia,nvidia_agp
aic7xxx               183124  0
amd74xx                15132  0 [permanent]
analog                 12320  0
battery                 9988  1 acpi_sbs
bitblit                 6272  1 fbcon
bluetooth              49892  4 rfcomm,l2cap
button                  6672  0
capability              5000  0
cdrom                  38560  1 ide_cd
commoncap               7296  1 capability
container               4608  0
cpufreq_conservative     7332  0
cpufreq_ondemand        6428  0
cpufreq_powersave       1920  0
cpufreq_stats           5636  0
cpufreq_userspace       4696  0
dev_acpi               11140  0
dm_mod                 58936  1
ehci_hcd               34184  0
evdev                   9856  1
exportfs                6272  1 nfsd
fan                     4868  0
fat                    53020  1 vfat
fbcon                  42784  72
floppy                 62148  0
font                    8320  1 fbcon
forcedeth              23428  0
freq_table              4740  1 cpufreq_stats
fuse                   38412  0
gameport               15496  1 analog
generic                 5124  0
hotkey                 11556  0
i2c_acpi_ec             5120  1 acpi_sbs
i2c_core               21904  3 i2c_acpi_ec,nvidia,i2c_nforce2
i2c_nforce2             6912  0
ide_cd                 33028  0
ide_disk               17664  3
ide_generic             1536  0
ipv6                  265728  6
l2cap                  26244  5 rfcomm
libata                 78992  1 sata_nv
lockd                  62216  2 nfsd
lp                     11844  0
md_mod                 72532  0
Module                  Size  Used by
nfsd                  228612  13
nls_cp437               5888  0
nls_utf8                2176  0
nvidia               4550772  0
nvidia_agp              8348  1
ohci_hcd               21892  0
parport                36296  3 ppdev,lp,parport_pc
parport_pc             35780  1
pcc_acpi               12416  0
pci_hotplug            29236  1 shpchp
pcmcia_core            42640  1 rsrc_nonstatic
pcspkr                  2180  0
ppdev                   9220  0
processor              23360  1 thermal
psmouse                36100  0
reiserfs              268016  1
rfcomm                 40216  0
rsrc_nonstatic         13440  0
rtc                    13492  0
sata_nv                 9604  0
scsi_mod              139496  6 sg,sd_mod,usb_storage,libata,aic7xxx,scsi_transport_spi2
scsi_transport_spi2    24960  1 aic7xxx
sd_mod                 19984  0
serio_raw               7300  0
sg                     37920  0
shpchp                 45632  0
snd                    55268  12 snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
snd_ac97_bus            2304  1 snd_ac97_codec
snd_ac97_codec         92704  1 snd_intel8x0
snd_intel8x0           33692  2
snd_mixer_oss          18688  3 snd_pcm_oss
snd_mpu401              6728  1
snd_mpu401_uart         7808  1 snd_mpu401
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm
snd_pcm                89864  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_pcm_oss            53664  0
snd_rawmidi            25504  1 snd_mpu401_uart
snd_seq_device          8716  1 snd_rawmidi
snd_timer              25220  1 snd_pcm
softcursor              2304  1 bitblit
sony_acpi               5644  0
soundcore              10208  3 snd
sunrpc                150332  8 nfsd,lockd
tc1100_wmi              6916  0
thermal                13576  0
tileblit                2816  1 fbcon
tsdev                   8000  0
usbcore               130692  5 usb_storage,usbhid,ehci_hcd,ohci_hcd
usbhid                 39904  0
usb_storage            74176  0
vfat                   13440  0
vga16fb                13704  1
vgastate               10368  1 vga16fb
video                  16260  0

---

