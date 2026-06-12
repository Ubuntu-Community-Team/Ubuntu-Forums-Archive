---
title: "USB 3.0 PCI card help"
date: 2011-08-13
forum: General Help
---

### Post by vanquishedangel on 2011-08-13
Hi and thank you for reading my post.

My issue is I bought a usb3.0 pci card that uses a fresco chip and I plugged it in but ubuntu does not see it (Lubuntu). The led is on that the card has. I tried adding pci=nomsi to grub but it seems to have had no effect. here is the output from lsusb

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 04e8:663e Samsung Electronics Co., Ltd D900e Phone
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 058f:6331 Alcor Micro Corp. SD/MMC/MS Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

uname -a
Linux shawn-HP-Compaq-dc7100-SFF-PC923A 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:07:17 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

dmesg | tail; lsusb; echo; sudo fdisk -l

[   84.930773] sd 4:0:0:0: [sdc] Mode Sense: 03 00 00 00
[   84.930777] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[   84.933263] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[   84.936631]  sdc: sdc1
[   84.938512] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[   84.938519] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[   94.040061] usb 4-1: USB disconnect, address 2
[  181.990030] usb 4-1: new full speed USB device using uhci_hcd and address 3
[  182.206900] cdc_acm 4-1:3.1: ttyACM0: USB ACM device
[  458.396780] exe (12417): /proc/12417/oom_adj is deprecated, please use /proc/12417/oom_score_adj instead.
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 04e8:663e Samsung Electronics Co., Ltd D900e Phone
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 058f:6331 Alcor Micro Corp. SD/MMC/MS Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006fbcd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9322    74873856   83  Linux
/dev/sda2            9322        9730     3274753    5  Extended
/dev/sda5            9322        9730     3274752   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00061fc6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4863    39062016   83  Linux

Disk /dev/sdc: 1017 MB, 1017643008 bytes
32 heads, 61 sectors/track, 1018 cylinders
Units = cylinders of 1952 * 512 = 999424 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000097af

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        1018      993537+  82  Linux swap / Solaris

I have a swap disk that plugs in by usb as you can see and I tether my phone for internet atm. nothing is plugged into the 3.0 usb port.  On another note my usb ports on the desktop are 2.0 not 1.1 like it says.

I have an hp dc7100sff 3.8 ht ghz sl8py processor,4 gigs high density ram, ati radeon hd 4350 512 mb vram, nec dvdrw/cdrw 240 watt psu.

The usb3.0 card uses a fresco chip set. a link to one exactly like it is here:

