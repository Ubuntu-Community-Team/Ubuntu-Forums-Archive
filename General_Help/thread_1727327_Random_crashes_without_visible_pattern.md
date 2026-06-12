---
title: "Random crashes without visible pattern"
date: 2011-04-12
forum: General Help
---

### Post by Alp82 on 2011-04-12
I have no clue when it started. Since 10 days or so my computer crashes randomly when working in Ubuntu. Here are some facts:

[LIST]
[*]It can happen after one minute or several hours
[*]Every time, music is playing (MPD / PulseAudio), but my player runs mostly the whole time, so i am not sure if that's helping
[*]No specific action triggers the freeze, but i think a simple click is mostly involved
[*]When freezing the audio buffer is repeated every second or so
[*]The reset button does not work! I have to press the power button for 5 seconds to shut down the computer
[*]In Windows i did not experience any freezes, while i am doing hardware intensive stuff like gaming or audio processing
[/LIST]

My Hardware:

CPU: Intel Core i5-2500K
MB: Gigabyte GA-P67A-UD3P 
GFX: Gigabyte GeForce GTX 560 Ti Overclock
RAM: G.Skill RipJaws DIMM Kit 8GB PC3-10667U
SSD: Crucial RealSSD C300 128GB

---

### Post by sanguinoso on 2011-04-12
Next time it happens run this command when you boot up again and post the results here. ```
tail -n 50 /var/log/messages
```

---

### Post by bluepicaso on 2011-04-12
i have a similar problem. 
System crashed randomly without warning. everything works file and suddenly its all goes.
happening from last 20-30 days. all startup programs are jumbled up. some do start some don't.
earlier i thought it was firefox but now seems banshee,

CAn you tell me what to do?
I'm new to ubuntu. not expert user though.
Please let me know what should i do. what commands output do you need ?

Just please i beg you.
Its really kinda time killing.

cpu: intel core 2duo
Make: DELL inspiron 1525
memory: 2gb

---

### Post by sanguinoso on 2011-04-12
Post output of the command above. It just outputs the last 50 lines of the system log so we can get a better idea of what's happening.

---

