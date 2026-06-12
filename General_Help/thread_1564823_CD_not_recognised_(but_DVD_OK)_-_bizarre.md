---
title: "CD not recognised (but DVD OK) - bizarre?"
date: 2010-08-31
forum: General Help
---

### Post by Glyn Hughes on 2010-08-31
I've got Ubuntu 10.04 on a Compaq mini.

Plug in an external USB CD/DVD drive with a **DVD **in and it works perfectly - icon appears on the desktop, DVD is opened and played. But a CD in the same drive is not recognised at all - no icon, sound juicer etc all say 'no CD'.

The drive and CD works perfectly on Mac and Windows, and this model of drive (Duronic) apparently works with other people's Ubuntu. Tried different USB ports and tried it with or without external power. 

Any Ideas?

---

### Post by varunendra on 2010-08-31
Is it same with all CDs or with only this one? And what does the cd contain?

Open nautilus (any folder), click on Edit>Preferences>Media (tab). Check if the settings are appropriate.

---

### Post by Glyn Hughes on 2010-08-31
Thank you varunendra - an excellent suggestion,  but, no, all media is set to "ask what to do" (which works fine with external hard drives and even with this CD/DVD drive when it has a DVD in it) - I tried other several settings, but no success.

I have tried different audio and data CD's - none of them are recognised.

This is especially odd as when you put a CD in the drive it powers up and the laptop's hard disc light flashes away, so I guess something is recognising something.

I really do want to listen to my 'teach yourself French' CD, J'espère que vous comprendrez!

---

### Post by DavidOfLondon on 2010-08-31
Use the subjunctive in French when using verbs of feeling, desire or hope!! Second verb is to always be in the subjunctive when using esperer, sentir etc.

We shall have to re-program you, mon ami.

:-)

Can't help you with sound issues. But as an old man reminded me when I used to live in Paris, "Impossible n'est pas francais!"

And NEVER EVER get baiser and baisser confused. "I kissed your daughter goodnight, madame" can become in French a true danger to your life if mispronounced.

I'm onto Arabic now and by God it is difficult...supposed to be one of the 3 hardest languages to learn for western vernacular speakers - it's conjugated! And the conjugations often don't mean what they say "She-it books they have green they bindings"" is a direct translation of "The books have green bindings". The feminine plural past tense of verbs is the EXACT same as the male singular past tense! How in God's name do these people understand each other?

"They went shopping"

"Oh did he?"

"He who?"

"The guy you just mentioned"

"Are you calling my mother and sister men?"

"Am *I* calling them men or the women?"

"Which women?!?!"

French is a true joy by comparison. And if you ever get to Paris you'll hear Algerians speaking both languages!

---

### Post by varunendra on 2010-09-01
> **Glyn Hughes said:**
> I have tried different audio and data CD's - none of them are recognised.
This is especially odd as when you put a CD in the drive it powers up and the laptop's hard disc light flashes away, so I guess something is recognising something.

If the OS even tries to read, there must be kernel event logs. Please incert a cd, and after the LEDs go off, enter & post output of:
```
dmesg | tail -20
```
```
sudo mount
```

> **DavidOfLondon said:**
> ....
....And NEVER EVER get baiser and baisser confused. "I kissed your daughter goodnight, madame" can become in French a true danger to your life if mispronounced....
....And the conjugations often don't mean what they say "She-it books they have green they bindings"" is a direct translation of "The books have green bindings". The feminine plural past tense of verbs is the EXACT same as the male singular past tense! How in God's name do these people understand each other?....
"They went shopping"
"Oh did he?"
"He who?"
"The guy you just mentioned"
"Are you calling my mother and sister men?"
"Am *I* calling them men or the women?"
"Which women?!?!"....
....not the right place for such posts, but given the quality of humor you made, you are [COLOR=Red]**EXECUTED**[/COLOR]..... err.. oh.. sorry,.. I mean **Excused** !!
:lolflag:

---

### Post by Glyn Hughes on 2010-09-01
Varunendra, here is the output. I'm afraid it is rather long..

