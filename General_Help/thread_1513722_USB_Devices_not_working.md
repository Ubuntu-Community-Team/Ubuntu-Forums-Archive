---
title: "USB Devices not working"
date: 2010-06-19
forum: General Help
---

### Post by RJ12 on 2010-06-19
For some reason my USB devices just stopped working. I'm on my laptop, so I really don't need a USB Mouse but I like to use it. I also can't use my flash drive. The Command lsusb sees it. It will see both the mouse and my flash drive. I don't have any other devices to test, but I would like to know that they would work when I need them. I really need help solving this. The strange thing is it also used to work. I don't know what changed.:confused:

---

### Post by RJ12 on 2010-06-20
Anyone?

---

### Post by RJ12 on 2010-06-20
Do you guys need some output?

---

### Post by happyhamster on 2010-06-20
> **RJ12 said:**
> Do you guys need some output?
Yes :) Could you show the output of:

uname -a

dmesg | grep usb

dmesg | grep error

cat /proc/interrupts

---

### Post by RJ12 on 2010-06-20
Sure! 


Output of uname -a
```
Linux ubuntu-laptop 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
```

Output of dmesg | grep usb
```
[    0.204058] usbcore: registered new interface driver usbfs
[    0.204070] usbcore: registered new interface driver hub
[    0.204094] usbcore: registered new device driver usb
[    0.341520] usb usb1: configuration #1 chosen from 1 choice
[    0.392260] usb usb2: configuration #1 chosen from 1 choice
[    0.497190] usb usb3: configuration #1 chosen from 1 choice
[    0.600768] usb usb4: configuration #1 chosen from 1 choice
[    0.700667] usb usb5: configuration #1 chosen from 1 choice
[    0.772021] usb usb6: configuration #1 chosen from 1 choice
[   11.832885] usbcore: registered new interface driver ndiswrapper
[ 5114.664087] usb 3-1: new low speed USB device using ohci_hcd and address 2
[ 5114.850098] usb 3-1: configuration #1 chosen from 1 choice
[ 5127.966257] usb 3-1: USB disconnect, address 2

```

Output of dmesg | grep error (None)

Output of cat /proc/interrupts

```
           CPU0       
  0:         73   IO-APIC-edge      timer
  1:        615   IO-APIC-edge      i8042
  7:          1   IO-APIC-edge    
  8:          1   IO-APIC-edge      rtc0
  9:       2720   IO-APIC-fasteoi   acpi
 12:      44975   IO-APIC-edge      i8042
 14:          0   IO-APIC-edge      pata_atiixp
 15:          0   IO-APIC-edge      pata_atiixp
 16:       1518   IO-APIC-fasteoi   ohci_hcd:usb3, ohci_hcd:usb4, HDA Intel
 17:          2   IO-APIC-fasteoi   ehci_hcd:usb1
 18:      22328   IO-APIC-fasteoi   ohci_hcd:usb5, ohci_hcd:usb6, radeon, ndiswrapper
 19:          0   IO-APIC-fasteoi   ehci_hcd:usb2
 22:      48069   IO-APIC-fasteoi   ahci
 27:          0   PCI-MSI-edge      eth0
NMI:          0   Non-maskable interrupts
LOC:     572647   Local timer interrupts
SPU:          0   Spurious interrupts
PMI:          0   Performance monitoring interrupts
PND:          0   Performance pending work
RES:          0   Rescheduling interrupts
CAL:          0   Function call interrupts
TLB:          0   TLB shootdowns
TRM:          0   Thermal event interrupts
THR:          0   Threshold APIC interrupts
MCE:          0   Machine check exceptions
MCP:         20   Machine check polls
ERR:          1
MIS:          0

```


Thank you for responding :p

---

### Post by happyhamster on 2010-06-20
- What does:

dmesg | grep usb

- show after you disconnect and re-connect the mouse? Is it a wireless mouse? Could you also show the output of:

lsmod

- It will show which modules are in use, and:

lspci

- Which will show detailed info about the hardware.

- Something to test: attach the mouse/drive to different usb ports.

- Another thing you could try: boot from a live cd. If the mouse/drive do work in that environment, it would be useful to see if there are differences in the output of: 