### Post by bluepicaso on 2011-04-12
OK so it crashed again.
I'm sure it has something to do with audio or video.
This time i was on you tube watching a video.
I'm not sure for the reason but its due to either audio(banshee) or video on any browser.
Find the out put below:-
> 
Apr 12 23:57:11 TheCodingBox kernel: [   20.069540] Console: switching to colour frame buffer device 160x50
Apr 12 23:57:11 TheCodingBox kernel: [   20.069549] fb0: inteldrmfb frame buffer device
Apr 12 23:57:11 TheCodingBox kernel: [   20.069551] drm: registered panic notifier
Apr 12 23:57:11 TheCodingBox kernel: [   20.069555] Slow work thread pool: Starting up
Apr 12 23:57:11 TheCodingBox kernel: [   20.069614] Slow work thread pool: Ready
Apr 12 23:57:11 TheCodingBox kernel: [   20.086760] acpi device:2f: registered as cooling_device2
Apr 12 23:57:11 TheCodingBox kernel: [   20.087636] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:00/input/input10
Apr 12 23:57:11 TheCodingBox kernel: [   20.087785] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Apr 12 23:57:11 TheCodingBox kernel: [   20.087823] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
Apr 12 23:57:11 TheCodingBox kernel: [   20.088506] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Apr 12 23:57:11 TheCodingBox kernel: [   20.088576] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Apr 12 23:57:11 TheCodingBox kernel: [   20.180568] vboxdrv: fAsync=0 offMin=0x2f8 offMax=0x1766
Apr 12 23:57:11 TheCodingBox kernel: [   20.181368] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Apr 12 23:57:11 TheCodingBox kernel: [   20.452304] Skipping EDID probe due to cached edid
Apr 12 23:57:12 TheCodingBox kernel: [   20.465159] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
Apr 12 23:57:12 TheCodingBox kernel: [   20.465255] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
Apr 12 23:57:12 TheCodingBox kernel: [   20.465326] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
Apr 12 23:57:12 TheCodingBox kernel: [   20.622851] ppdev: user-space parallel port driver
Apr 12 23:57:12 TheCodingBox kernel: [   20.849284] Skipping EDID probe due to cached edid
Apr 12 23:57:13 TheCodingBox kernel: [   22.153060] Skipping EDID probe due to cached edid
Apr 12 23:57:14 TheCodingBox kernel: [   22.540254] Skipping EDID probe due to cached edid
Apr 12 23:57:14 TheCodingBox kernel: [   22.937058] Skipping EDID probe due to cached edid
Apr 12 23:57:14 TheCodingBox kernel: [   23.325065] Skipping EDID probe due to cached edid
Apr 12 23:57:16 TheCodingBox kernel: [   25.300852] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr 12 23:57:17 TheCodingBox kernel: [   25.511304] Bluetooth: L2CAP ver 2.14
Apr 12 23:57:17 TheCodingBox kernel: [   25.511309] Bluetooth: L2CAP socket layer initialized
Apr 12 23:57:17 TheCodingBox kernel: [   25.566425] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Apr 12 23:57:17 TheCodingBox kernel: [   25.566429] Bluetooth: BNEP filters: protocol multicast
Apr 12 23:57:17 TheCodingBox kernel: [   25.588527] Bluetooth: SCO (Voice Link) ver 0.6
Apr 12 23:57:17 TheCodingBox kernel: [   25.588533] Bluetooth: SCO socket layer initialized
Apr 12 23:57:17 TheCodingBox kernel: [   25.742813] Bluetooth: RFCOMM TTY layer initialized
Apr 12 23:57:17 TheCodingBox kernel: [   25.742823] Bluetooth: RFCOMM socket layer initialized
Apr 12 23:57:17 TheCodingBox kernel: [   25.742828] Bluetooth: RFCOMM ver 1.11
Apr 12 23:57:17 TheCodingBox kernel: [   26.193098] usb 7-2: USB disconnect, address 2
Apr 12 23:57:17 TheCodingBox kernel: [   26.193105] usb 7-2.1: USB disconnect, address 3
Apr 12 23:57:17 TheCodingBox kernel: [   26.198850] usb 7-2.2: USB disconnect, address 4
Apr 12 23:57:17 TheCodingBox pulseaudio[1809]: lock-autospawn.c: Cannot access autospawn lock.
Apr 12 23:57:17 TheCodingBox kernel: [   26.248299] usb 7-2.3: USB disconnect, address 5
Apr 12 23:57:18 TheCodingBox kernel: [   27.435070] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Apr 12 23:57:18 TheCodingBox kernel: [   27.439561] EXT4-fs (sda5): re-mounted. Opts: commit=0
Apr 12 23:57:19 TheCodingBox kernel: [   27.975844] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Apr 12 23:57:26 TheCodingBox kernel: [   34.893054] Skipping EDID probe due to cached edid
Apr 12 23:57:26 TheCodingBox kernel: [   35.280259] Skipping EDID probe due to cached edid
Apr 12 23:57:27 TheCodingBox kernel: [   35.664225] Skipping EDID probe due to cached edid
Apr 12 23:57:29 TheCodingBox kernel: [   38.004245] Skipping EDID probe due to cached edid
Apr 12 23:57:55 TheCodingBox kernel: [   63.844066] Skipping EDID probe due to cached edid
Apr 12 23:57:58 TheCodingBox kernel: [   67.404569] show_signal_msg: 33 callbacks suppressed
Apr 12 23:57:58 TheCodingBox kernel: [   67.404574] synapse[2055]: segfault at 207ac381 ip 006e22c6 sp bfb47740 error 4 in libzeitgeist-1.0.so.0.0.0[6da000+27000]
Apr 12 23:58:51 TheCodingBox kernel: [  119.801341] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
Apr 12 23:59:07 TheCodingBox pulseaudio[2018]: ratelimit.c: 4058 events suppressed


---