WITH CD
dmesg | tail -20
[106855.180156] sr 9:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[106855.180191] end_request: I/O error, dev sr0, sector 0
[106855.186080] sr 9:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[106855.186107] sr 9:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[106855.186135] Info fld=0x400, ILI
[106855.186147] sr 9:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[106855.186179] sr 9:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 04 00 00 00 02 00
[106855.186232] end_request: I/O error, dev sr0, sector 4096
[106855.449953] sr 9:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[106855.449979] sr 9:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[106855.450006] Info fld=0x0, ILI
[106855.450017] sr 9:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[106855.450047] sr 9:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[106855.450099] end_request: I/O error, dev sr0, sector 0
[106855.454077] sr 9:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[106855.454107] sr 9:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[106855.454137] Info fld=0x0, ILI
[106855.454149] sr 9:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[106855.454181] sr 9:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[106855.454234] end_request: I/O error, dev sr0, sector 0
glyn@glyn-laptop:~$ 

sudo mount
[sudo] password for glyn: 
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
none on /var/lib/ureadahead/debugfs type debugfs (rw,relatime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/glyn/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=glyn)
glyn@glyn-laptop:~$ 

WITH DVD
dmesg | tail -20
[107042.397345] sr 10:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[107042.397374] sr 10:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[107042.397402] Info fld=0x400, ILI
[107042.397415] sr 10:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[107042.397447] sr 10:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 04 00 00 00 02 00
[107042.397500] end_request: I/O error, dev sr0, sector 4096
[107042.589854] sr 10:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[107042.589877] sr 10:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[107042.589898] Info fld=0x0, ILI
[107042.589907] sr 10:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[107042.589929] sr 10:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[107042.589965] end_request: I/O error, dev sr0, sector 0
[107042.593499] sr 10:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[107042.593527] sr 10:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[107042.593555] Info fld=0x0, ILI
[107042.593567] sr 10:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[107042.593599] sr 10:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[107042.593653] end_request: I/O error, dev sr0, sector 0
[107204.805382] UDF-fs: Partition marked readonly; forcing readonly mount
[107204.856760] UDF-fs INFO UDF: Mounting volume 'COMEDY', timestamp 2005/01/29 13:34 (103c)
glyn@glyn-laptop:~$ 

sudo mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
none on /var/lib/ureadahead/debugfs type debugfs (rw,relatime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/glyn/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=glyn)
/dev/sr0 on /media/COMEDY type udf (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077)
glyn@glyn-laptop:~$

---

### Post by varunendra on 2010-09-01
> **Glyn Hughes said:**
> 
[106855.454077] sr 9:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[106855.454107] sr 9:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[106855.454137] Info fld=0x0, ILI
[106855.454149] sr 9:0:0:0: [sr0] Add. Sense: **Illegal mode for this track**
[106855.454181] sr 9:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[106855.454234] **end_request: I/O error, dev sr0, sector 0**
glyn@glyn-laptop:~$ 

**WITH DVD**
dmesg | tail -20
[107204.805382] UDF-fs: Partition marked readonly; forcing readonly mount
[107204.856760]** UDF-fs INFO UDF: Mounting volume** 'COMEDY', timestamp 2005/01/29 13:34 (103c)
glyn@glyn-laptop:~$ 

sudo mount
/dev/sr0 on /media/COMEDY type udf (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077)
glyn@glyn-laptop:~$
I'm unable to conclude anything from this except that it is apparently a hardware or driver issue, not a settings problem.

You said the same drive+cd have no issues on **other people's ubuntu**, so I suggest you to check the drivers on their system handling the drive & compare them with yours.

To check the drivers use these commands:
```
lsmod
```, and,
```
lspci -v
```

Note the drivers/kernel-modules for USB, SCSI, and IDE.

If unsure, post those results back here (only the lines associated with above devices should be sufficient).

For now, this is all I could think of. I'll try to have a deeper look into this & would get back if found something relevant.

---

### Post by Glyn Hughes on 2010-09-01
Thank you for that. Here is the code, I'm afraid I can't send just the important bits, as none of it makes any sense to me. Your help is very much appreciated.