dmesg | grep usb

lsmod

lspci

- in that case. Good luck.

---

### Post by RJ12 on 2010-06-20
Its a wired mouse, but see all of my USB devices do not work. Here is the output of 
dmesg | usb after disconnecting and reconnecting

```
[    0.204058] usbcore: registered new interface driver usbfs
[    0.204070] usbcore: registered new interface driver hub
[    0.204094] usbcore: registered new device driver usb
[    0.341520] usb usb1: configuration #1 chosen from 1 choice
[    0.392260] usb usb2: configuration #1 chosen from 1 choice
[    0.497190] usb usb3: configuration #1 chosen from 1 choice
[    0.600768] usb usb4: configuration #1 chosen from 1 choice
[    0.700667] usb usb5: configuration #1 chosen from 1 choice
[    0.772021] usb usb6: configuration #1 chosen from 1 choice
[   11.832885] usbcore: registered new interface driver ndiswrapper
[ 5114.664087] usb 3-1: new low speed USB device using ohci_hcd and address 2
[ 5114.850098] usb 3-1: configuration #1 chosen from 1 choice
[ 5127.966257] usb 3-1: USB disconnect, address 2
[ 5549.992031] PM: resume of drv:usb dev:usb1 complete after 147.851 msecs
[10491.732045] usb 3-2: new low speed USB device using ohci_hcd and address 3
[10491.901273] usb 3-2: configuration #1 chosen from 1 choice
[10533.751820] usb 3-2: USB disconnect, address 3

```

Output of lsmod

```
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
vboxnetadp              6326  0 
vboxnetflt             15194  0 
vboxdrv               190409  2 vboxnetadp,vboxnetflt
joydev                  8708  0 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_codec_realtek   203168  1 
snd_hda_intel          21877  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
radeon                674135  3 
ttm                    49943  1 radeon
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
drm_kms_helper         29297  1 radeon
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
drm                   162471  5 radeon,ttm,drm_kms_helper
agpgart                31724  2 ttm,drm
i2c_algo_bit            5028  1 radeon
snd                    54148  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                63245  0 
serio_raw               3978  0 
ndiswrapper           184677  0 
shpchp                 28820  0 
i2c_piix4               8335  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
video                  17375  0 
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
pata_atiixp             3148  0 
r8169                  33884  0 
mii                     4381  1 r8169
ahci                   32008  3 
```

Output of lspci

```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Toshiba America Info Systems Device 9602
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780MC [Radeon HD 3100 Graphics]
0e:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller (rev 22)
14:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

```

I will post the output differences once I am in a live environment.


The Following Output is from the live usb

dmesg | grep usb

```
[    0.000000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz noprompt cdrom-detect/try-usb=true file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash -- maybe-ubiquity
[    0.180574] usbcore: registered new interface driver usbfs
[    0.180586] usbcore: registered new interface driver hub
[    0.180610] usbcore: registered new device driver usb
[    2.448214] usb usb1: configuration #1 chosen from 1 choice
[    2.498914] usb usb2: configuration #1 chosen from 1 choice
[    2.580397] usb usb3: configuration #1 chosen from 1 choice
[    2.681745] usb usb4: configuration #1 chosen from 1 choice
[    2.777714] usb usb5: configuration #1 chosen from 1 choice
[    2.869920] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    2.874047] usb usb6: configuration #1 chosen from 1 choice
[    3.005555] usb 1-1: configuration #1 chosen from 1 choice
[    3.448608] usbcore: registered new interface driver usb-storage
[    3.448716] usb-storage: device found at 2
[    3.448718] usb-storage: waiting for device to settle before scanning
[    8.448174] usb-storage: device scan complete
[   81.332013] usb 3-3: new low speed USB device using ohci_hcd and address 2
[   81.502730] usb 3-3: configuration #1 chosen from 1 choice
[   81.537005] usbcore: registered new interface driver hiddev
[   81.543380] input: Dell Dell USB Mouse as /devices/pci0000:00/0000:00:12.0/usb3/3-3/3-3:1.0/input/input8
[   81.543596] generic-usb 0003:413C:3200.0001: input,hidraw0: USB HID v1.10 Mouse [Dell Dell USB Mouse] on usb-0000:00:12.0-3/input0
[   81.543634] usbcore: registered new interface driver usbhid
[   81.544900] usbhid: v2.6:USB HID core driver
```

