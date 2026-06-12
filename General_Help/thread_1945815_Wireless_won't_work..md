---
title: "Wireless won't work."
date: 2012-03-23
forum: General Help
---

### Post by Zoaruki on 2012-03-23
Hi people,
I'm posting here because I've been trying to get connected to my network from my laptop for over 2 hours, without positive results. I've followed [this tutorial]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") step by step and everything went good until 3.5. When I introduce:
```
sudo depmod -a
```I get that something went wrong with the bus (I don't paste the error here because I'm using the OS in a different language and I don't know if my translation is the same as the original output. Anyway I think it's understandable).
And I don't know if it's important, but before, when I introduced:
```
ndiswrapper -l
```It told me that the driver is installed, but I got this warning:
```
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
```I also executed this command (as root):
```
tail /var/log/messages
```And I got:
```
Mar 23 15:00:56 zoaruki-laptop kernel: [ 2390.076925] sd 0:0:0:0: [sda] Unhandled sense code
Mar 23 15:00:56 zoaruki-laptop kernel: [ 2390.076934] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 23 15:00:56 zoaruki-laptop kernel: [ 2390.076946] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Mar 23 15:00:56 zoaruki-laptop kernel: [ 2390.076962] Descriptor sense data with sense descriptors (in hex):
Mar 23 15:00:56 zoaruki-laptop kernel: [ 2390.076969]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Mar 23 15:00:56 zoaruki-laptop kernel: [ 2390.077002]         04 05 5d d8 
Mar 23 15:00:56 zoaruki-laptop kernel: [ 2390.077015] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Mar 23 15:00:56 zoaruki-laptop kernel: [ 2390.077032] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 04 05 5d d8 00 00 08 00
Mar 23 15:00:56 zoaruki-laptop kernel: [ 2390.077125] ata1: EH complete
Mar 23 15:08:50 zoaruki-laptop kernel: [ 2864.072172] usb 2-2: USB disconnect, address 5
```Extra data (unrelated to Ubuntu):

The netbook model is HP Mini 210-1070NR. I tried with two drivers with the same results: bcmwl6 (Win7) and bcmwl5 (WinXP).
And I don't know if this has something to do with anything, but: the original operative system of the computer was Windows 7. When I tried to change it to Windows XP (using an external CD/DVD drive) the installation told me that it couldn't detect a hard disk. Instead of trying to reinstall the original OS (because I thought it would be the same) I tried with Ubuntu 10.04 and everything went good.

This is all I know. I hope you can help me :)

---

### Post by wildmanne39 on 2012-03-23
Hi, I doubt you need ndiswrapper please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by Zoaruki on 2012-03-23
Sure, here you are:
```
zoaruki@zoaruki-laptop:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.4 LTS"
Linux zoaruki-laptop 2.6.32-38-generic #83-Ubuntu SMP Wed Jan 4 11:13:04 UTC 2012 i686 GNU/Linux
zoaruki@zoaruki-laptop:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Kernel driver in use: r8169
    Kernel modules: r8169
02:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4357] (rev 01)
zoaruki@zoaruki-laptop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 192f:0416 Avago Technologies, Pte. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0408:0ff1 Quanta Computer, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
zoaruki@zoaruki-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

zoaruki@zoaruki-laptop:~$ rfkill list all
zoaruki@zoaruki-laptop:~$ lsmod
Module                  Size  Used by
usbhid                 36110  0 
hid                    67288  1 usbhid
binfmt_misc             6587  1 
ppdev                   5259  0 
joydev                  8740  0 
snd_hda_codec_idt      52042  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i915                  289715  3 
snd                    54244  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               57438  0 
drm_kms_helper         29329  1 i915
videodev               34425  1 uvcvideo
drm                   163747  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
intel_agp              24375  2 i915
soundcore               6620  1 snd
v4l1_compat            13251  2 uvcvideo,videodev
psmouse                63677  0 
serio_raw               3978  0 
ndiswrapper           184677  0 
video                  17375  1 i915
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
output                  1871  1 video
agpgart                31724  2 drm,intel_agp
lp                      7028  0 
parport                32635  2 ppdev,lp
ahci                   32680  2 
r8169                  34140  0 
mii                     4381  1 r8169
```

---

### Post by wildmanne39 on 2012-03-23
Hi, your card is so new that you do need ndiswrapper unless you installed the newest kernel 3.1 then it has the driver for your card but neither one of these options is my speciality but I will try to help with ndiswrapper if you want me too.
Thanks

---

### Post by Zoaruki on 2012-03-23
Are you suggesting me to install 11.10?

---

### Post by wildmanne39 on 2012-03-23
Hi, no even with 11.10 it would require an update to the 3.1 kernel because 11.10 only comes with the 3.0.

---

### Post by wildmanne39 on 2012-03-23
Hi, I am getting the directions to upgrade your kernel it is going to take a little while to get it all written up.
Thanks

---

### Post by wildmanne39 on 2012-03-23
Hi, download the following packages.

> 
linux-headers_all.deb
linux-headers-generic_i386.deb
linux-image-generic_i386.deb

from here to your downloads file:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2-precise/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2-precise/)

Open synaptic and install module-init-tools then open a terminal and do:
```
cd ~/Downloads/
```
run these commands in this order:
```
sudo dpkg -i linux-headers-3.2.0-030200_3.2.0-030200.201201042035_all.deb
```
```
sudo dpkg -i linux-headers-3.2.0-030200-generic_3.2.0-030200.201201042035_i386.deb
```
```
sudo dpkg -i linux-image-3.2.0-030200-generic_3.2.0-030200.201201042035_i386.deb
```
watch for errors.

Then run this command to see if the kernel is upgraded:
```
uname -r
```
if so then reboot.
Thanks

---

### Post by Zoaruki on 2012-03-23
Thank you for your time.
Before I rebooted the shell told me that the version was 2.6, but after rebooting it told me that now is 3.2. And now what do I need to do?

EDIT: I forgot to say that when I start the system I get an error that says "READ FPDMA QUEUED"

---

### Post by wildmanne39 on 2012-03-23
Hi, that is great install all updates if there are any then reboot and run this command please:
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
watch for errors then run:
```
sudo modprobe b43
```
and it should work unless we have to remove ndiswrapper but I think it will be ok in your case.
Thanks

---

