---
title: "Sound just vanished"
date: 2010-02-01
forum: General Help
---

### Post by Jim Lewis on 2010-02-01
I'm using U. 8.10 and, until yesterday, was happy.

Then, my video sound simply vanished.  Nothing was changed (by me) and no one else uses the machine.  Nothing is muted.  I've been into Preferences - sound; all appears to be well.  I do NOT use beeps and such for keyboard commands, so THEY are all off.

I've clicked the "Master" icon, everything is supposed to be "on."

My speakers are set to high volume.  They are plugged in correctly.

There have been a couple of automatic (presumably) security updates recently, requiring a restart, but I don't know if I'd needed sound for anything since, until now.

---

### Post by [pl]ice on 2010-02-01
hi dude,
1) Go to terminal and type: uname -a.
2) ls /boot/  and see if there is a higher version of the kernel 
3) lsmod
better to post the results here.

 I think that after an upgrade, a box popped up to update your /boot/grub/menu.cnf (can't remeber file name) to the newest kernel, but you clicked  'don't change anything' now you will be using older kernel that's why it won't load the sound modules. That's my guess, happened to few of us.

---

### Post by Jim Lewis on 2010-02-01
Thanks.  Here's what I got.  It's all Greek to me:

jim@jim-desktop:~$ uname -a
Linux jim-desktop 2.6.27-16-generic #1 SMP Tue Dec 1 17:56:54 UTC 2009 i686 GNU/Linux
jim@jim-desktop:~$ 
jim@jim-desktop:~$ 
jim@jim-desktop:~$ 
jim@jim-desktop:~$ ls /boot/
abi-2.6.27-11-generic         memtest86+.bin
abi-2.6.27-14-generic         System.map-2.6.27-11-generic
abi-2.6.27-15-generic         System.map-2.6.27-14-generic
abi-2.6.27-16-generic         System.map-2.6.27-15-generic
abi-2.6.27-7-generic          System.map-2.6.27-16-generic
abi-2.6.27-9-generic          System.map-2.6.27-7-generic
config-2.6.27-11-generic      System.map-2.6.27-9-generic
config-2.6.27-14-generic      vmcoreinfo-2.6.27-11-generic
config-2.6.27-15-generic      vmcoreinfo-2.6.27-14-generic
config-2.6.27-16-generic      vmcoreinfo-2.6.27-15-generic
config-2.6.27-7-generic       vmcoreinfo-2.6.27-16-generic
config-2.6.27-9-generic       vmcoreinfo-2.6.27-7-generic
grub                          vmcoreinfo-2.6.27-9-generic
initrd.img-2.6.27-11-generic  vmlinuz-2.6.27-11-generic
initrd.img-2.6.27-14-generic  vmlinuz-2.6.27-14-generic
initrd.img-2.6.27-15-generic  vmlinuz-2.6.27-15-generic
initrd.img-2.6.27-16-generic  vmlinuz-2.6.27-16-generic
initrd.img-2.6.27-7-generic   vmlinuz-2.6.27-7-generic
initrd.img-2.6.27-9-generic   vmlinuz-2.6.27-9-generic
jim@jim-desktop:~$ 
jim@jim-desktop:~$ 
jim@jim-desktop:~$ 
jim@jim-desktop:~$ lsmod
Module                  Size  Used by
ipv6                  264356  10 
af_packet              25856  2 
binfmt_misc            16904  1 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20352  2 
rfcomm                 44432  0 
sco                    18308  2 
l2cap                  30464  6 bnep,rfcomm
bluetooth              62180  6 bnep,rfcomm,sco,l2cap
ppdev                  15748  0 
cpufreq_stats          13188  0 
cpufreq_userspace      11396  0 
cpufreq_conservative    14600  0 
cpufreq_ondemand       14988  0 
cpufreq_powersave       9856  0 
freq_table             12672  2 cpufreq_stats,cpufreq_ondemand
pci_slot               12680  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
wmi                    14504  0 
container              11520  0 
video                  25488  0 
output                 11008  1 video
battery                18436  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ac                     12292  0 
lp                     17156  0 
snd_hda_intel         385072  5 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  3 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
psmouse                45200  0 
evdev                  17696  6 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
serio_raw              13444  0 
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
pcspkr                 10624  0 
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
k8temp                 12416  0 
snd                    63396  18 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
usblp                  20480  0 
parport_pc             39332  1 
parport                42604  3 ppdev,lp,parport_pc
i2c_nforce2            14468  0 
button                 14224  0 
nvidia               7103300  24 
agpgart                42184  1 nvidia
i2c_core               31892  2 i2c_nforce2,nvidia
shpchp                 38036  0 
pci_hotplug            34976  1 shpchp
ext3                  133384  1 
jbd                    55956  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42392  3 
crc_t10dif              9984  1 sd_mod
pata_amd               18564  2 
ata_generic            12932  0 
sg                     39732  0 
usb_storage            83392  0 
libusual               29972  1 usb_storage
sata_nv                30984  0 
pata_acpi              12160  0 
libata                178336  4 pata_amd,ata_generic,sata_nv,pata_acpi
forcedeth              61456  0 
scsi_mod              155468  5 sr_mod,sd_mod,sg,usb_storage,libata
dock                   16656  1 libata
ehci_hcd               43788  0 
ohci_hcd               32016  0 
usbcore               149616  6 usblp,usb_storage,libusual,ehci_hcd,ohci_hcd
thermal                23708  0 
processor              42156  1 thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60956  3 
jim@jim-desktop:~$

---

### Post by Jim Lewis on 2010-02-02
Anybody?????

---

### Post by Jim Lewis on 2010-02-04
Come on.  I'm at a loss!

---