Output of lsmod

```
Module                  Size  Used by
usbhid                 36110  0 
hid                    67032  1 usbhid
binfmt_misc             6587  1 
ppdev                   5259  0 
lp                      7028  0 
parport                32635  2 ppdev,lp
joydev                  8708  0 
dm_crypt               11331  0 
snd_hda_codec_realtek   203168  1 
snd_hda_intel          21877  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54148  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               6620  1 snd
psmouse                63245  0 
shpchp                 28820  0 
serio_raw               3978  0 
rtl8187se             159435  0 
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
i2c_piix4               8335  0 
squashfs               20680  1 
aufs                  149050  1 
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8901  1 
fat                    47767  1 vfat
dm_raid45              81647  0 
xor                    15028  1 dm_raid45
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
radeon                674135  3 
ttm                    49943  1 radeon
drm_kms_helper         29297  1 radeon
drm                   162471  5 radeon,ttm,drm_kms_helper
usb_storage            39425  1 
agpgart                31724  2 ttm,drm
i2c_algo_bit            5028  1 radeon
pata_atiixp             3148  0 
r8169                  33884  0 
mii                     4381  1 r8169
ahci                   32008  1 
video                  17375  0 
output                  1871  1 video

```

Output of lspci

```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Toshiba America Info Systems Device 9602
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780MC [Radeon HD 3100 Graphics]
0e:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller (rev 22)
14:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

```

The mouse works perfectly in the live usb. I can't test my flash drive because its being used by the Live USB

---

### Post by warfacegod on 2010-06-20
I ran into this several times in the last few weeks. First few times, I fixed it by reinstalling Ubuntu. After a while I realized that the whole thing was my own fault. The combination of updates and the 800 MB or so that I remove from Ubuntu, after an install, was causing my USB drives to not mount. I used Synaptic and reinstalled the ubuntu-desktop package and everything was better again. I'm not sure which package ubuntu-desktop pulled in that actually fixed the problem so I've been more conservative about removing things.

---

### Post by RJ12 on 2010-06-20
> **warfacegod said:**
> I ran into this several times in the last few weeks. First few times, I fixed it by reinstalling Ubuntu. After a while I realized that the whole thing was my own fault. The combination of updates and the 800 MB or so that I remove from Ubuntu, after an install, was causing my USB drives to not mount. I used Synaptic and reinstalled the ubuntu-desktop package and everything was better again. I'm not sure which package ubuntu-desktop pulled in that actually fixed the problem so I've been more conservative about removing things.

Well I have not done any updates yet (waiting on something)

But I just found something out...

I did not plug my mouse out after I rebooted... Logged in and by mistake moved the mouse, it works!! But bad news is plugging in my flash drive did not work...


But more good news! I plugged out the mouse and put the flash drive in that USB port, it works! It also works with different USB ports! I will reboot without it plugged in and see what will work.



After Reboot:

