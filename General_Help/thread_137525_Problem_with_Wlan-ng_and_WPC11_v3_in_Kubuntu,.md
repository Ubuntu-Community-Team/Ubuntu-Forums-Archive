---
title: "Problem with Wlan-ng and WPC11 v3 in Kubuntu,"
date: 2006-02-28
forum: General Help
---

### Post by KarlGibbs36 on 2006-02-28
hey,

ok heres the situation

ive installed Kubuntu, checked and reintalled

pcmcia-cs
hostap
wlan-ng
and the aircrack suite (aircrack, airodump, aireplay).

i have just got hold of a Linksys WPC11 v3 card (this is the 3rd purchased trying to get this to work)

i install wlan-ng and hostap and i goto the Konsole and type in ifup wlan0 and i get this error message.


====================================================
wlanctl-ng: No such device
Failed to enable the device, exitcode= 1 .
run-parts: /etc/network/if-pre-up.d/linux-wlan-ng-pre-up exited with return code 1
There is already a pid file /var/run/dhclient.wlan0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
sit0: unknown hardware address type 776
Bind socket to interface: No such device
Failed to bring up wlan0.

======================================================

when i execute the commands iwconfig and ifconfig wlan0 doesnt apear in the list.

when executing modprobe prism2_cs i get FATAL: Module prism2_cs not found.

when executing lsmod i get the following, and Prism2_cs isnt listed. the USB driver is there but im using
a PCMCIA card, not USB.

========================================================

Module                  Size  Used by
radeon                 68352  1
drm                    58004  2 radeon
ipv6                  217408  13
binfmt_misc            10888  1
rfcomm                 34972  6
l2cap                  22404  5 rfcomm
speedstep_centrino      7380  1
cpufreq_userspace       4444  1
cpufreq_stats           5124  0
freq_table              4484  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
pcmcia                 24584  2
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
i2c_core               19728  1 i2c_acpi_ec
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
af_packet              20232  2
p80211                 30992  0
rtc                    11832  0
pcspkr                  3652  0
irtty_sir               7808  0
sir_dev                17324  1 irtty_sir
irda                  159804  2 irtty_sir,sir_dev
crc_ccitt               2176  1 irda
wbsd                   15112  0
mmc_core               17924  1 wbsd
hci_usb                13192  6
bluetooth              43012  15 rfcomm,l2cap,hci_usb
yenta_socket           22540  2
rsrc_nonstatic         12032  1 yenta_socket
pcmcia_core            44932  3 pcmcia,yenta_socket,rsrc_nonstatic
ipw2200                92680  0
firmware_class          9472  1 ipw2200
ieee80211              27012  1 ipw2200
ieee80211_crypt         5636  2 ipw2200,ieee80211
ohci1394               30644  0
snd_intel8x0           30144  1
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm
tpm_atmel               5504  0
tpm_nsc                 6528  0
tpm                     9504  2 tpm_atmel,tpm_nsc
pci_hotplug            24628  0
intel_agp              21276  1
agpgart                32328  2 drm,intel_agp
dm_mod                 50364  1
joydev                  9280  0
tsdev                   7616  0
evdev                   9088  1
sr_mod                 15652  0
sbp2                   21128  0
scsi_mod              124872  2 sr_mod,sbp2
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
processor              23100  2 speedstep_centrino,thermal
fan                     4740  0
8139too                23552  0
8139cp                 18432  0
mii                     5248  2 8139too,8139cp
ehci_hcd               29448  0
uhci_hcd               28048  0
usbcore               104188  4 hci_usb,ehci_hcd,uhci_hcd
ide_cd                 36996  0
cdrom                  33952  2 sr_mod,ide_cd
ide_disk               16128  3
ide_generic             1664  0
piix                    9476  1
ide_core              125268  4 ide_cd,ide_disk,ide_generic,piix
unix                   24624  453
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

=========================================================


after trying for 5 weeks solid at this, going to chat rooms, google, even reading through what is posted here, and buying 3 different cards in the process, i am really F****d of at the moment.

i want to use the card with aireplay to test the security of my wifi network at my house. by googling it i need a card with a prism2 chipset and wlan-ng in order to preform packet injection to speed the process up. 

could someone please please take me through this right from the begining.

cheers

---

### Post by az on 2006-02-28
You compiled linux-wlan-ng from source?   Because by default, the kernel will try to use the orinoco drivers for prism2_cs hardware.

---

### Post by KarlGibbs36 on 2006-02-28
i didnt compile wlan-ng from source, i used apt-get, plus ive read up that the orinco_cs dirvers work with the card, but i want the prism 2 drivers,

---

### Post by az on 2006-02-28
[QUOTE=KarlGibbs36]i didnt compile wlan-ng from source, i used apt-get, plus ive read up that the orinco_cs dirvers work with the card, but i want the prism 2 drivers,[/QUOTE]

Installing the linux-wlan-ng package only gives you the userspace tools neede to run the prism2_usb module.  The orinoco driver does not provide a usb module so that's why prism2_usb is used..  All the other prism2 modules are not included in the kernel.  You would need to build them yourself from source.

There are three drivers for the prism2 devices, orinoco, hostap and linux-wlan-ng.  Ubuntu only includes one driver for a device.  Orinoco being the oldest and most stable, is the one used.

---

### Post by KarlGibbs36 on 2006-03-01
do you know where i can get the Prism2_cs drivers from and, how to install them, then use them with your device (if it doesnt do it automatically)

---