WITH CD
lsmod
Module                  Size  Used by
nls_utf8                1069  0 
udf                    78785  0 
crc_itu_t               1371  1 udf
isofs                  29250  0 
usb_storage            39425  0 
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_nvhdmi     3840  1 
snd_hda_codec_idt      51978  1 
rfcomm                 33421  4 
sco                     7885  2 
snd_hda_intel          21941  2 
snd_hda_codec          74201  3 snd_hda_codec_nvhdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
bridge                 45582  0 
stp                     1655  1 bridge
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
bnep                    9436  2 
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
l2cap                  30624  16 rfcomm,bnep
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
fbcon                  35102  71 
snd_timer              19098  2 snd_pcm,snd_seq
tileblit                2031  1 fbcon
lib80211_crypt_tkip     7596  0 
font                    7557  1 fbcon
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd                    54148  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wl                   1959598  0 
video                  17375  0 
vga16fb                11385  1 
uvcvideo               56990  0 
lp                      7028  0 
soundcore               6620  1 snd
psmouse                63245  0 
i2c_nforce2             5199  0 
videodev               34361  1 uvcvideo
lib80211                5046  2 lib80211_crypt_tkip,wl
vgastate                8961  1 vga16fb
output                  1871  1 video
btusb                  10925  2 
nvidia               9961216  44 
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
v4l1_compat            13251  2 uvcvideo,videodev
serio_raw               3978  0 
shpchp                 28820  0 
bluetooth              49892  9 rfcomm,sco,bnep,l2cap,btusb
agpgart                31724  1 nvidia
parport                32635  2 ppdev,lp
ahci                   32200  2 
forcedeth              49556  0 

WITH CD
lspci -v
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
    Subsystem: Hewlett-Packard Company Device 3651
    Flags: bus master, 66MHz, fast devsel, latency 0

00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
    Subsystem: Hewlett-Packard Company Device 3651
    Flags: bus master, 66MHz, fast devsel, latency 0

00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b3)
    Subsystem: Hewlett-Packard Company Device 3651
    Flags: bus master, 66MHz, fast devsel, latency 0

00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
    Subsystem: Hewlett-Packard Company Device 3651
    Flags: 66MHz, fast devsel

00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
    Subsystem: Hewlett-Packard Company Device 3651
    Flags: 66MHz, fast devsel, IRQ 11
    I/O ports at 3080 [size=64]
    I/O ports at 3040 [size=64]
    I/O ports at 3000 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: nForce2_smbus
    Kernel modules: i2c-nforce2

00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
    Subsystem: Hewlett-Packard Company Device 3651
    Flags: 66MHz, fast devsel

00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
    Subsystem: Hewlett-Packard Company Device 3651
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    Memory at feb80000 (32-bit, non-prefetchable) [size=512K]
    Kernel driver in use: nvidia
    Kernel modules: nvidia-current

00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1) (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 3651
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    Memory at d3108000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1) (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 3651
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
    Memory at d3109200 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1) (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 3651
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
    Memory at d3107000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1) (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 3651
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    Memory at d3109100 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
    Subsystem: Hewlett-Packard Company Device 3651
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
    Memory at d3100000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1) (prog-if 01)
    Flags: bus master, 66MHz, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    Capabilities: <access denied>

