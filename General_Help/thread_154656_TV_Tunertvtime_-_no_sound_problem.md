---
title: "TV Tuner/tvtime - no sound problem"
date: 2006-04-03
forum: General Help
---

### Post by TomPreuss on 2006-04-03
Hi all.

I've been working on getting my TV Tuner card completely working (model/product details forthcoming) and I managed to get the color working and the channels working correctly (by trial and error modprobe-ing various cx8800/cx88xx card/tuner parameters).  I've been using tvtime to test it (seems like a great program), as it seems to work better on my setup than xawtv.

I've been stumped for a while now with getting the sound to work.  Right now, I get no sound at all in Breezy.  The sound works fine from the TV card if I boot into Windows XP, which leads me to believe that it isn't a hardware connection issue.  I've checked all my input levels, and none are muted or turned down.

I've given my lsmod and lspci outputs below, because that seemed to be helpful in other threads of this nature I've seen.  The "Conexant Winfast TV2000 XP" is my TV card.  Oh, and I'm in the United States, so I use NTSC.    If I need to provide any additional info, please feel free to ask.

Any suggestions on what steps to take from here?

Thank you in advance.


lsmod```
Module                  Size  Used by
joydev                 10048  0
cx8800                 31692  0
v4l1_compat            14788  1 cx8800
v4l2_common             5824  1 cx8800
cx88xx                 54176  1 cx8800
i2c_algo_bit            9480  1 cx88xx
video_buf              21316  2 cx8800,cx88xx
ir_common               7620  1 cx88xx
btcx_risc               4936  2 cx8800,cx88xx
tveeprom               13208  1 cx88xx
videodev                9536  2 cx8800,cx88xx
tda9887                14104  0
nls_utf8                2112  1
ntfs                  109104  1
binfmt_misc            11592  1
rfcomm                 38748  0
l2cap                  25156  5 rfcomm
bluetooth              48580  4 rfcomm,l2cap
powernow_k8            12424  0
cpufreq_userspace       4380  1
cpufreq_stats           5316  0
freq_table              4484  2 powernow_k8,cpufreq_stats
cpufreq_powersave       1792  0
cpufreq_ondemand        6108  0
cpufreq_conservative     7012  0
nvidia               4089456  12
video                  15812  0
tc1100_wmi              6788  0
sony_acpi               5388  0
pcc_acpi               11200  0
hotkey                  9380  0
dev_acpi               11268  0
i2c_acpi_ec             5568  0
button                  6544  0
battery                 9412  0
container               4480  0
ac                      4804  0
ipv6                  252544  20
af_packet              22088  2
tsdev                   7872  0
floppy                 59412  0
pcspkr                  3460  0
rtc                    12408  0
usblp                  12736  0
tuner                  27176  0
shpchp                 97252  0
pci_hotplug            27636  1 shpchp
snd_intel8x0           33344  2
snd_ac97_codec         84028  1 snd_intel8x0
snd_pcm_oss            53152  0
snd_mixer_oss          19392  2 snd_pcm_oss
snd_pcm                89032  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              24260  1 snd_pcm
snd                    55172  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9696  2 snd
snd_page_alloc         10696  2 snd_intel8x0,snd_pcm
i2c_nforce2             6784  0
i2c_core               21328  7 cx88xx,i2c_algo_bit,tveeprom,tda9887,i2c_acpi_ec,tuner,i2c_nforce2
amd64_agp              12296  1
agpgart                34888  2 nvidia,amd64_agp
dm_mod                 58044  1
evdev                   9728  0
psmouse                30212  0
mousedev               11680  1
parport_pc             35460  1
lp                     12420  0
parport                36104  2 parport_pc,lp
md                     45648  0
ext3                  137352  1
jbd                    55128  1 ext3
mbcache                 9348  1 ext3
thermal                13064  0
processor              22908  2 powernow_k8,thermal
fan                     4548  0
usbhid                 35552  0
skge                   36880  0
ehci_hcd               34312  0
ohci_hcd               20740  0
usbcore               118396  5 usblp,usbhid,ehci_hcd,ohci_hcd
sd_mod                 19216  3
ide_cd                 41732  0
cdrom                  39904  1 ide_cd
ide_disk               18560  2
ide_generic             1472  0
sata_nv                 9412  4
libata                 54020  1 sata_nv
scsi_mod              135944  2 sd_mod,libata
amd74xx                14044  1
ide_core              139028  4 ide_cd,ide_disk,ide_generic,amd74xx
unix                   27248  947
vesafb                  8088  0
capability              4808  0
commoncap               6912  1 capability
vga16fb                12680  1
vgastate                9792  1 vga16fb
softcursor              2496  2 vesafb,vga16fb
cfbimgblt               3008  2 vesafb,vga16fb
cfbfillrect             3968  2 vesafb,vga16fb
cfbcopyarea             4672  2 vesafb,vga16fb
fbcon                  39104  72
tileblit                2432  1 fbcon
font                    8320  1 fbcon
bitblit                 5696  1 fbcon
```
lspci -vvv```
0000:00:00.0 Host bridge: nVidia Corporation: Unknown device 00e1 (rev a1)
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Region 0: Memory at e0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <available only to root>

0000:00:01.0 ISA bridge: nVidia Corporation: Unknown device 00e0 (rev a2)
        Subsystem: Giga-byte Technology: Unknown device 0c11
        Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0

0000:00:01.1 SMBus: nVidia Corporation: Unknown device 00e4 (rev a1)
        Subsystem: Giga-byte Technology: Unknown device 0c11
        Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin A routed to IRQ 11
        Region 0: I/O ports at e400 [size=32]
        Region 4: I/O ports at 1c00 [size=64]
        Region 5: I/O ports at 2000 [size=64]
        Capabilities: <available only to root>

0000:00:02.0 USB Controller: nVidia Corporation: Unknown device 00e7 (rev a1) (prog-if 10 [OHCI])
        Subsystem: Giga-byte Technology: Unknown device 5004
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (750ns min, 250ns max)
        Interrupt: pin A routed to IRQ 21
        Region 0: Memory at f7003000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:02.1 USB Controller: nVidia Corporation: Unknown device 00e7 (rev a1) (prog-if 10 [OHCI])
        Subsystem: Giga-byte Technology: Unknown device 5004
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (750ns min, 250ns max)
        Interrupt: pin B routed to IRQ 20
        Region 0: Memory at f7004000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:02.2 USB Controller: nVidia Corporation: Unknown device 00e8 (rev a2) (prog-if 20 [EHCI])
        Subsystem: Giga-byte Technology: Unknown device 5004
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (750ns min, 250ns max)
        Interrupt: pin C routed to IRQ 22
        Region 0: Memory at f7005000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:00:06.0 Multimedia audio controller: nVidia Corporation: Unknown device 00ea (rev a1)
        Subsystem: Giga-byte Technology: Unknown device a002
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (500ns min, 1250ns max)
        Interrupt: pin A routed to IRQ 21
        Region 0: I/O ports at bc00 [size=256]
        Region 1: I/O ports at c000 [size=128]
        Region 2: Memory at f7001000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:08.0 IDE interface: nVidia Corporation: Unknown device 00e5 (rev a2) (prog-if 8a [Master SecP PriP])
        Subsystem: Giga-byte Technology: Unknown device 5002
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (750ns min, 250ns max)
        Region 4: I/O ports at f000 [size=16]
        Capabilities: <available only to root>

0000:00:0a.0 IDE interface: nVidia Corporation: Unknown device 00e3 (rev a2) (prog-if 85 [Master SecO PriO])
        Subsystem: Giga-byte Technology: Unknown device b002
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (750ns min, 250ns max)
        Interrupt: pin A routed to IRQ 22
        Region 0: I/O ports at 09f0 [size=8]
        Region 1: I/O ports at 0bf0 [size=4]
        Region 2: I/O ports at 0970 [size=8]
        Region 3: I/O ports at 0b70 [size=4]
        Region 4: I/O ports at dc00 [size=16]
        Region 5: I/O ports at e000 [size=128]
        Capabilities: <available only to root>

0000:00:0b.0 PCI bridge: nVidia Corporation: Unknown device 00e2 (rev a2) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 16
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=10
        I/O behind bridge: 0000f000-00000fff
        Memory behind bridge: f0000000-f1ffffff
        Prefetchable memory behind bridge: e8000000-efffffff
        BridgeCtl: Parity- SERR+ NoISA+ VGA+ MAbort- >Reset- FastB2B-

0000:00:0e.0 PCI bridge: nVidia Corporation: Unknown device 00ed (rev a2) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=128
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: f2000000-f6ffffff
        Prefetchable memory behind bridge: fff00000-000fffff
        BridgeCtl: Parity- SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-

0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Capabilities: <available only to root>

0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0326 (rev a1) (prog-if 00 [VGA])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 248 (1250ns min, 250ns max)
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at f0000000 (32-bit, non-prefetchable) [size=16M]
        Region 1: Memory at e8000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <available only to root>

0000:02:07.0 Multimedia video controller: Conexant Winfast TV2000 XP (rev 05)
        Subsystem: Avermedia Technologies Inc: Unknown device c111
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (5000ns min, 13750ns max), Cache Line Size: 0x08 (32 bytes)
        Interrupt: pin A routed to IRQ 19
        Region 0: Memory at f2000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: <available only to root>

0000:02:07.1 Multimedia controller: Conexant: Unknown device 8801 (rev 05)
        Subsystem: Avermedia Technologies Inc: Unknown device c111
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (1000ns min, 63750ns max), Cache Line Size: 0x08 (32 bytes)
        Interrupt: pin A routed to IRQ 10
        Region 0: Memory at f3000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: <available only to root>

0000:02:07.2 Multimedia controller: Conexant: Unknown device 8802 (rev 05)
        Subsystem: Avermedia Technologies Inc: Unknown device c111
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (1500ns min, 22000ns max), Cache Line Size: 0x08 (32 bytes)
        Interrupt: pin A routed to IRQ 10
        Region 0: Memory at f4000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: <available only to root>

0000:02:0b.0 Ethernet controller: Marvell Technology Group Ltd. Yukon Gigabit Ethernet 10/100/1000Base-T Adapter (rev 13)
        Subsystem: Giga-byte Technology: Unknown device e000
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (5750ns min, 7750ns max), Cache Line Size: 0x08 (32 bytes)
        Interrupt: pin A routed to IRQ 19
        Region 0: Memory at f6000000 (32-bit, non-prefetchable) [size=16K]
        Region 1: I/O ports at a000 [size=256]
        Capabilities: <available only to root>
```