[http://www.aliexpress.com/fm-store/706012/210921283-428810680/PP3U-PCI-to-USB3-0-Host-Adapter-.html](http://www.aliexpress.com/fm-store/706012/210921283-428810680/PP3U-PCI-to-USB3-0-Host-Adapter-.html)

Link to my computer specs are here:

[http://h18000.www1.hp.com/products/quickspecs/11948_div/11948_div.HTML](http://h18000.www1.hp.com/products/quickspecs/11948_div/11948_div.HTML)

Please if you can post links if needed, I have used linux for years and several types but I am still kinda newb.

---

### Post by JC Cheloven on 2011-08-16
Support for usb 3.0 is supposed to be included in the linux kernel since the times of Karmic Koala. 

I don't have any usb 3.0 port myself, so talking by memory, but I believe the related kernel module is named XHCI (or xhci). Please run ```
lsmod
``` to see if the module is loaded. If not, you should be able to load the module with something as ```
sudo modprobe xhci
``` and eventually to make it permanent adding it to the file /etc/modules.

Again, talking by memory here, use my indications with caution. Thank you.

---

### Post by Manyette on 2011-08-16
USB 3.0 requires harware capable of supporting it.  On my Acer the USB 3.0 socket is coded in blue to differentiate it from 2.0

---

### Post by vanquishedangel on 2011-08-17
out put of lsmod:


ppp_deflate            12990  0 
bsd_comp               12913  0 
ppp_async              17540  1 
crc_ccitt              12667  1 ppp_async
binfmt_misc            17565  1 
dm_crypt               22993  0 
vesafb                 13761  1 
snd_hda_codec_hdmi     28167  1 
snd_hda_intel          33211  0 
snd_intel8x0           38272  1 
snd_hda_codec         103804  2 snd_hda_codec_hdmi,snd_hda_intel
snd_ac97_codec        134270  1 snd_intel8x0
ac97_bus               12730  1 snd_ac97_codec
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96391  5 snd_hda_codec_hdmi,snd_hda_intel,snd_intel8x0,snd_ac97_codec,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
ppdev                  17113  0 
microcode              22702  0 
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
fglrx                2739144  76 
psmouse                73535  0 
snd                    67382  13 snd_hda_codec_hdmi,snd_hda_intel,snd_intel8x0,snd_ac97_codec,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cdc_acm                22574  3 
serio_raw              13166  0 
parport_pc             36959  1 
soundcore              12680  1 snd
snd_page_alloc         18529  3 snd_hda_intel,snd_intel8x0,snd_pcm
lp                     17825  0 
parport                46458  3 ppdev,parport_pc,lp
dm_raid45              77827  0 
xor                    12890  1 dm_raid45
btrfs                 550457  0 
zlib_deflate           27074  2 ppp_deflate,btrfs
libcrc32c              12644  1 btrfs
floppy                 74120  0 
pata_sil680            13246  2 
tg3                   141750  0 


out put of sudo modprobe xhci:
WARNING: All config files need .conf: /etc/modprobe.d/bad_list, it will be ignored in a future release.
FATAL: Module xhci not found.

I really am not sure what this means? is it blocked?

---

### Post by JC Cheloven on 2011-08-17
Sorry, I googled a little to find out that the name of the driver actually is xhci_hcd (as said I'm from memory, and with no usb3.0 port at hand). So please run ```
sudo modprobe xhci_hcd
```
The module should be loaded (please see with "lsmod" as previously), and tell us if that worked. Thank you.

---

### Post by vanquishedangel on 2011-08-18
shawn@shawn-HP-Compaq-dc7100-SFF-PC923A:~$ sudo modprobe xhci_hcd
[sudo] password for shawn: 
WARNING: All config files need .conf: /etc/modprobe.d/bad_list, it will be ignored in a future release.
shawn@shawn-HP-Compaq-dc7100-SFF-PC923A:~$

same result, and ty for helping it is appreciated.

---

### Post by vanquishedangel on 2011-08-18
OK figured it out

I searched the error "WARNING: All config files need .conf: /etc/modprobe.d/bad_list, it will be ignored in a future release." and I found this thread: 

[http://ubuntuforums.org/archive/index.php/t-1186010.html](http://ubuntuforums.org/archive/index.php/t-1186010.html)

and got the idea to modify the command to fit my error, the command they gave was:

sudo cat /etc/modprobe.d/blacklist >> /etc/modprobe.d/blacklist.conf && sudo rm /etc/modprobe.d/blacklist

The command i used is:

sudo cat /etc/modprobe.d/bad_list >> /etc/modprobe.d/bad_list.conf && sudo rm /etc/modprobe.d/bad_list

and then I used this command:

sudo modprobe xhci_hcd

and with lsmod i get:


Module                  Size  Used by
xhci_hcd               77643  0 
ppp_deflate            12990  0 
bsd_comp               12913  0 
ppp_async              17540  1 
crc_ccitt              12667  1 ppp_async
binfmt_misc            17565  1 
dm_crypt               22993  0 
vesafb                 13761  1 
snd_hda_codec_hdmi     28167  1 
snd_hda_intel          33211  0 
ppdev                  17113  0 
microcode              22702  0 
cdc_acm                22574  3 
snd_hda_codec         103804  2 snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_intel8x0           38272  1 
psmouse                73535  0 
snd_ac97_codec        134270  1 snd_intel8x0
ac97_bus               12730  1 snd_ac97_codec
snd_pcm                96391  5 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_intel8x0,snd_ac97_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
serio_raw              13166  0 
parport_pc             36959  1 
fglrx                2786212  71 
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    67382  13 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  3 snd_hda_intel,snd_intel8x0,snd_pcm
lp                     17825  0 
parport                46458  3 ppdev,parport_pc,lp
dm_raid45              77827  0 
xor                    12890  1 dm_raid45
btrfs                 550457  0 
zlib_deflate           27074  2 ppp_deflate,btrfs
libcrc32c              12644  1 btrfs
floppy                 74120  0 
tg3                   141750  0 
pata_sil680            13246  2 


as you can see it is first on the list

Thank you for your help guys, I wouldn't have found the answer without your replies, also I don't belive this should hurt anyones system so if I am wrong please post.

---

### Post by vanquishedangel on 2011-08-19
ok so the module is loaded but no dice, nothing from the pci card, I wonder if it requires pci 2.0? or 2.1?

---

### Post by vanquishedangel on 2011-08-25
ok this is now working mostly lol and yes I kinda feel stupid

step 1. remove protective film from the pci card before plugging it in ( this is what was wrong lol)

step 2. add pci=nomsi to grub in /etc/default

step 3. run in a terminal sudo update-grub


it now reads my camera sd card and will recharge my phone however i still cannot connect to the apn on my phone through this port.

---

### Post by JC Cheloven on 2011-08-26
> **vanquishedangel said:**
> 
step 1. remove protective film from the pci card before plugging it in ( this is what was wrong lol)
:lolflag: Glad it was all about a tiny detail after all (I was out of ideas :) ).
Enjoy your new card!

---

### Post by ArtInvent on 2011-12-19
Remove plastic film. This is the funniest thing I have read in ages. Thank you all posters.

---