00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
    Subsystem: Hewlett-Packard Company Device 3651
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
    Memory at d3106000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at 30e0 [size=8]
    Memory at d3109000 (32-bit, non-prefetchable) [size=256]
    Memory at d3109300 (32-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>
    Kernel driver in use: forcedeth
    Kernel modules: forcedeth

00:0b.0 SATA controller: nVidia Corporation MCP79 AHCI Controller (rev b1) (prog-if 01)
    Subsystem: Hewlett-Packard Company Device 3651
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 26
    I/O ports at 30d8 [size=8]
    I/O ports at 30ec [size=4]
    I/O ports at 30d0 [size=8]
    I/O ports at 30e8 [size=4]
    I/O ports at 30c0 [size=16]
    Memory at d3104000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: d2000000-d2ffffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000d1ffffff
    Capabilities: <access denied>
    Kernel modules: shpchp

00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Memory behind bridge: d3000000-d30fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

02:00.0 VGA compatible controller: nVidia Corporation C79 [Quadro FX 470M] (rev b1)
    Subsystem: Hewlett-Packard Company Device 3651
    Flags: bus master, fast devsel, latency 0, IRQ 20
    Memory at d2000000 (32-bit, non-prefetchable) [size=16M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at d0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at 2000 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia-173, nvidia-current, nvidiafb, nouveau

03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
    Subsystem: Hewlett-Packard Company Device 365e
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at d3000000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: wl
    Kernel modules: wl, ssb

WITH DVD
lsmod
Module                  Size  Used by
nls_utf8                1069  1 
udf                    78785  1 
crc_itu_t               1371  1 udf
isofs                  29250  0 
usb_storage            39425  1 
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_nvhdmi     3840  1 
snd_hda_codec_idt      51978  1 
rfcomm                 33421  4 
sco                     7885  2 
snd_hda_intel          21941  2 
snd_hda_codec          74201  3 snd_hda_codec_nvhdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
bridge                 45582  0 
stp                     1655  1 bridge
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
bnep                    9436  2 
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
l2cap                  30624  16 rfcomm,bnep
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
fbcon                  35102  71 
snd_timer              19098  2 snd_pcm,snd_seq
tileblit                2031  1 fbcon
lib80211_crypt_tkip     7596  0 
font                    7557  1 fbcon
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd                    54148  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wl                   1959598  0 
video                  17375  0 
vga16fb                11385  1 
uvcvideo               56990  0 
lp                      7028  0 
soundcore               6620  1 snd
psmouse                63245  0 
i2c_nforce2             5199  0 
videodev               34361  1 uvcvideo
lib80211                5046  2 lib80211_crypt_tkip,wl
vgastate                8961  1 vga16fb
output                  1871  1 video
btusb                  10925  2 
nvidia               9961216  44 
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
v4l1_compat            13251  2 uvcvideo,videodev
serio_raw               3978  0 
shpchp                 28820  0 
bluetooth              49892  9 rfcomm,sco,bnep,l2cap,btusb
agpgart                31724  1 nvidia
parport                32635  2 ppdev,lp
ahci                   32200  2 
forcedeth              49556  0 

WITH DVD 
lspci -v
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
    Subsystem: Hewlett-Packard Company Device 3651
    Flags: bus master, 66MHz, fast devsel, latency 0

00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
    Subsystem: Hewlett-Packard Company Device 3651
    Flags: bus master, 66MHz, fast devsel, latency 0

00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b3)
    Subsystem: Hewlett-Packard Company Device 3651
    Flags: bus master, 66MHz, fast devsel, latency 0

00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
    Subsystem: Hewlett-Packard Company Device 3651
    Flags: 66MHz, fast devsel

00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
    Subsystem: Hewlett-Packard Company Device 3651
    Flags: 66MHz, fast devsel, IRQ 11
    I/O ports at 3080 [size=64]
    I/O ports at 3040 [size=64]
    I/O ports at 3000 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: nForce2_smbus
    Kernel modules: i2c-nforce2

00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
    Subsystem: Hewlett-Packard Company Device 3651
    Flags: 66MHz, fast devsel

00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
    Subsystem: Hewlett-Packard Company Device 3651
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    Memory at feb80000 (32-bit, non-prefetchable) [size=512K]
    Kernel driver in use: nvidia
    Kernel modules: nvidia-current

00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1) (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 3651
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    Memory at d3108000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1) (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 3651
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
    Memory at d3109200 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1) (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 3651
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
    Memory at d3107000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1) (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 3651
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    Memory at d3109100 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
    Subsystem: Hewlett-Packard Company Device 3651
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
    Memory at d3100000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1) (prog-if 01)
    Flags: bus master, 66MHz, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    Capabilities: <access denied>