---

### Post by Christmas on 2006-04-03
I have the same tv-tunner card and i had no problems with the sound. Try playing with Input configuration options then "Change default audio standard", try with every one of the three options. Also make sure at the "Audio Boost" option the sound is set to Full or Medium and at "Preferred audio mode" I use Stereo. And I think from Applications -> Sound and Video -> Volume control you should have activated from the Capture tab the Line-in option. Not sure about that but I think it should be from there somewhere, probably is muted.

---

### Post by TomPreuss on 2006-04-03
Thank you for your reply Christmas.
[QUOTE=Christmas]I have the same tv-tunner card and i had no problems with the sound. Try playing with Input configuration options then "Change default audio standard", try with every one of the three options.[/quote]
I don't see this option.  The "Input configuration" menu presents me with the following options:
```
Change video source: Television
Preferred audio mode
Audio volume boost
Television standard
Horizontal resolution
Toggle closed captions
Toggle XDS decoding
<-- Back
```
I'm on NTSC, could that be a PAL-only option your thinking of?

[QUOTE=Christmas]Also make sure at the "Audio Boost" option the sound is set to Full or Medium[/quote]
I changed the setting to "Full", still no sound.

[QUOTE=Christmas]and at "Preferred audio mode" I use Stereo.[/quote]
I tried all three, Mono, Stereo, and SAP, no luck.

