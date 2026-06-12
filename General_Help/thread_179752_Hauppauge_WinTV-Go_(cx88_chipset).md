---
title: "Hauppauge WinTV-Go (cx88 chipset)"
date: 2006-05-20
forum: General Help
---

### Post by DoddyUK on 2006-05-20
Hi. I bought the Hauppauge WinTV-Go TV tuner card a few days ago. I installed it under Windows and it worked perfectly. I also heard that this card worked perfectly under Ubuntu, though that has yet to be the case so far. I can only watch the last channel I tuned into under Windows.

I've searched these forums and Google, and have yet to find answer to get this working. Here's the output from my dmesg:

```
[4294700.871000] Linux video capture interface: v1.00
[4294700.967000] cx2388x v4l2 driver version 0.0.4 loaded
[4294700.973000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 18 (level, low) -> I
RQ 18
[4294700.973000] cx88[0]: subsystem: 0070:3401, board: Hauppauge WinTV 34xxx mod
els [card=1,autodetected]
[4294701.135000] tveeprom: Hauppauge: model = 34705, rev = J198, serial# = 85073
73
[4294701.135000] tveeprom: tuner = <unknown> (idx = 98, type = -827701632)
[4294701.135000] tveeprom: tuner fmt = PAL(D/K) (eeprom = 0x50, v4l2 = 0x00000e1
0)
[4294701.135000] tveeprom: audio_processor = MSP3425 (type = 15)
[4294701.187000] cx88[0]: registered IR remote control
[4294701.187000] cx88[0]/0: found at 0000:00:0b.0, rev: 5, irq: 18, latency: 32,
 mmio: 0xde000000
[4294701.207000] tuner 0-0061: chip found @ 0xc2 (cx88[0])
[4294701.314000] cx88[0]/0: registered device video0 [v4l2]
[4294701.316000] cx88[0]/0: registered device vbi0
[4294701.317000] cx88[0]/0: registered device radio0

```

I've tried adding the following modules to /etc/modules, but with no success:

```

cx88xx card=1 tuner=43
cx8800

```

As some additional information, here's the results of my LSPCI and LSMOD:

```
michael@rei:~$ lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400] Chipset Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
0000:00:0a.0 Network controller: RaLink Ralink RT2500 802.11 Cardbus Reference Card (rev 01)
0000:00:0b.0 Multimedia video controller: Conexant Winfast TV2000 XP (rev 05)
0000:00:0b.1 Multimedia controller: Conexant: Unknown device 8811 (rev 05)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
0000:01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)
```

```
michael@rei:~$ lsmod
Module                  Size  Used by
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
cpufreq_userspace       4444  0
cpufreq_stats           5124  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
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
ipv6                  217408  6
smbfs                  57208  2
af_packet              20232  4
floppy                 52692  0
pcspkr                  3652  0
rtc                    11832  0
snd_via82xx            25792  2
gameport               14472  1 snd_via82xx
snd_ac97_codec         72188  1 snd_via82xx
snd_pcm_oss            46368  0
snd_mixer_oss          16128  2 snd_pcm_oss
snd_pcm                78344  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10120  2 snd_via82xx,snd_pcm
snd_mpu401_uart         6784  1 snd_via82xx
i2c_viapro              7696  0
via_ircc               23700  0
irda                  159804  1 via_ircc
crc_ccitt               2176  1 irda
tda9887                13208  0
tuner                  24488  0
cx8800                 28812  1
cx88xx                 50976  1 cx8800
i2c_algo_bit            8584  1 cx88xx
video_buf              19844  2 cx8800,cx88xx
ir_common               7428  1 cx88xx
tveeprom               12568  1 cx88xx
i2c_core               19728  7 i2c_acpi_ec,i2c_viapro,tda9887,tuner,cx88xx,i2c_algo_bit,tveeprom
v4l1_compat            12420  1 cx8800
v4l2_common             5888  1 cx8800
btcx_risc               4872  2 cx8800,cx88xx
videodev                9344  3 cx8800,cx88xx
rt2500                150372  1
pci_hotplug            24628  0
via_agp                 9472  1
agpgart                32328  1 via_agp
nls_utf8                2176  1
nls_cp437               5888  1
vfat                   12288  1
fat                    46492  1 vfat
dm_mod                 50364  1
tsdev                   7616  0
evdev                   9088  0
snd_seq_dummy           3844  0
snd_seq_oss            29440  0
snd_seq_midi            8608  0
snd_rawmidi            22816  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      6656  2 snd_seq_oss,snd_seq_midi
snd_seq                44688  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              21764  2 snd_pcm,snd_seq
snd_seq_device          8204  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    48644  14 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9184  2 snd
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  1
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  3
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
via_rhine              20356  0
mii                     5248  1 via_rhine
ehci_hcd               29448  0
uhci_hcd               28048  0
usbcore               104316  3 ehci_hcd,uhci_hcd
ide_cd                 36996  0
cdrom                  33952  1 ide_cd
ide_disk               16128  7
ide_generic             1664  0
via82cxxx              12188  1
ide_core              125268  4 ide_cd,ide_disk,ide_generic,via82cxxx
unix                   24624  459
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

```

Any help would be greatly appreciated. Cheers.

**EDIT** - Just to add to that, I've tried compiling the cx88 kernel modules from [http://linux.bytesex.org/v4l2/cx88.html](http://linux.bytesex.org/v4l2/cx88.html), but with no success. Here's the output:

```
michael@rei:~/install/cx88-0.0.4$ make
make -C /lib/modules/2.6.12-10-386/build SUBDIRS=/home/michael/install/cx88-0.0.4 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
  CC [M]  /home/michael/install/cx88-0.0.4/video-buf.o
  CC [M]  /home/michael/install/cx88-0.0.4/v4l1-compat.o
  CC [M]  /home/michael/install/cx88-0.0.4/v4l2-common.o
  CC [M]  /home/michael/install/cx88-0.0.4/btcx-risc.o
  CC [M]  /home/michael/install/cx88-0.0.4/cx88-video.o
/home/michael/install/cx88-0.0.4/cx88-video.c: In function `cx8800_suspend':
/home/michael/install/cx88-0.0.4/cx88-video.c:2552: error: too many arguments to function `pci_save_state'
/home/michael/install/cx88-0.0.4/cx88-video.c: In function `cx8800_resume':
/home/michael/install/cx88-0.0.4/cx88-video.c:2571: error: too many arguments to function `pci_restore_state'
make[2]: *** [/home/michael/install/cx88-0.0.4/cx88-video.o] Error 1
make[1]: *** [_module_/home/michael/install/cx88-0.0.4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
make: *** [default] Error 2
```

---

