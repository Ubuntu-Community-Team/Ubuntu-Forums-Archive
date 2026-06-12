---
title: "Mount usbdisk fails after compiling new kernel"
date: 2006-06-16
forum: General Help
---

### Post by mucha on 2006-06-16
After I compiled a new kernel my usbdisks will not (auto)mount. They doesn't show up att all in /dev/sda*. But works perfect in an ubuntu-kernel. Any suggestions?

Dmesg:
> [4294984.771000] usb-storage: device found at 5
[4294984.771000] usb-storage: waiting for device to settle before scanning
[4294989.772000]   Vendor: MATSHITA  Model: DMC-LC80          Rev: 0100
[4294989.772000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[4294989.772000] usb-storage: device scan complete

---

### Post by Rui Pais on 2006-06-16
Hi, 
are you sure you not forgot anything on Usb Support section?
Whats the output of 
```
cat config | grep USB | grep "="
```?

---

### Post by mucha on 2006-06-16
I may forgot something, but I compiled by the old config

> /usr/src/linux$ cat .config | grep USB | grep "="
CONFIG_USBPCWATCHDOG=m
CONFIG_VIDEO_CPIA_USB=m
CONFIG_USB_ARCH_HAS_HCD=y
CONFIG_USB_ARCH_HAS_OHCI=y
CONFIG_USB=m
CONFIG_USB_DEVICEFS=y
CONFIG_USB_BANDWIDTH=y
CONFIG_USB_EHCI_HCD=m
CONFIG_USB_OHCI_HCD=m
CONFIG_USB_OHCI_LITTLE_ENDIAN=y
CONFIG_USB_UHCI_HCD=m
CONFIG_USB_SL811_HCD=m
CONFIG_USB_PRINTER=m
CONFIG_USB_STORAGE=m
CONFIG_USB_STORAGE_DATAFAB=y
CONFIG_USB_STORAGE_FREECOM=y
CONFIG_USB_STORAGE_ISD200=y
CONFIG_USB_STORAGE_DPCM=y
CONFIG_USB_STORAGE_USBAT=y
CONFIG_USB_STORAGE_SDDR09=y
CONFIG_USB_STORAGE_SDDR55=y
CONFIG_USB_STORAGE_JUMPSHOT=y
CONFIG_USB_HID=m
CONFIG_USB_HIDINPUT=y
CONFIG_USB_HIDDEV=y
CONFIG_USB_KBD=m
CONFIG_USB_MOUSE=m
CONFIG_USB_AIPTEK=m
CONFIG_USB_WACOM=m
CONFIG_USB_ACECAD=m
CONFIG_USB_KBTAB=m
CONFIG_USB_POWERMATE=m
CONFIG_USB_MDC800=m
CONFIG_USB_DABUSB=m
CONFIG_USB_VICAM=m
CONFIG_USB_DSBR=m
CONFIG_USB_IBMCAM=m
CONFIG_USB_KONICAWC=m
CONFIG_USB_OV511=m
CONFIG_USB_SE401=m
CONFIG_USB_SN9C102=m
CONFIG_USB_STV680=m
CONFIG_USB_W9968CF=m
CONFIG_USB_PWC=m
CONFIG_USB_CATC=m
CONFIG_USB_KAWETH=m
CONFIG_USB_PEGASUS=m
CONFIG_USB_RTL8150=m
CONFIG_USB_USBNET=m
CONFIG_USB_NET_AX8817X=m
CONFIG_USB_NET_CDCETHER=m
CONFIG_USB_NET_GL620A=m
CONFIG_USB_NET_NET1080=m
CONFIG_USB_NET_PLUSB=m
CONFIG_USB_NET_RNDIS_HOST=m
CONFIG_USB_NET_CDC_SUBSET=m
CONFIG_USB_ALI_M5632=y
CONFIG_USB_AN2720=y
CONFIG_USB_BELKIN=y
CONFIG_USB_ARMLINUX=y
CONFIG_USB_EPSON2888=y
CONFIG_USB_NET_ZAURUS=m
CONFIG_USB_MON=y
CONFIG_USB_USS720=m
CONFIG_USB_SERIAL=m
CONFIG_USB_SERIAL_GENERIC=y
CONFIG_USB_SERIAL_AIRPRIME=m
CONFIG_USB_SERIAL_ANYDATA=m
CONFIG_USB_SERIAL_BELKIN=m
CONFIG_USB_SERIAL_WHITEHEAT=m
CONFIG_USB_SERIAL_DIGI_ACCELEPORT=m
CONFIG_USB_SERIAL_CP2101=m
CONFIG_USB_SERIAL_CYPRESS_M8=m
CONFIG_USB_SERIAL_EMPEG=m
CONFIG_USB_SERIAL_FTDI_SIO=m
CONFIG_USB_SERIAL_VISOR=m
CONFIG_USB_SERIAL_IPAQ=m
CONFIG_USB_SERIAL_IR=m
CONFIG_USB_SERIAL_EDGEPORT=m
CONFIG_USB_SERIAL_EDGEPORT_TI=m
CONFIG_USB_SERIAL_GARMIN=m
CONFIG_USB_SERIAL_IPW=m
CONFIG_USB_SERIAL_KEYSPAN_PDA=m
CONFIG_USB_SERIAL_KEYSPAN=m
CONFIG_USB_SERIAL_KLSI=m
CONFIG_USB_SERIAL_KOBIL_SCT=m
CONFIG_USB_SERIAL_MCT_U232=m
CONFIG_USB_SERIAL_PL2303=m
CONFIG_USB_SERIAL_HP4X=m
CONFIG_USB_SERIAL_SAFE=m
CONFIG_USB_SERIAL_TI=m
CONFIG_USB_SERIAL_CYBERJACK=m
CONFIG_USB_SERIAL_XIRCOM=m
CONFIG_USB_SERIAL_OMNINET=m
CONFIG_USB_EZUSB=y
CONFIG_USB_EMI62=m
CONFIG_USB_EMI26=m
CONFIG_USB_AUERSWALD=m
CONFIG_USB_RIO500=m
CONFIG_USB_LEGOTOWER=m
CONFIG_USB_CYTHERM=m
CONFIG_USB_PHIDGETKIT=m
CONFIG_USB_PHIDGETSERVO=m
CONFIG_USB_SISUSBVGA=m
CONFIG_USB_LD=m
CONFIG_USB_TEST=m
CONFIG_USB_GADGET=m
CONFIG_USB_GADGET_SELECTED=y
CONFIG_USB_GADGET_NET2280=y
CONFIG_USB_NET2280=m
CONFIG_USB_GADGET_DUALSPEED=y
CONFIG_USB_ZERO=m
CONFIG_USB_ETH=m
CONFIG_USB_ETH_RNDIS=y
CONFIG_USB_GADGETFS=m
CONFIG_USB_FILE_STORAGE=m
CONFIG_USB_G_SERIAL=m

---

### Post by Rui Pais on 2006-06-16
hi,
sorry, seems ok. I can't see nothig important missing...

Maybe trying to boot with both kernels and take note of lsmod output to see if some module is not loading with one of them.

---

### Post by mucha on 2006-06-17
Here is the output of lsmod by the both kernels:

The one that's working:
> Module                  Size  Used by
binfmt_misc            12296  1 
ppdev                   9220  0 
cpufreq_userspace       4696  0 
cpufreq_stats           5636  0 
freq_table              4740  1 cpufreq_stats
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
ac                      5252  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
nls_utf8                2176  1 
ntfs                  103536  1 
dm_mod                 58936  1 
sr_mod                 16932  0 
sbp2                   24196  0 
lp                     11844  0 
parport_pc             35780  1 
parport                36296  3 ppdev,lp,parport_pc
floppy                 62148  0 
nvidia               4550772  20 
agpgart                34888  1 nvidia
tsdev                   8000  0 
sky2                   39684  0 
pcspkr                  2180  0 
rtc                    13492  0 
snd_usb_audio          78784  0 
snd_usb_lib            16640  1 snd_usb_audio
snd_rawmidi            25504  1 snd_usb_lib
snd_seq_device          8716  1 snd_rawmidi
snd_hwdep               9376  1 snd_usb_audio
psmouse                36100  0 
serio_raw               7300  0 
snd_intel8x0           33692  1 
snd_ac97_codec         92704  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0 
snd_mixer_oss          18688  2 snd_pcm_oss
quickcam               77860  0 
snd_pcm                89864  4 snd_usb_audio,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
videodev                9856  1 quickcam
i2c_nforce2             6912  0 
snd                    55268  10 snd_usb_audio,snd_rawmidi,snd_seq_device,snd_hwdep,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  2 snd
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm
shpchp                 45632  0 
pci_hotplug            29236  1 shpchp
usbhid                 39904  0 
i2c_core               21904  3 i2c_acpi_ec,nvidia,i2c_nforce2
usblp                  13056  0 
ipv6                  265728  6 
evdev                   9856  2 
ext3                  135688  5 
jbd                    58772  1 ext3
ide_generic             1536  0 
ohci1394               35124  0 
ieee1394              299832  2 sbp2,ohci1394
uhci_hcd               33680  0 
forcedeth              23428  0 
ehci_hcd               34184  0 
ohci_hcd               21892  0 
usbcore               130692  9 snd_usb_audio,snd_usb_lib,quickcam,usbhid,usblp,uhci_hcd,ehci_hcd,ohci_hcd
sata_sil                9348  0 
ide_cd                 33028  0 
cdrom                  38560  2 sr_mod,ide_cd
ide_disk               17664  10 
generic                 5124  0 
amd74xx                15132  0 [permanent]
sata_nv                 9604  0 
libata                 78992  2 sata_sil,sata_nv
scsi_mod              139496  3 sr_mod,sbp2,libata
thermal                13576  0 
processor              23360  1 thermal
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


The one that's **not** working:
> Module                  Size  Used by
vmnet                  34084  13 
vmmon                 109528  0 
quickcam               72356  0 
videodev                9600  1 quickcam
usb_storage            73536  0 
binfmt_misc            11656  1 
ppdev                   9732  0 
cpufreq_userspace       4244  0 
cpufreq_stats           5252  0 
freq_table              4740  1 cpufreq_stats
cpufreq_powersave       1920  0 
cpufreq_ondemand        6172  0 
cpufreq_conservative     6948  0 
video                  15364  0 
button                  6672  0 
container               4480  0 
nls_utf8                2304  1 
ntfs                  110580  1 
dm_mod                 56244  1 
sbp2                   21892  0 
scsi_mod               95560  2 usb_storage,sbp2
lp                     12224  0 
parport_pc             36080  1 
parport                37576  3 ppdev,lp,parport_pc
psmouse                40584  0 
floppy                 64556  0 
pcspkr                  3332  0 
rtc                    12852  0 
serio_raw               7428  0 
nvidia               4551124  20 
agpgart                32944  1 nvidia
sky2                   37632  0 
usblp                  14080  0 
usbhid                 39136  0 
snd_intel8x0           32796  3 
snd_ac97_codec         96672  1 snd_intel8x0
snd_ac97_bus            2432  1 snd_ac97_codec
snd_pcm_oss            52384  0 
snd_mixer_oss          18688  2 snd_pcm_oss
snd_pcm                87560  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23428  2 snd_pcm
snd                    52736  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9568  2 snd
snd_page_alloc         11144  2 snd_intel8x0,snd_pcm
i2c_nforce2             7040  0 
i2c_core               21904  2 nvidia,i2c_nforce2
ipv6                  263008  8 
evdev                  10112  2 
ext3                  139016  5 
jbd                    54804  1 ext3
mbcache                 8580  1 ext3
ide_generic             1408  0 [permanent]
forcedeth              23940  0 
ohci1394               34608  0 
ieee1394              300344  2 sbp2,ohci1394
uhci_hcd               31504  0 
ehci_hcd               29832  0 
ohci_hcd               20356  0 
usbcore               128672  8 quickcam,usb_storage,usblp,usbhid,uhci_hcd,ehci_hcd,ohci_hcd
ide_cd                 41760  1 
cdrom                  38576  1 ide_cd
ide_disk               17280  10 
generic                 4484  0 [permanent]
amd74xx                14748  0 [permanent]
thermal                13320  0 
processor              21824  1 thermal
fan                     4740  0 
vga16fb                12808  1 
vgastate                9344  1 vga16fb


---

### Post by Rui Pais on 2006-06-17
hi,

the only thing different that seem that could have some importance is that your non-work kernel is loading usb_storage and not sr_mod, sata_sil, sata_nv and libsata while the working one do exactly the opposite. 

Try to add sata_sil, sata_nv (this one should not be relevant... but in anycase) and sr_mod to your cat /etc/modules and see if that changes anything.

By the way, you are trying to automount usb disks (external?) not usb pens isn't it?

---

### Post by mucha on 2006-06-17
[QUOTE=Rui Pais]By the way, you are trying to automount usb disks (external?) not usb pens isn't it?[/QUOTE]

Ops sorry, I didn't thought it would matter so much. I mean usb pens, like memorycards to cameras and mobiletelephones. Don't really know if I can mount external disks.

---

### Post by Rui Pais on 2006-06-17
Hi, i was just wondering what kind of usbdisks you want mounting. 
My pens automounts loading usb_storage and sd_mod... thats why i ask...

Did loading sr_mod work?

---

### Post by mucha on 2006-06-17
sr_mod is in /etc/modules but I don't see it in lsmod. What can that depend on?

---

### Post by Rui Pais on 2006-06-18
[QUOTE=mucha]sr_mod is in /etc/modules but I don't see it in lsmod. What can that depend on?[/QUOTE]
hi, strange...
```
sudo modprobe sr_mod
``` gives you any error?

anyway there must be something wrong because those modules should be automaticaly loaded when inserted the pen

---

### Post by mucha on 2006-06-18
I get these errors when I do that:
> ~$ sudo modprobe sr_mod
Password:
FATAL: Module sr_mod not found.

---

### Post by Rui Pais on 2006-06-18
hi,
no, sorry, i was just shooting in the dark... sr_mod is for scsi cdroms sould have nothing to do with your problem. :( I just mention that one cause it was on the list of the working kernel but missing in the non-working.

I check my list of loaded modules and using usb_storage the one that should be loaded is sd_mod thats for scsi disk support (generic disk drives, not only cdrom drives) 

so it should be
```
sudo modprobe sd_mod 
```
instead of sr_mod... Anyway it must be compiled as module or inside kernel. 
If it was not automaticly loaded maybe you have forget that one.

---

### Post by mucha on 2006-06-18
Thanks for your help :), now it works fine!

---

### Post by Rui Pais on 2006-06-19
no problem, 

sorry about my sr_mod -> sd_mod mistake, it would be faster to get the solution without it... 

anyway, glad it works :)

---