[QUOTE=Christmas]And I think from Applications -> Sound and Video -> Volume control you should have activated from the Capture tab the Line-in option. Not sure about that but I think it should be from there somewhere, probably is muted.[/QUOTE]
I've just triple-checked all my input levels, and none are muted or turned down.

Still no sound.  Any other ideas?

---

### Post by TomPreuss on 2006-04-04
A quick update:

Still no sound, but I did try something else that might spark some ideas.  I plugged my speakers directly into the Tuner Card (instead of into my motherboard's audio out like usual) and that didn't produce any sound either.

Any suggestions will be welcome.

---

### Post by Michael Matthews on 2006-04-04
There used to be v4lctl command as part of v4l util package. see bytesex.org

v4lctl volume 65535
v4lctl volume mute off

Have you tried tvtime volume boost control?

---

### Post by TomPreuss on 2006-04-04
Thank you for your reply Michael.

[QUOTE=Michael Matthews]There used to be v4lctl command as part of v4l util package. see bytesex.org

v4lctl volume 65535
v4lctl volume mute off[/QUOTE]
Nope, no luck here.  I got "no handler for 65535" and "no handler for mute" when I tried these.

[QUOTE=Michael Matthews]Have you tried tvtime volume boost control?[/QUOTE]
Yes, I changed the setting to "Full" after Christmas suggested it above, still no sound.

Keep the suggestions coming, I'll try anything.

---

### Post by Christmas on 2006-04-05
[QUOTE=TomPreuss]
I'm on NTSC, could that be a PAL-only option your thinking of?[/QUOTE]

Yes here in Romania looks like PAL is the TV-Standard. Anyway, I changed from PAL to NTSC and "Restart with new settings". That "Change Default Audio Standard" option is still present under the Input Configuration menu. I really don't know how can I help... maybe you have another TVTime version? I think that this audio option should be there somewhere. In Synaptic it shows me I have installed package tvtime, version 1.0.1-2ubuntu1.

---

### Post by TomPreuss on 2006-04-05
[QUOTE=Christmas]Yes here in Romania looks like PAL is the TV-Standard. Anyway, I changed from PAL to NTSC and "Restart with new settings". That "Change Default Audio Standard" option is still present under the Input Configuration menu. I really don't know how can I help... maybe you have another TVTime version? I think that this audio option should be there somewhere. In Synaptic it shows me I have installed package tvtime, version 1.0.1-2ubuntu1.[/QUOTE]
I am only presented with the "Restart with new settings" after I change to PAL and restart tvtime.  Then the option appears and I can choose from PAL-I, PAL-BG, and PAL-DK.  Of course, once I switch to PAL, nothing works.  Thank you for the suggestion though.

I also am running tvtime version 1.0.1-2ubuntu1.

Keep those suggestions coming.

---

### Post by Donshyoku on 2006-04-07
I am in Dapper and I have the same tuner and same audio problem.  All of what has been mentioned here so far has not worked for me either. 

BTW, what sound chip are you running when you have this problem?  I have the C-Media CMI9880 which is supported with ALSA 1.0.9 and I am on 1.0.10.  My line in and CD are enabled, the volume is up (not muted), and I have this problem.

So please, keep the suggestions coming!:)