### Post by sanguinoso on 2011-04-12
I'm inclined to agree, do you have multiple video cards? The relevant line seems to be ```
[Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controlle
```

---

### Post by sanguinoso on 2011-04-12
Oh and if so what types are they?

---

### Post by bluepicaso on 2011-04-12
> **sanguinoso said:**
> Oh and if so what types are they?

HOw do i get to know that?
Sorry. dont know much commands..

---

### Post by bluepicaso on 2011-04-12
got the command
lspci | grep 'VGA'

and got output
> 
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)



also found this bug
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/722377](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/722377)

---

### Post by Alp82 on 2011-04-12
> **sanguinoso said:**
> Next time it happens run this command when you boot up again and post the results here. ```
tail -n 50 /var/log/messages
```

Thanks for your response. Didn't have a crash since my post, but i will post the output when it happens again.

---

### Post by sanguinoso on 2011-04-12
To determine graphics cards installed in your system type: ```
sudo lshw -C display
```
And paste the results.

---

### Post by bluepicaso on 2011-04-12
another output is this
from "sudo lshw -C video" command
> 
*-display:0             
       description: VGA compatible controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:44 memory:fea00000-feafffff memory:e0000000-efffffff ioport:efe8(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:feb00000-febfffff



---

### Post by sanguinoso on 2011-04-12
I saw that you're using skype, is skype active when there is a crash? I found this thread on the skype forums [http://forum.skype.com/index.php?showtopic=276161](http://forum.skype.com/index.php?showtopic=276161). That seems be a similar problem if thats the case. Maybe try not running skype for a while to rule it out?

Also do you have xserver-xorg-video-intel installed?

---

### Post by bluepicaso on 2011-04-12
> **sanguinoso said:**
> 
Also do you have xserver-xorg-video-intel installed?
yeah seems to


[IMG]http://imm.io/media/4W/4WZW.png[/IMG]

---

### Post by sanguinoso on 2011-04-12
Ok what about skype?

---

### Post by bluepicaso on 2011-04-12
> **sanguinoso said:**
> Ok what about skype?
hmm ... well i have turned it off..
Yeah it may be skype. 
I'm not sure though. lets play some videos on youtube
MIght get the crash again

---

### Post by sanguinoso on 2011-04-12
Its a hard one to debug because you just have to change things one at a time and sit and wait for something to happen.

---

### Post by bluepicaso on 2011-04-12
yeah i know that.
But thank you for you time brother.
Please keep following.
You would save my life

god bless you mate

---

### Post by bluepicaso on 2011-04-13
> **sanguinoso said:**
> Its a hard one to debug because you just have to change things one at a time and sit and wait for something to happen.

ok so here you go. crash again when i was on you tube today.
Please help again.
> 
Apr 13 14:06:14 TheCodingBox kernel: [   17.247367] vboxdrv: fAsync=0 offMin=0x1cc offMax=0x690
Apr 13 14:06:14 TheCodingBox kernel: [   17.247918] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Apr 13 14:06:14 TheCodingBox kernel: [   17.262993] Console: switching to colour dummy device 80x25
Apr 13 14:06:14 TheCodingBox kernel: [   17.264267] Console: switching to colour frame buffer device 160x50
Apr 13 14:06:14 TheCodingBox kernel: [   17.264277] fb0: inteldrmfb frame buffer device
Apr 13 14:06:14 TheCodingBox kernel: [   17.264279] drm: registered panic notifier
Apr 13 14:06:14 TheCodingBox kernel: [   17.264283] Slow work thread pool: Starting up
Apr 13 14:06:14 TheCodingBox kernel: [   17.264339] Slow work thread pool: Ready
Apr 13 14:06:14 TheCodingBox kernel: [   17.279355] acpi device:2f: registered as cooling_device2
Apr 13 14:06:14 TheCodingBox kernel: [   17.280563] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:00/input/input9
Apr 13 14:06:14 TheCodingBox kernel: [   17.280716] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Apr 13 14:06:14 TheCodingBox kernel: [   17.280743] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
Apr 13 14:06:14 TheCodingBox kernel: [   17.281410] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Apr 13 14:06:14 TheCodingBox kernel: [   17.281465] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Apr 13 14:06:15 TheCodingBox kernel: [   17.605166] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
Apr 13 14:06:15 TheCodingBox kernel: [   17.605259] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
Apr 13 14:06:15 TheCodingBox kernel: [   17.605356] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
Apr 13 14:06:15 TheCodingBox kernel: [   17.697104] Skipping EDID probe due to cached edid
Apr 13 14:06:15 TheCodingBox kernel: [   17.751425] ppdev: user-space parallel port driver
Apr 13 14:06:15 TheCodingBox kernel: [   18.077119] Skipping EDID probe due to cached edid
Apr 13 14:06:17 TheCodingBox kernel: [   19.344094] Skipping EDID probe due to cached edid
Apr 13 14:06:17 TheCodingBox kernel: [   19.737398] Skipping EDID probe due to cached edid
Apr 13 14:06:17 TheCodingBox kernel: [   20.132076] Skipping EDID probe due to cached edid
Apr 13 14:06:18 TheCodingBox kernel: [   20.520247] Skipping EDID probe due to cached edid
Apr 13 14:06:19 TheCodingBox kernel: [   21.828175] Disabling lock debugging due to kernel taint
Apr 13 14:06:19 TheCodingBox kernel: [   21.828817] CPU1: Core temperature/speed normal
Apr 13 14:06:20 TheCodingBox kernel: [   22.461777] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr 13 14:06:20 TheCodingBox kernel: [   22.622618] Bluetooth: L2CAP ver 2.14
Apr 13 14:06:20 TheCodingBox kernel: [   22.622622] Bluetooth: L2CAP socket layer initialized
Apr 13 14:06:20 TheCodingBox kernel: [   22.629088] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Apr 13 14:06:20 TheCodingBox kernel: [   22.629092] Bluetooth: BNEP filters: protocol multicast
Apr 13 14:06:20 TheCodingBox kernel: [   22.635347] Bluetooth: SCO (Voice Link) ver 0.6
Apr 13 14:06:20 TheCodingBox kernel: [   22.635350] Bluetooth: SCO socket layer initialized
Apr 13 14:06:20 TheCodingBox kernel: [   22.793959] Bluetooth: RFCOMM TTY layer initialized
Apr 13 14:06:20 TheCodingBox kernel: [   22.793968] Bluetooth: RFCOMM socket layer initialized
Apr 13 14:06:20 TheCodingBox kernel: [   22.793971] Bluetooth: RFCOMM ver 1.11
Apr 13 14:06:20 TheCodingBox kernel: [   23.216091] usb 7-2: USB disconnect, address 2
Apr 13 14:06:20 TheCodingBox kernel: [   23.216097] usb 7-2.1: USB disconnect, address 3
Apr 13 14:06:20 TheCodingBox kernel: [   23.217439] usb 7-2.2: USB disconnect, address 4
Apr 13 14:06:20 TheCodingBox kernel: [   23.248622] usb 7-2.3: USB disconnect, address 5
Apr 13 14:06:21 TheCodingBox pulseaudio[1863]: lock-autospawn.c: Cannot access autospawn lock.
Apr 13 14:06:21 TheCodingBox kernel: [   24.079217] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Apr 13 14:06:21 TheCodingBox kernel: [   24.082555] EXT4-fs (sda5): re-mounted. Opts: commit=0
Apr 13 14:06:22 TheCodingBox kernel: [   25.117463] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Apr 13 14:10:57 TheCodingBox kernel: [  299.988232] Machine check events logged
Apr 13 14:16:58 TheCodingBox kernel: [  661.184065] Skipping EDID probe due to cached edid
Apr 13 14:16:59 TheCodingBox kernel: [  661.573215] Skipping EDID probe due to cached edid
Apr 13 14:16:59 TheCodingBox kernel: [  661.960263] Skipping EDID probe due to cached edid
Apr 13 14:17:02 TheCodingBox kernel: [  664.844076] Skipping EDID probe due to cached edid
Apr 13 14:17:23 TheCodingBox kernel: [  685.717079] Skipping EDID probe due to cached edid



---

### Post by bluepicaso on 2011-04-13
can this help
output id this lspci; lsusb; lsmod; dmesg | egrep -i "error|warn|webcam|video"
> 

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Module                  Size  Used by
rfcomm                 33811  0 
binfmt_misc             6599  1 
sco                     7998  0 
bnep                    9542  0 
l2cap                  37008  4 rfcomm,bnep
parport_pc             26058  0 
ppdev                   5556  0 
snd_hda_codec_idt      54919  1 
snd_hda_codec_intelhdmi     9812  1 
vboxnetadp              6454  0 
vboxnetflt             15152  0 
vboxdrv               190199  2 vboxnetadp,vboxnetflt
joydev                  8767  0 
arc4                    1165  2 
snd_hda_intel          22235  2 
snd_hda_codec          87552  3 snd_hda_codec_idt,snd_hda_codec_intelhdmi,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
i915                  295435  5 
b43                   168681  0 
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
mac80211              231959  1 b43
drm_kms_helper         30200  1 i915
r852                    9536  0 
sm_common               3285  1 r852
nand                   34905  2 r852,sm_common
btusb                  10969  0 
nand_ids                2903  1 nand
snd_timer              19067  2 snd_pcm,snd_seq
nand_ecc                3938  1 nand
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   168060  5 i915,drm_kms_helper
mtd                    18877  2 sm_common,nand
dell_wmi                2852  0 
uvcvideo               55847  0 
bluetooth              50500  5 rfcomm,sco,bnep,l2cap,btusb
snd                    49038  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dell_laptop             5730  0 
videodev               43098  1 uvcvideo
v4l1_compat            13359  2 uvcvideo,videodev
cfg80211              144694  2 b43,mac80211
dcdbas                  5402  1 dell_laptop
psmouse                59033  0 
intel_agp              26566  2 i915
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
serio_raw               4022  0 
i2c_algo_bit            5168  1 i915
agpgart                32011  2 drm,intel_agp
video                  18712  1 i915
output                  1883  1 video
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
usbhid                 36882  0 
hid                    67742  1 usbhid
sdhci_pci               6601  0 
firewire_ohci          21234  0 
ssb                    39320  1 b43
sdhci                  15922  1 sdhci_pci
led_class               2633  2 b43,sdhci
sky2                   45127  0 
firewire_core          46643  1 firewire_ohci
crc_itu_t               1383  1 firewire_core
[    0.420434] pci 0000:00:02.0: Boot video device
[   15.616039] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   15.779388] Linux video capture interface: v2.00
[   15.913592] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:2640)
[   15.919342] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[   15.925348] uvcvideo: Failed to query (129) UVC probe control : -32 (exp. 26).
[   15.925351] uvcvideo: Failed to initialize the device (-5).
[   15.925650] usbcore: registered new interface driver uvcvideo
[   15.925653] USB Video Class driver (v0.1.0)
[   17.280563] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:00/input/input9
[   17.280716] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   17.280743] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[   24.079217] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0



---

### Post by Jouke74 on 2011-04-13
First thing to test with random crashes is the internal memory (MEMTEST). Although, in this case I tend to agree with the rest that your video chip is acting up.

---

### Post by bluepicaso on 2011-04-13
> **Jouke74 said:**
> First thing to test with random crashes is the internal memory (MEMTEST). Although, in this case I tend to agree with the rest that your video chip is acting up.
How do i do a memtest?
I found a forum that says to press shift ley after bios screen.
What would it do? for how long i should run it. and when?
Will that effect my work?

---

### Post by bluepicaso on 2011-04-13
also how do i remove that video chip diplicate BUs error.
any idea. most of the times is just coz of video. few minutes ago i was due to java. memory $ cpu usage went of the limit. I was using an online banking service...

---

### Post by Alp82 on 2011-04-14
Ok it happened again. Here is the output of **tail -n 100 /var/log/messages**:
```
Apr 14 16:07:24 alp-pc kernel: [   11.905357] WARNING! power/level is deprecated; use power/control instead
Apr 14 16:07:24 alp-pc kernel: [   11.915089] b2c2-flexcop: B2C2 FlexcopII/II(b)/III digital TV receiver chip loaded successfully
Apr 14 16:07:24 alp-pc kernel: [   11.919847] flexcop-pci: will use the HW PID filter.
Apr 14 16:07:24 alp-pc kernel: [   11.919852] flexcop-pci: card revision 2
Apr 14 16:07:24 alp-pc kernel: [   11.919860] b2c2_flexcop_pci 0000:06:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr 14 16:07:24 alp-pc kernel: [   11.919886] ------------[ cut here ]------------
Apr 14 16:07:24 alp-pc kernel: [   11.919890] WARNING: at /build/buildd/linux-2.6.35/fs/proc/generic.c:317 __xlate_proc_name+0xcd/0xf0()
Apr 14 16:07:24 alp-pc kernel: [   11.919891] Hardware name: P67A-UD3P
Apr 14 16:07:24 alp-pc kernel: [   11.919891] name 'Technisat/B2C2 FlexCop II/IIb/III Digital TV PCI Driver'
Apr 14 16:07:24 alp-pc kernel: [   11.919892] Modules linked in: b2c2_flexcop_pci(+) b2c2_flexcop snd_seq_device snd_timer dvb_core cx24123 cx24113 s5h1420 uvcvideo(+) videodev v4l1_compat v4l2_compat_ioctl32 serio_raw joydev snd xhci_hcd soundcore snd_page_alloc intel_agp lp parport usb_storage hid_cherry usbhid hid floppy ahci r8169 libahci mii
Apr 14 16:07:24 alp-pc kernel: [   11.919901] Pid: 725, comm: modprobe Tainted: P            2.6.35-28-generic #49-Ubuntu
Apr 14 16:07:24 alp-pc kernel: [   11.919902] Call Trace:
Apr 14 16:07:24 alp-pc kernel: [   11.919905]  [<ffffffff81060b7f>] warn_slowpath_common+0x7f/0xc0
Apr 14 16:07:24 alp-pc kernel: [   11.919907]  [<ffffffff81060c76>] warn_slowpath_fmt+0x46/0x50
Apr 14 16:07:24 alp-pc kernel: [   11.919908]  [<ffffffff811b09cd>] __xlate_proc_name+0xcd/0xf0
Apr 14 16:07:24 alp-pc kernel: [   11.919910]  [<ffffffff811b17f4>] __proc_create+0x74/0x150
Apr 14 16:07:24 alp-pc kernel: [   11.919911]  [<ffffffff811b1aee>] proc_mkdir_mode+0x2e/0x60
Apr 14 16:07:24 alp-pc kernel: [   11.919912]  [<ffffffff811b1b36>] proc_mkdir+0x16/0x20
Apr 14 16:07:24 alp-pc kernel: [   11.919915]  [<ffffffff810cdf7b>] register_handler_proc+0x11b/0x140
Apr 14 16:07:24 alp-pc kernel: [   11.919917]  [<ffffffff810cb161>] __setup_irq+0x1e1/0x340
Apr 14 16:07:24 alp-pc kernel: [   11.919919]  [<ffffffff81143954>] ? kmem_cache_alloc_notrace+0xb4/0xd0
Apr 14 16:07:24 alp-pc kernel: [   11.919921]  [<ffffffffa00d22d0>] ? flexcop_pci_isr+0x0/0x190 [b2c2_flexcop_pci]
Apr 14 16:07:24 alp-pc kernel: [   11.919922]  [<ffffffff810cbc0c>] request_threaded_irq+0x10c/0x1e0
Apr 14 16:07:24 alp-pc kernel: [   11.919924]  [<ffffffffa00d225d>] flexcop_pci_init+0xcd/0x140 [b2c2_flexcop_pci]
Apr 14 16:07:24 alp-pc kernel: [   11.919925]  [<ffffffffa00d252f>] flexcop_pci_probe+0xcf/0x250 [b2c2_flexcop_pci]
Apr 14 16:07:24 alp-pc kernel: [   11.919928]  [<ffffffff812d7ae7>] local_pci_probe+0x17/0x20
Apr 14 16:07:24 alp-pc kernel: [   11.919930]  [<ffffffff812d7dd9>] __pci_device_probe+0xe9/0xf0
Apr 14 16:07:24 alp-pc kernel: [   11.919932]  [<ffffffff812ba10a>] ? kobject_get+0x1a/0x30
Apr 14 16:07:24 alp-pc kernel: [   11.919935]  [<ffffffff81384c59>] ? get_device+0x19/0x20
Apr 14 16:07:24 alp-pc kernel: [   11.919936]  [<ffffffff812d8e7a>] pci_device_probe+0x3a/0x60
Apr 14 16:07:24 alp-pc kernel: [   11.919938]  [<ffffffff81389018>] really_probe+0x68/0x190
Apr 14 16:07:24 alp-pc kernel: [   11.919939]  [<ffffffff81389185>] driver_probe_device+0x45/0x70
Apr 14 16:07:24 alp-pc kernel: [   11.919940]  [<ffffffff8138924b>] __driver_attach+0x9b/0xa0
Apr 14 16:07:24 alp-pc kernel: [   11.919941]  [<ffffffff813891b0>] ? __driver_attach+0x0/0xa0
Apr 14 16:07:24 alp-pc kernel: [   11.919942]  [<ffffffff81388458>] bus_for_each_dev+0x68/0x90
Apr 14 16:07:24 alp-pc kernel: [   11.919943]  [<ffffffff81388e8e>] driver_attach+0x1e/0x20
Apr 14 16:07:24 alp-pc kernel: [   11.919944]  [<ffffffff8138874e>] bus_add_driver+0xde/0x280
Apr 14 16:07:24 alp-pc kernel: [   11.919946]  [<ffffffff81389590>] driver_register+0x80/0x150
Apr 14 16:07:24 alp-pc kernel: [   11.919949]  [<ffffffff8158f236>] ? notifier_call_chain+0x56/0x80
Apr 14 16:07:24 alp-pc kernel: [   11.919950]  [<ffffffff812d9106>] __pci_register_driver+0x56/0xd0
Apr 14 16:07:24 alp-pc kernel: [   11.919953]  [<ffffffff810853e5>] ? __blocking_notifier_call_chain+0x65/0x80
Apr 14 16:07:24 alp-pc kernel: [   11.919954]  [<ffffffffa00df000>] ? flexcop_pci_module_init+0x0/0x20 [b2c2_flexcop_pci]
Apr 14 16:07:24 alp-pc kernel: [   11.919956]  [<ffffffffa00df01e>] flexcop_pci_module_init+0x1e/0x20 [b2c2_flexcop_pci]
Apr 14 16:07:24 alp-pc kernel: [   11.919958]  [<ffffffff8100204c>] do_one_initcall+0x3c/0x1a0
Apr 14 16:07:24 alp-pc kernel: [   11.919960]  [<ffffffff8109c06b>] sys_init_module+0xbb/0x200
Apr 14 16:07:24 alp-pc kernel: [   11.919963]  [<ffffffff8100a0f2>] system_call_fastpath+0x16/0x1b
Apr 14 16:07:24 alp-pc kernel: [   11.919964] ---[ end trace 1d4e661553122685 ]---
Apr 14 16:07:24 alp-pc kernel: [   11.924502] usblp0: USB Bidirectional printer dev 4 if 0 alt 0 proto 2 vid 0x04F9 pid 0x0190
Apr 14 16:07:24 alp-pc kernel: [   11.924641] usbcore: registered new interface driver usblp
Apr 14 16:07:24 alp-pc kernel: [   11.925205] type=1400 audit(1302790043.159:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=784 comm="apparmor_parser"
Apr 14 16:07:24 alp-pc kernel: [   11.925498] type=1400 audit(1302790043.159:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=784 comm="apparmor_parser"
Apr 14 16:07:24 alp-pc kernel: [   11.925655] type=1400 audit(1302790043.159:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=784 comm="apparmor_parser"
Apr 14 16:07:24 alp-pc kernel: [   11.926302] type=1400 audit(1302790043.159:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=802 comm="apparmor_parser"
Apr 14 16:07:24 alp-pc kernel: [   11.926618] type=1400 audit(1302790043.159:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=802 comm="apparmor_parser"
Apr 14 16:07:24 alp-pc kernel: [   11.926776] type=1400 audit(1302790043.159:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=802 comm="apparmor_parser"
Apr 14 16:07:24 alp-pc kernel: [   11.958397] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Apr 14 16:07:24 alp-pc kernel: [   11.959999] DVB: registering new adapter (FlexCop Digital TV device)
Apr 14 16:07:24 alp-pc kernel: [   11.961449] b2c2-flexcop: MAC address = 00:d0:d7:0f:b4:51
Apr 14 16:07:24 alp-pc kernel: [   12.053602] hda_codec: ALC892: BIOS auto-probing.
Apr 14 16:07:24 alp-pc kernel: [   12.059274] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Apr 14 16:07:24 alp-pc kernel: [   12.059275] hda_intel: Disable MSI for Nvidia chipset
Apr 14 16:07:24 alp-pc kernel: [   12.112093] input: UVC Camera (046d:0821) as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.2/1-1.3.2:1.2/input/input7
Apr 14 16:07:24 alp-pc kernel: [   12.112124] usbcore: registered new interface driver uvcvideo
Apr 14 16:07:24 alp-pc kernel: [   12.112125] USB Video Class driver (v0.1.0)
Apr 14 16:07:24 alp-pc kernel: [   12.170165] b2c2-flexcop: found 'ST STV0299 DVB-S' .
Apr 14 16:07:24 alp-pc kernel: [   12.170167] DVB: registering adapter 0 frontend 0 (ST STV0299 DVB-S)...
Apr 14 16:07:24 alp-pc kernel: [   12.170200] b2c2-flexcop: initialization of 'Sky2PC/SkyStar 2 DVB-S rev 2.6' at the 'PCI' bus controlled by a 'FlexCopIIb' complete
Apr 14 16:07:24 alp-pc kernel: [   12.172267] ICE1724 0000:06:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Apr 14 16:07:24 alp-pc kernel: [   12.233303] juli@: analog I/O detected
Apr 14 16:07:24 alp-pc kernel: [   12.286598] usbcore: registered new interface driver snd-usb-audio
Apr 14 16:07:24 alp-pc kernel: [   12.601775] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
Apr 14 16:07:24 alp-pc kernel: [   13.176302] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null)
Apr 14 16:07:24 alp-pc kernel: [   13.217795] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
Apr 14 16:07:24 alp-pc kernel: [   13.231577] type=1400 audit(1302790044.469:8): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1217 comm="apparmor_parser"
Apr 14 16:07:24 alp-pc kernel: [   13.231969] type=1400 audit(1302790044.469:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1218 comm="apparmor_parser"
Apr 14 16:07:24 alp-pc kernel: [   13.232263] type=1400 audit(1302790044.469:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1218 comm="apparmor_parser"
Apr 14 16:07:24 alp-pc kernel: [   13.232420] type=1400 audit(1302790044.469:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1218 comm="apparmor_parser"
Apr 14 16:07:24 alp-pc kernel: [   13.242725] r8169 0000:04:00.0: eth0: link up
Apr 14 16:07:24 alp-pc kernel: [   13.242730] r8169 0000:04:00.0: eth0: link up
Apr 14 16:07:24 alp-pc kernel: [   13.283005] VBoxDrv: dbg - g_abExecMemory=ffffffffa0e49d60
Apr 14 16:07:24 alp-pc kernel: [   13.283023] vboxdrv: fAsync=0 offMin=0x1e0 offMax=0x12ae
Apr 14 16:07:24 alp-pc kernel: [   13.283045] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Apr 14 16:07:24 alp-pc pulseaudio[1421]: main.c: Running in system mode, but --disallow-exit not set!
Apr 14 16:07:24 alp-pc pulseaudio[1421]: main.c: Running in system mode, but --disallow-module-loading not set!
Apr 14 16:07:24 alp-pc pulseaudio[1421]: main.c: Running in system mode, forcibly disabling SHM mode!
Apr 14 16:07:24 alp-pc pulseaudio[1421]: main.c: Running in system mode, forcibly disabling exit idle time!
Apr 14 16:07:24 alp-pc pulseaudio[1422]: main.c: OK, so you are running PA in system mode. Please note that you most likely shouldn't be doing that.
Apr 14 16:07:24 alp-pc pulseaudio[1422]: main.c: If you do it nonetheless then it's your own fault if things don't work as expected.
Apr 14 16:07:24 alp-pc pulseaudio[1422]: main.c: Please read http://pulseaudio.org/wiki/WhatIsWrongWithSystemMode for an explanation why system mode is usually a bad idea.
Apr 14 16:07:24 alp-pc kernel: [   13.658345] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
Apr 14 16:07:24 alp-pc kernel: [   13.662838] EXT4-fs (sda3): re-mounted. Opts: commit=0
Apr 14 16:07:24 alp-pc kernel: [   13.666761] EXT4-fs (sda6): re-mounted. Opts: commit=0
Apr 14 16:07:25 alp-pc kernel: [   13.804295] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr 14 16:07:25 alp-pc kernel: [   13.804303] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Apr 14 16:07:25 alp-pc kernel: [   13.804426] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  270.41.03  Sat Apr  9 00:06:19 PDT 2011
Apr 14 16:07:25 alp-pc kernel: [   13.935574] ppdev: user-space parallel port driver
Apr 14 16:07:26 alp-pc kernel: [   15.444331] usb 2-1.8: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
Apr 14 16:07:26 alp-pc kernel: [   15.481386] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
Apr 14 16:07:26 alp-pc kernel: [   15.482827] EXT4-fs (sda3): re-mounted. Opts: commit=0
Apr 14 16:07:26 alp-pc kernel: [   15.495056] EXT4-fs (sda6): re-mounted. Opts: commit=0

```

---

### Post by sanguinoso on 2011-04-15
alp82: It looks like there is some kind of kernel problem. ```
WARNING: at /build/buildd/linux-2.6.35/fs/proc/generic.c:317 __xlate_proc_name+0xcd/0xf0()
```

It also looks like its related to your TV Receiver card.
```
name 'Technisat/B2C2 FlexCop II/IIb/III Digital TV PCI Driver'
```

Can you disable that card to confirm that that is the problem?

---

### Post by sanguinoso on 2011-04-15
bluepicaso: memtest just tests your system memory for errors, it takes something like half an hour and will not effect the data on your hard drive. It is definitely worth doing as you added the information that when you ran out memory with java the crash occurred.

---

### Post by Alp82 on 2011-04-16
> **sanguinoso said:**
> alp82: It looks like there is some kind of kernel problem. ```
WARNING: at /build/buildd/linux-2.6.35/fs/proc/generic.c:317 __xlate_proc_name+0xcd/0xf0()
```

It also looks like its related to your TV Receiver card.
```
name 'Technisat/B2C2 FlexCop II/IIb/III Digital TV PCI Driver'
```

Can you disable that card to confirm that that is the problem?

Thank you very much for your reply. I will try it out.

---

### Post by Port 80 on 2011-04-18
Alp 82:

Are you using a NIVIDA driver for video?

---

### Post by Alp82 on 2011-04-18
> **Port 80 said:**
> Alp 82:

Are you using a NIVIDA driver for video?

Yes i do.

---

### Post by sanguinoso on 2011-04-19
Any crashes since?

---

### Post by Alp82 on 2011-04-19
Not yet. Seems to work fine at the moment. I dislike random behavior like that, but it's better than having freezes every day.

---

### Post by sanguinoso on 2011-04-19
Did you disable the TV card?

---

### Post by Alp82 on 2011-04-19
> **sanguinoso said:**
> Did you disable the TV card?

No. But I reduced the overclocking of my CPU from 4,3 to 3,9 GHz. Don't think it has to do with it though, because in Windows I made tests with Prime and actual PC games, which didn't do any trouble.

---

### Post by cespinal on 2011-05-02
any hints yet? I would like some help with this issue, too. 

I would like to start performing a memtest... how do I do that?

---

### Post by Alp82 on 2011-05-02
Didn't have any crashes since then, so i have to say that i have absolutely no clue why.

---

### Post by cespinal on 2011-05-02
I have not had any crashes since yesterday.. I have been removing applications that I have noted make the system crash. Chromium rendered the system unusable. Computer Janitor just does not work and crashes the system every time I use it. 

I'm trying now to force a crash... but so far nothing has happened... .

---

### Post by retchid on 2011-05-02
Obvious answer is overheating given that it worked ok then started going random.

Even more obvious if overclocked.

1. computer full of dust?
2. graphic card overclocked and overheating
3. computer stuck against a wall 
4. fan dead or full of dust?

Next obvious would be Hard Drive on its way out but less likely than overheating.

---

### Post by cespinal on 2011-05-03
Computer works perfectly in Windows 7. It is clean and the hard drive is healthy. 

Next obvious is that 11.04 does not work...

---

### Post by retchid on 2011-05-03
I just installed OPENSUSE 

FAST or WHAT - leaves UBUNTU for Dead

in firefox blink and page  is on screen same in apps also

only negative is a less friendly software manager

---

### Post by retchid on 2011-05-03
odd though I had to format my second drive as fat32 as opensuse could not read it - but that may be because I had the 2nd drive disconnected when installing Opensuse?

also have windows 7 on my computer relieved not to have to reinstall that so quite impressed with opensuse

---

### Post by cespinal on 2011-05-03
Just made some updates and disabled vsync in ccsm.... no crashes in 6 hours... we will see...

---