None of the USB devices worked :(

---

### Post by happyhamster on 2010-06-20
- When the mouse isn't working, try loading the module usbhid manually:

sudo modprobe usbhid

- and see if that will get the mouse to work. (Perhaps you'll have to unplug - replug it to see any effect.)

---

### Post by RJ12 on 2010-06-20
> **happyhamster said:**
> - When the mouse isn't working, try loading the module usbhid manually:

sudo modprobe usbhid

- and see if that will get the mouse to work. (Perhaps you'll have to unplug - replug it to see any effect.)

THANK YOU!! That made the mouse work!! But the Flash Drive still isn't working 

:(
:p

---

### Post by happyhamster on 2010-06-20
> **RJ12 said:**
> THANK YOU!! That made the mouse work!! But the Flash Drive still isn't working 
- For the drive, it's likely the module usb_storage:

sudo modprobe usb_storage

- but the real problem is why those modules aren't loading automatically. Make sure the system is fully upgraded. Also: are there exotic configuration options or packages you're using? I'm thinking about manually-set boot parameters, or using something experimental as the xorg-edgers repository for example. 

- Finally, although I doubt you're affected by this bug:
[https://bugs.launchpad.net/ubuntu/+source/irqbalance/+bug/528720](https://bugs.launchpad.net/ubuntu/+source/irqbalance/+bug/528720)
it would be nice to rule it out. Try uninstalling the package "irqbalance" which causes problems for lots of people on Ubuntu Lucid. It's a daemon that balances the distribution of interrupts for multicore systems, so it can safely be removed on single-core systems. 

Good luck.

---

### Post by RJ12 on 2010-06-20
> **happyhamster said:**
> - For the drive, it's likely the module usb_storage:

sudo modprobe usb_storage

- but the real problem is why those modules aren't loading automatically. Make sure the system is fully upgraded. Also: are there exotic configuration options or packages you're using? I'm thinking about manually-set boot parameters, or using something experimental as the xorg-edgers repository for example. 

- Finally, although I doubt you're affected by this bug:
[https://bugs.launchpad.net/ubuntu/+source/irqbalance/+bug/528720](https://bugs.launchpad.net/ubuntu/+source/irqbalance/+bug/528720)
it would be nice to rule it out. Try uninstalling the package "irqbalance" which causes problems for lots of people on Ubuntu Lucid. It's a daemon that balances the distribution of interrupts for multicore systems, so it can safely be removed on single-core systems. 

Good luck.

That made my flash drive work! But now after reboot it does not stay, even after uninstalling the irqbalance package and rebooting. By upgraded do you mean updated? I am always weary about doing the system updates. I am also wondering why the modules are not loading by them selves. I don't have any wacky configs (like boot paramaters)

---

### Post by happyhamster on 2010-06-21
> **RJ12 said:**
> That made my flash drive work! But now after reboot it does not stay, even after uninstalling the irqbalance package and rebooting.
- To force loading the modules permanently, add the names of the modules to the file /etc/modules :

gksudo gedit /etc/modules

- In my case, the file looks like this:
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc

```

- Just add the module names:

```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
usbhid
usb_storage

```
Save, and exit the text editor. Then reboot.

> 
 By upgraded do you mean updated? I am always weary about doing the system updates.
There are sometimes troubles because of updates, true (especially if you're using proprietary video/network drivers). But most updates are there to protect you. Give them a chance :)

>  I am also wondering why the modules are not loading by them selves. I don't have any wacky configs (like boot paramaters)
Editing /etc/modules is just patching some unknown problem IMHO, but I have no further ideas at this point. If you're not tired of trying to debug this yet, could you post the entire dmesg output here (dmesg output without having the modules loaded manually, and preferably after having removed and re-attached both drive and mouse). Good luck.

---

### Post by RJ12 on 2010-06-21
Ok, strange results this reboot...

The USB Flash Drive worked, mouse didn't.


I didn't load the modules manually or change the modules file.

I wonder what will happen after I shutdown and power back up, anyway I put the output of dmesg in a text file (It was very big, it exceeded forum upload limit)

---

### Post by happyhamster on 2010-06-21
Hello again.

> **RJ12 said:**
> Ok, strange results this reboot...

The USB Flash Drive worked, mouse didn't.
Ok, so it looks a bit random then. I have been looking on launchpad for bugreports on this, and there are a zillion, some reported for gvfs, hdparm, the kernel, xserver-xorg-input-keyboard, udev, etc. There's just way too much of them.

- Could you show the output of:

ls /lib/udev/rules.d/ -l

- It will show if the udev files are intact.

- Do you get the erratic usb behaviour when booting another kernel? To do this: boot into the grub menu (hold the shift key during the early stages of the boot proces). Select a lower kernel to boot, for example 2.6.32-19, and test if things are any better.

- Also: did you perhaps tweak ubuntu for low-power usage (using a tool as powertop for example)?

[edit: thanks for the log. It shows that the kernel applies some usb workaround for the chipset found in the laptop. That's why booting another kernel is interesting.]

---

### Post by RJ12 on 2010-06-21
Here is your output

```
total 620
-rw-r--r-- 1 root root     29 2010-01-26 18:26 40-fuse-utils.rules
-rw-r--r-- 1 root root    583 2010-01-05 04:43 40-gnupg.rules
-rw-r--r-- 1 root root   6733 2010-04-12 05:47 40-hplip.rules
-rw-r--r-- 1 root root     90 2009-12-03 06:45 40-ia64.rules
-rw-r--r-- 1 root root    410 2009-12-03 06:45 40-infiniband.rules
-rw-r--r-- 1 root root    180 2009-12-03 06:45 40-isdn.rules
-rw-r--r-- 1 root root 150222 2010-04-22 13:55 40-libgphoto2-2.rules
-rw-r--r-- 1 root root   2656 2010-01-06 02:12 40-libpisock9.rules
-rw-r--r-- 1 root root  42579 2010-04-14 21:24 40-libsane.rules
-rw-r--r-- 1 root root    174 2009-12-03 06:45 40-pilot-links.rules
-rw-r--r-- 1 root root    212 2009-12-03 06:45 40-ppc.rules
-rw-r--r-- 1 root root  14829 2010-04-11 07:24 40-usb-media-players.rules
-rw-r--r-- 1 root root    495 2010-04-26 02:43 40-xserver-xorg-video-intel.rules
-rw-r--r-- 1 root root    334 2009-12-03 06:45 40-zaptel.rules
-rw-r--r-- 1 root root     30 2010-01-26 18:26 45-fuse.rules
-rw-r--r-- 1 root root  72677 2010-02-17 03:43 45-libmtp8.rules
-rw-r--r-- 1 root root    219 2010-04-19 04:30 50-firmware.rules
-rw-r--r-- 1 root root   4140 2010-04-19 04:30 50-udev-default.rules
-rw-r--r-- 1 root root   2688 2010-04-26 01:00 55-dm.rules
-rw-r--r-- 1 root root    445 2010-04-12 05:47 56-hpmud_support.rules
-rw-r--r-- 1 root root    240 2010-04-19 04:30 60-cdrom_id.rules
-rw-r--r-- 1 root root    250 2010-04-19 04:30 60-floppy.rules
-rw-r--r-- 1 root root    676 2010-04-19 04:30 60-persistent-alsa.rules
-rw-r--r-- 1 root root   2005 2010-04-19 04:30 60-persistent-input.rules
-rw-r--r-- 1 root root    893 2010-04-19 04:30 60-persistent-serial.rules
-rw-r--r-- 1 root root    767 2010-04-26 01:00 60-persistent-storage-dm.rules
-rw-r--r-- 1 root root   4768 2010-04-19 04:30 60-persistent-storage.rules
-rw-r--r-- 1 root root   1450 2010-04-19 04:30 60-persistent-storage-tape.rules
-rw-r--r-- 1 root root    789 2010-04-19 04:30 60-persistent-v4l.rules
-rw-r--r-- 1 root root    133 2010-04-09 06:13 61-gnome-bluetooth-rfkill.rules
-rw-r--r-- 1 root root    610 2010-04-19 04:30 61-mobile-action.rules
-rw-r--r-- 1 root root   4267 2010-04-19 04:30 61-option-modem-modeswitch.rules
-rw-r--r-- 1 root root    532 2010-04-19 04:30 61-persistent-storage-edd.rules
-rw-r--r-- 1 root root    107 2009-12-03 06:45 64-device-mapper.rules
-rw-r--r-- 1 root root    280 2010-04-23 12:16 64-xorg-xkb.rules
-rw-r--r-- 1 root root    578 2010-04-15 16:17 66-xorg-synaptics.rules
-rw-r--r-- 1 root root    151 2010-04-22 09:48 69-xorg-vmmouse.rules
-rw-r--r-- 1 root root   7687 2010-04-22 15:55 69-xserver-xorg-input-wacom.rules
-rw-r--r-- 1 root root   2565 2010-04-19 04:30 70-acl.rules
-rw-r--r-- 1 root root   1360 2010-04-19 04:30 70-hid2hci.rules
-rw-r--r-- 1 root root    450 2010-04-10 13:30 70-printers.rules
-rw-r--r-- 1 root root    462 2010-04-19 04:30 75-cd-aliases-generator.rules
-rw-r--r-- 1 root root    658 2010-04-19 04:30 75-net-description.rules
-rw-r--r-- 1 root root   3770 2010-04-19 04:30 75-persistent-net-generator.rules
-rw-r--r-- 1 root root    658 2010-04-19 04:30 75-tty-description.rules
-rw-r--r-- 1 root root   1551 2010-02-01 16:17 77-mm-ericsson-mbm.rules
-rw-r--r-- 1 root root   1672 2010-02-01 16:17 77-mm-longcheer-port-types.rules
-rw-r--r-- 1 root root   6247 2010-02-01 16:17 77-mm-zte-port-types.rules
-rw-r--r-- 1 root root    887 2010-04-19 04:30 78-graphics-card.rules
-rw-r--r-- 1 root root   4905 2010-04-19 04:30 78-sound-card.rules
-rw-r--r-- 1 root root    137 2010-04-19 04:30 79-fstab_import.rules
-rw-r--r-- 1 root root     68 2010-03-28 18:02 80-alsa.rules
-rw-r--r-- 1 root root    701 2010-04-19 04:30 80-drivers.rules
-rw-r--r-- 1 root root   9616 2010-04-13 03:12 80-udisks.rules
-rw-r--r-- 1 root root   3460 2010-02-16 20:10 85-brltty.rules
-rw-r--r-- 1 root root    396 2010-04-24 16:17 85-console-setup.rules
-rw-r--r-- 1 root root     84 2010-04-22 14:15 85-hdparm.rules
-rw-r--r-- 1 root root   1855 2010-03-25 03:12 85-hplj10xx.rules
-rw-r--r-- 1 root root    949 2010-03-06 21:49 85-pcmcia.rules
-rw-r--r-- 1 root root    221 2010-02-23 10:01 85-regulatory.rules
-rw-r--r-- 1 root root    619 2010-04-09 03:26 85-usbmuxd.rules
-rw-r--r-- 1 root root     83 2010-04-01 12:54 90-hal.rules
-rw-r--r-- 1 root root   1079 2010-04-09 05:42 90-libgpod.rules
-rw-r--r-- 1 root root   1328 2010-03-26 18:38 90-pulseaudio.rules
-rw-r--r-- 1 root root   1572 2010-04-19 04:30 95-keyboard-force-release.rules
-rw-r--r-- 1 root root   8755 2010-04-19 04:30 95-keymap.rules
-rw-r--r-- 1 root root    155 2010-04-19 04:30 95-udev-late.rules
-rw-r--r-- 1 root root   2866 2010-03-05 04:20 95-upower-battery-recall-dell.rules
-rw-r--r-- 1 root root   1211 2010-03-05 04:20 95-upower-battery-recall-fujitsu.rules
-rw-r--r-- 1 root root   1020 2010-03-05 04:20 95-upower-battery-recall-gateway.rules
-rw-r--r-- 1 root root   1557 2010-03-05 04:20 95-upower-battery-recall-ibm.rules
-rw-r--r-- 1 root root    774 2010-03-05 04:20 95-upower-battery-recall-lenovo.rules
-rw-r--r-- 1 root root   1067 2010-03-05 04:20 95-upower-battery-recall-toshiba.rules
-rw-r--r-- 1 root root   1622 2010-03-05 04:20 95-upower-csr.rules
-rw-r--r-- 1 root root   4048 2010-03-05 04:20 95-upower-hid.rules
-rw-r--r-- 1 root root    354 2010-03-05 04:20 95-upower-wup.rules
-rw-r--r-- 1 root root    182 2010-04-09 05:34 97-bluetooth.rules
-rw-r--r-- 1 root root   1436 2010-04-19 04:30 README

```


I have not done any power settings, also I don't have any other kernels to try

---

### Post by happyhamster on 2010-06-21
That looks fine, only 64-xorg-xkb.rules hasn't been updated yet. Apart from updating the system or adding the usb modules to /etc/modules, I'm out of ideas.

---

### Post by RJ12 on 2010-06-21
> **happyhamster said:**
> That looks fine, only 64-xorg-xkb.rules hasn't been updated yet. Apart from updating the system or adding the usb modules to /etc/modules, I'm out of ideas.

Well, I appreciate the help and time you have given me :) I will just go ahead and mark this as solved

---