---

### Post by Michael Matthews on 2006-04-07
Post

v4lctl list
v4lctl show volume

---

### Post by Donshyoku on 2006-04-07
[QUOTE=Michael Matthews]Post

v4lctl list
v4lctl show volume[/QUOTE]


In terminal?

I am getting that "v4lctl" is not a recognized command...

---

### Post by TomPreuss on 2006-04-08
[QUOTE=Michael Matthews]Post

v4lctl list
v4lctl show volume[/QUOTE]
v4lctl list```
attribute  | type   | current | default | comment
-----------+--------+---------+---------+-------------------------------------
norm       | choice | NTSC-M  | NTSC-M  | NTSC-M NTSC-JP PAL-BG PAL-DK PAL-I PAL-M PAL-N PAL-Nc PAL-60 SECAM-L SECAM-DK
input      | choice | Televis | Televis | Television Composite1 S-Video
audio mode | choice | mono    | mono    | mono stereo lang1 lang2
bright     | int    |     128 |       0 | range is 0 => 255
contrast   | int    |     128 |       0 | range is 0 => 255
color      | int    |     128 |       0 | range is 0 => 255
hue        | int    |     128 |       0 | range is 0 => 255
volume     | int    |      63 |       0 | range is 0 => 63
Balance    | int    |      64 |      64 | range is 0 => 127
mute       | bool   | on      | off     |
```
v4lctl show volume```
volume: 63
```
What's this mean?

**Edit:**
Okay, so I played around a little with this:
```
$ v4lctl show mute
mute: on
$ v4lctl volume mute off
$ v4lctl show mute
mute: off
$ tvtime
Running tvtime 1.0.1.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/tom/.tvtime/tvtime.xml
```
tvtime opens with no sound.  I then quit tvtime and am brought back to the terminal:
```
Thank you for using tvtime.
$ v4lctl show mute
mute: on
```
Does this mean that something to do with tvtime is setting the mute to on?

---

### Post by TomPreuss on 2006-04-22
[QUOTE=TomPreuss]```
$ v4lctl show mute
mute: on
$ v4lctl volume mute off
$ v4lctl show mute
mute: off
$ tvtime
Running tvtime 1.0.1.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/tom/.tvtime/tvtime.xml
```
tvtime opens with no sound.  I then quit tvtime and am brought back to the terminal:
```
Thank you for using tvtime.
$ v4lctl show mute
mute: on
```
Does this mean that something to do with tvtime is setting the mute to on?[/QUOTE]
I'm still getting this same behavior.  Any ideas?

---

### Post by etitor on 2007-10-07
> **TomPreuss said:**
> I'm still getting this same behavior.  Any ideas?

Your post is old now, but I'm facing the same problems.

Try to disable automute. In my case that didn't help either, but who knows.

```
v4lctl setattr automute off
```

---

