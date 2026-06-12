---
title: "Audio in only one app at a time?"
date: 2009-07-05
forum: General Help
---

### Post by derekeverett on 2009-07-05
I have tried to find a possibly existing thread on this but I'm not real sure how such a thread would be titled. So if one exists accept my apologies in advance...

This is my problem.

I can't seem to run 2 apps at the same time and get audio in both. For example, if I am playing an album in Rhythmbox, and pause it for a moment to watch a youtube video that a friend has sent me, I get no audio in youtube. If I actually shut Rhythmbox down then I get my youtube audio but I usually have to re-start firefox.

It's really starting to frustrate me. Sometimes I actually have to kill processes in order to get audio from another app. Any ideas?

---

### Post by Johnny B on 2009-07-05
what audio driver are you using?
did you try installing alsa, oss.. ?
can you post output from lsmod and lspci please?

edit:
 find your sound card in here:
[http://www.alsa-project.org/main/index.php/Matrix:Main]("http://www.alsa-project.org/main/index.php/Matrix:Main")

---

### Post by derekeverett on 2009-07-05
gnome-device-manager says it's HDA ATI SB sound card Model #SBx00

lsmod:
Module                  Size  Used by
sha1_generic            4352  0 
ppp_mppe                9608  0 
ppp_async              14592  0 
crc_ccitt               3584  1 ppp_async
ppp_generic            33568  2 ppp_mppe,ppp_async
slhc                    8192  1 ppp_generic
ipv6                  311848  18 
af_packet              27272  2 
rfcomm                 47392  2 
l2cap                  28800  13 rfcomm
bluetooth              67620  4 rfcomm,l2cap
vboxdrv              1649152  0 
ppdev                  11400  0 
powernow_k8            16608  1 
cpufreq_userspace       6180  0 
cpufreq_conservative    10632  0 
cpufreq_ondemand       11152  1 
cpufreq_stats           8416  0 
cpufreq_powersave       3200  0 
freq_table              6464  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
dock                   12960  0 
container               6656  0 
video                  23444  0 
output                  5632  1 video
sbs                    17808  0 
sbshc                   8960  1 sbs
battery                16776  0 
iptable_filter          4608  0 
ip_tables              24104  1 iptable_filter
x_tables               23560  1 ip_tables
ac                      8328  0 
sbp2                   27272  0 
parport_pc             41128  0 
lp                     14916  0 
parport                44300  3 ppdev,parport_pc,lp
arc4                    3456  2 
ecb                     5248  2 
blkcipher               9476  1 ecb
rt73usb                28928  0 
rt2x00usb              14720  1 rt73usb
rt2x00lib              25344  2 rt73usb,rt2x00usb
rfkill                 10144  1 rt2x00lib
input_polldev           6928  1 rt2x00lib
crc_itu_t               3584  1 rt2x00lib
snd_hda_intel         442200  3 
mac80211              192532  2 rt2x00usb,rt2x00lib
snd_pcm_oss            47648  0 
snd_mixer_oss          20224  1 snd_pcm_oss
usbhid                 35680  0 
hid                    44992  1 usbhid
usb_storage            82624  1 
snd_pcm                92168  2 snd_hda_intel,snd_pcm_oss
cfg80211               17680  1 mac80211
snd_page_alloc         13200  2 snd_hda_intel,snd_pcm
snd_hwdep              12552  1 snd_hda_intel
libusual               23648  1 usb_storage
evdev                  14976  4 
fglrx                1804800  24 
snd_seq_dummy           5764  0 
psmouse                46236  0 
snd_seq_oss            38912  0 
snd_seq_midi           10688  0 
serio_raw               9092  0 
snd_rawmidi            29856  1 snd_seq_midi
snd_seq_midi_event     10112  2 snd_seq_oss,snd_seq_midi
snd_seq                63232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27912  2 snd_pcm,snd_seq
snd_seq_device         10644  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    70856  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
k8temp                  7680  0 
pcspkr                  4992  0 
button                 10912  0 
soundcore              10400  1 snd
shpchp                 38172  0 
pci_hotplug            34608  1 shpchp
i2c_piix4              11148  0 
i2c_core               28544  1 i2c_piix4
ext3                  149264  2 
jbd                    57000  1 ext3
mbcache                11392  1 ext3
pata_atiixp            10496  0 
ata_generic             9988  0 
sg                     41880  0 
sr_mod                 20132  0 
cdrom                  41512  1 sr_mod
sd_mod                 33280  5 
pata_acpi               9856  0 
ohci_hcd               28956  0 
ahci                   33284  2 
ehci_hcd               41996  0 
atiixp                  6672  0 [permanent]
ide_core              136600  1 atiixp
r8169                  38532  0 
libata                176560  4 pata_atiixp,ata_generic,pata_acpi,ahci
ohci1394               36532  0 
usbcore               170288  8 rt73usb,rt2x00usb,usbhid,usb_storage,libusual,ohci_hcd,ehci_hcd
scsi_mod              178488  6 sbp2,usb_storage,sg,sr_mod,sd_mod,libata
ieee1394              106968  2 sbp2,ohci1394
thermal                19744  0 
processor              40424  2 powernow_k8,thermal
fan                     6792  0 
fbcon                  46336  0 
tileblit                4096  1 fbcon
font                   10112  1 fbcon
bitblit                 7424  1 fbcon
softcursor              3712  1 bitblit
fuse                   56112  3 

lspci:
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Hewlett-Packard Company Unknown device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:11.0 RAID bus controller: ATI Technologies Inc SB700/SB800 SATA Controller [Non-RAID5 mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics
02:00.0 FireWire (IEEE 1394): JMicron Technologies, Inc. Unknown device 2380
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

---

### Post by Jesus_Valdez on 2009-07-05
What I did to changes that was really easy, just go to System- Preferences-Sound and set evertyhing to Pulse Audio server et voila!, sound on everything.

I guess a read about it at ubuntugeek.com but I'm not sure.

---

### Post by derekeverett on 2009-07-05
I just gave that a shot. No dice.

I had everything on auto-detect before.

Thanks Tho!

---

### Post by Johnny B on 2009-07-05
[http://ubuntuforums.org/showthread.php?t=600308]("http://ubuntuforums.org/showthread.php?t=600308")

---

### Post by derekeverett on 2009-07-06
Thanks for the thread, I read it over but I'm not real sure what your trying to tell me here.

I do have sound. In fact i've been working with a lot of converting both audio and video lately and I'm not having problems. Even with restricted stuff. I just can't get audio out of 2 apps at the same time. Even if one is paused. 

Totally possible I missed your point here, if I did I apologize but could you please clarify?

---

### Post by Agent ME on 2009-07-06
What version of Ubuntu are you running?

---

### Post by derekeverett on 2009-07-06
8.04 64 bit.

---

### Post by jocko on 2009-07-06
The cause of your problem is that your applications are trying to use alsa directly instead of going through a software mixer. Only one application at the time can have direct access to alsa (unless you are one of the very lucky few to have a sound card with good enough alsa drivers to be able to use a hardware mixer).
Set **all** your applications to use pulseaudio (not just system-->settings-->sound).
Check in:
```
gnome-sound properties
``````
gstreamer-properties
```And all your applications' individual settings (for all apps like mplayer, vlc, audacious, xmms, bmp etc. that don't use gstreamer).
As long as **all** sound streams go to pulseaudio, and pulseaudio is the **only** program that have direct access to alsa, you will get sound from several sources at the time.

---

### Post by derekeverett on 2009-07-06
Thanks, This sounds like it's on the right track.

How do I check/change the settings for individual apps? I can't seem to find anything under preferences for any of the apps.

Everything else is set up like you said system->preferences->sound and under gstreamer-properties. It has been for weeks I'm sure.

---

### Post by jocko on 2009-07-06
> **derekeverett said:**
> How do I check/change the settings for individual apps? I can't seem to find anything under preferences for any of the apps.
Well, it depends on which apps you use. Gstreamer-properties takes care of many (totem, rhythmbox, ...).
Only apps that don't use gstreamer have their own settings (usually found in a "preferences" menu option). If you can't find it, you'll have to ask about that specific app, as each app is different.

---

### Post by derekeverett on 2009-07-06
well that's not good news for me because Totem and Rhythmbox are the two apps I'm using to test...

gstreamer-properties are all set proper like I said.

Still can't get audio out of both. I have to shut one down :(

---