00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
    Subsystem: Hewlett-Packard Company Device 3651
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
    Memory at d3106000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at 30e0 [size=8]
    Memory at d3109000 (32-bit, non-prefetchable) [size=256]
    Memory at d3109300 (32-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>
    Kernel driver in use: forcedeth
    Kernel modules: forcedeth

00:0b.0 SATA controller: nVidia Corporation MCP79 AHCI Controller (rev b1) (prog-if 01)
    Subsystem: Hewlett-Packard Company Device 3651
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 26
    I/O ports at 30d8 [size=8]
    I/O ports at 30ec [size=4]
    I/O ports at 30d0 [size=8]
    I/O ports at 30e8 [size=4]
    I/O ports at 30c0 [size=16]
    Memory at d3104000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: d2000000-d2ffffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000d1ffffff
    Capabilities: <access denied>
    Kernel modules: shpchp

00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Memory behind bridge: d3000000-d30fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

02:00.0 VGA compatible controller: nVidia Corporation C79 [Quadro FX 470M] (rev b1)
    Subsystem: Hewlett-Packard Company Device 3651
    Flags: bus master, fast devsel, latency 0, IRQ 20
    Memory at d2000000 (32-bit, non-prefetchable) [size=16M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at d0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at 2000 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia-173, nvidia-current, nvidiafb, nouveau

03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
    Subsystem: Hewlett-Packard Company Device 365e
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at d3000000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: wl
    Kernel modules: wl, ssb

glyn@glyn-laptop:~$

---

### Post by varunendra on 2010-09-01
No good news yet. All I found so far was that the error messages you found in dmesg are common with mostly audio cds (see [here]("http://ubuntuforums.org/showthread.php?t=1329530"), there are many such examples including bug reports). But your problem is same with all kind of CDs!

Sorry for not being able to help yet, however, here are a few tips for your existing & future posts:

[LIST]
[*]To make the posts short & outputs more readable, always use **[ code]*(pasted output)*[ /code]** tags around the pasted outputs. To do so, just highlight the pasted text, and click on the # mark on the editing panel. (let's see how you do this with your previous post :))
[*]Once the OS is loaded, the outputs of lsmod & lspci don't change with the status of hardware (as far as I know, but I may be wrong on this). They are just meant to see which module is used for which device. So you may safely remove the repeated outputs with/without CD/DVD. Keeping only one set of those outputs would make your post shorter & easy to read in case someone else wants to have a look at them.
[*]Now that you've posted the results for your hardware, I want to see the same outputs for any other ubuntu machine on which the cd (with the same cd drive) is readable. (do it while the drive is connected & the cd is loaded).
[*]You can safely remove parts of outputs that are clearly related with devices not relevant for this issue (like-RAM, processor, audio, video,... etc.) but if you have doubts, it is absolutely okay to leave them and post the complete result :).
[/LIST]
I know all of this is irrelevant with your problem, but following these would help getting you better attention of anyone who maybe willing to help.



However, the more important thing for now is to confirm these:

[LIST=1]
[*]The same cd is readable on at least one other ubuntu machine.
[*]Apart from audio cds, data cds are also unreadable (& same are readable on the same drive, with other machine)
[/LIST]
Things to try/check:

[LIST=1]
[*]Try a shorter USB lead (if possible, less than a meter to ensure minimum loss of data signals)
[*]Compare outputs of lsmod and lspci -v obtained from the other computer on which the drive is working.
[/LIST]

---

### Post by Glyn Hughes on 2010-09-01
Thank you very much Varunendra, but I'm afraid this has become far beyond my comprehension or ability. I would just like to play a CD, that is all, so, sadly, I must abandon Ubuntu. Pity.

Thank you again.

---

### Post by varunendra on 2010-09-01
Whatever I've found so far suggests that it most probably is an unfixed bug for which there may be workarounds, only I've not been able to find them yet.

Besides, I'm still not mature enough to know about commands that give precise & more comprehensive outputs. I've just started learning them!

If you are planning to switch to some other OS or distro, I'd suggest to give Mint9 or Kubuntu a shot.

Sorry for scaring you with those HUGE outputs. :D. Hopefully, You'd find yourself a more suitable OS/distro. Best of luck for that!

However, I'll get back to this thread **IF** I found something really useful.

---

