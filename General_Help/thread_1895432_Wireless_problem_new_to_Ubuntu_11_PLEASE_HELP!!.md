---
title: "Wireless problem new to Ubuntu 11 PLEASE HELP!!"
date: 2011-12-14
forum: General Help
---

### Post by alfonzo97 on 2011-12-14
Alright. so i have had Ubuntu now for a couple years, and never had any problems. i have had the same computer, and it wasn't until the latest update this problem occurred. whats happening is my wireless only connects about 4 out of 10 times. sometimes it connects every time for a few days, then it again goes to being derpy. this happens with two networks, so its not my internet. it never happened before the stupid update which i hate in every way, espesially the side bar thing, anyway, it just keeps doing the connecting thing, where the icon goes up and down. it seems to only happen if i leave my computer on when i leave the network (ie when i go to school, if i close the lid while connected to my home network, it tends not to connect at school until i hard restart. and vise versa.) and please dont tell me to just restart it every time it does it. i want a fix to the problem. and also dont say drivers. if it were the drivers it would probably not work at all. i also tried a usb wireless card. thats how im typing this right now. and sometime neither of them work! this is frustrating the hell out of me! please if you have anything that might help, that would be great. thanks

---

### Post by josephmills on 2011-12-14
Hello there could you please open your terminal and enter
```
lspci -nn && lsmod && rfkill list all 
``` and paste here thanks 
Joseph

---

### Post by alfonzo97 on 2011-12-14
here ya go
```
00:00.0 Host bridge [0600]: nVidia Corporation MCP79 Host Bridge [10de:0a82] (rev b1)
00:00.1 RAM memory [0500]: nVidia Corporation MCP79 Memory Controller [10de:0a88] (rev b1)
00:03.0 ISA bridge [0601]: nVidia Corporation MCP79 LPC Bridge [10de:0aae] (rev b3)
00:03.1 RAM memory [0500]: nVidia Corporation MCP79 Memory Controller [10de:0aa4] (rev b1)
00:03.2 SMBus [0c05]: nVidia Corporation MCP79 SMBus [10de:0aa2] (rev b1)
00:03.3 RAM memory [0500]: nVidia Corporation MCP79 Memory Controller [10de:0a89] (rev b1)
00:03.5 Co-processor [0b40]: nVidia Corporation MCP79 Co-processor [10de:0aa3] (rev b1)
00:04.0 USB Controller [0c03]: nVidia Corporation MCP79 OHCI USB 1.1 Controller [10de:0aa5] (rev b1)
00:04.1 USB Controller [0c03]: nVidia Corporation MCP79 EHCI USB 2.0 Controller [10de:0aa6] (rev b1)
00:06.0 USB Controller [0c03]: nVidia Corporation MCP79 OHCI USB 1.1 Controller [10de:0aa7] (rev b1)
00:06.1 USB Controller [0c03]: nVidia Corporation MCP79 EHCI USB 2.0 Controller [10de:0aa9] (rev b1)
00:08.0 Audio device [0403]: nVidia Corporation MCP79 High Definition Audio [10de:0ac0] (rev b1)
00:09.0 PCI bridge [0604]: nVidia Corporation MCP79 PCI Bridge [10de:0aab] (rev b1)
00:0b.0 IDE interface [0101]: nVidia Corporation MCP79 SATA Controller [10de:0ab5] (rev b1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP79 PCI Express Bridge [10de:0aa0] (rev b1)
00:16.0 PCI bridge [0604]: nVidia Corporation MCP79 PCI Express Bridge [10de:0ac7] (rev b1)
00:18.0 PCI bridge [0604]: nVidia Corporation MCP79 PCI Express Bridge [10de:0ac7] (rev b1)
05:00.0 VGA compatible controller [0300]: nVidia Corporation ION VGA [GeForce 9400M] [10de:0876] (rev b1)
07:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller [10ec:8171] (rev 10)
09:00.0 Ethernet controller [0200]: Atheros Communications AR8132 Fast Ethernet [1969:1062] (rev c0)
Module                  Size  Used by
rt2800usb              22300  0 
rt2800lib              48717  1 rt2800usb
crc_ccitt              12595  1 rt2800lib
rt2x00usb              20092  1 rt2800usb
rt2x00lib              48114  3 rt2800usb,rt2800lib,rt2x00usb
usbhid                 41905  0 
hid                    77367  1 usbhid
webcamstudio           13807  0 
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55577  1 vfat
bnep                   17923  2 
rfcomm                 38408  12 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             13328  0 
vboxnetflt             27211  0 
vboxdrv               251814  3 vboxpci,vboxnetadp,vboxnetflt
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13489  1 
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_realtek   254125  1 
arc4                   12473  4 
nvidia              10390874  42 
snd_hda_intel          28358  1 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
btusb                  18160  2 
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
binfmt_misc            17292  1 
joydev                 17393  0 
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
bluetooth             148839  23 bnep,rfcomm,btusb
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
rtl8192se              94139  0 
uvcvideo               67271  0 
videodev               85626  2 webcamstudio,uvcvideo
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
video                  18908  0 
eeepc_wmi              12722  0 
asus_wmi               19333  1 eeepc_wmi
rtlwifi                95614  1 rtl8192se
mac80211              272785  5 rt2800lib,rt2x00usb,rt2x00lib,rtl8192se,rtlwifi
snd                    55902  13 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sparse_keymap          13658  1 asus_wmi
psmouse                63474  0 
wmi                    18744  1 asus_wmi
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
cfg80211              172392  3 rt2x00lib,rtlwifi,mac80211
serio_raw              12990  0 
shpchp                 32356  0 
i2c_nforce2            12906  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usb_storage            44173  1 
uas                    17699  0 
atl1c                  36638  0 
ahci                   21634  2 
libahci                25761  1 ahci
0: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: asus-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
6: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
7: phy2: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

---

### Post by waltsullivan on 2011-12-14
When you close the lid (to go to/from school/home), the Power Manager is invoked, to prepare the system for entering the Suspend state.  Ditto when you open the lid. Part of preparing to Suspend is shutting down and starting the wireless. For your 
Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller [10ec:8171] (rev 10)

[FONT=Verdana]it seems to be not working. Look at `/var/log/pm*.log`, and the scripts in `/usr/lib/pm-utils/...`. 

You could write your own script to handle shutdown/reinitialize for your own wireless card, make it executable, put in in `/etc/pm/sleep.d/`, and you're golden.

`man pm-action` and `dpkg -L pm-utils` are of interest.
[/FONT]

---

### Post by jimmydean886-2 on 2011-12-14
Have you tried using WiCD to connect? Install it from the software center and give it a shot. Sometimes I have problems with GNOME-NM, which is the default and what WiCD replaces. Hope this helps!

---

### Post by josephmills on 2011-12-14
> **alfonzo97 said:**
> here ya go
```
00:00.0 Host bridge [0600]: nVidia Corporation MCP79 Host Bridge [10de:0a82] (rev b1)
00:00.1 RAM memory [0500]: nVidia Corporation MCP79 Memory Controller [10de:0a88] (rev b1)
00:03.0 ISA bridge [0601]: nVidia Corporation MCP79 LPC Bridge [10de:0aae] (rev b3)
00:03.1 RAM memory [0500]: nVidia Corporation MCP79 Memory Controller [10de:0aa4] (rev b1)
00:03.2 SMBus [0c05]: nVidia Corporation MCP79 SMBus [10de:0aa2] (rev b1)
00:03.3 RAM memory [0500]: nVidia Corporation MCP79 Memory Controller [10de:0a89] (rev b1)
00:03.5 Co-processor [0b40]: nVidia Corporation MCP79 Co-processor [10de:0aa3] (rev b1)
00:04.0 USB Controller [0c03]: nVidia Corporation MCP79 OHCI USB 1.1 Controller [10de:0aa5] (rev b1)
00:04.1 USB Controller [0c03]: nVidia Corporation MCP79 EHCI USB 2.0 Controller [10de:0aa6] (rev b1)
00:06.0 USB Controller [0c03]: nVidia Corporation MCP79 OHCI USB 1.1 Controller [10de:0aa7] (rev b1)
00:06.1 USB Controller [0c03]: nVidia Corporation MCP79 EHCI USB 2.0 Controller [10de:0aa9] (rev b1)
00:08.0 Audio device [0403]: nVidia Corporation MCP79 High Definition Audio [10de:0ac0] (rev b1)
00:09.0 PCI bridge [0604]: nVidia Corporation MCP79 PCI Bridge [10de:0aab] (rev b1)
00:0b.0 IDE interface [0101]: nVidia Corporation MCP79 SATA Controller [10de:0ab5] (rev b1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP79 PCI Express Bridge [10de:0aa0] (rev b1)
00:16.0 PCI bridge [0604]: nVidia Corporation MCP79 PCI Express Bridge [10de:0ac7] (rev b1)
00:18.0 PCI bridge [0604]: nVidia Corporation MCP79 PCI Express Bridge [10de:0ac7] (rev b1)
05:00.0 VGA compatible controller [0300]: nVidia Corporation ION VGA [GeForce 9400M] [10de:0876] (rev b1)
07:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller [10ec:8171] (rev 10)
09:00.0 Ethernet controller [0200]: Atheros Communications AR8132 Fast Ethernet [1969:1062] (rev c0)
Module                  Size  Used by
rt2800usb              22300  0 
rt2800lib              48717  1 rt2800usb
crc_ccitt              12595  1 rt2800lib
rt2x00usb              20092  1 rt2800usb
rt2x00lib              48114  3 rt2800usb,rt2800lib,rt2x00usb
usbhid                 41905  0 
hid                    77367  1 usbhid
webcamstudio           13807  0 
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55577  1 vfat
bnep                   17923  2 
rfcomm                 38408  12 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             13328  0 
vboxnetflt             27211  0 
vboxdrv               251814  3 vboxpci,vboxnetadp,vboxnetflt
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13489  1 
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_realtek   254125  1 
arc4                   12473  4 
nvidia              10390874  42 
snd_hda_intel          28358  1 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
btusb                  18160  2 
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
binfmt_misc            17292  1 
joydev                 17393  0 
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
bluetooth             148839  23 bnep,rfcomm,btusb
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
rtl8192se              94139  0 
uvcvideo               67271  0 
videodev               85626  2 webcamstudio,uvcvideo
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
video                  18908  0 
eeepc_wmi              12722  0 
asus_wmi               19333  1 eeepc_wmi
rtlwifi                95614  1 rtl8192se
mac80211              272785  5 rt2800lib,rt2x00usb,rt2x00lib,rtl8192se,rtlwifi
snd                    55902  13 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sparse_keymap          13658  1 asus_wmi
psmouse                63474  0 
wmi                    18744  1 asus_wmi
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
cfg80211              172392  3 rt2x00lib,rtlwifi,mac80211
serio_raw              12990  0 
shpchp                 32356  0 
i2c_nforce2            12906  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usb_storage            44173  1 
uas                    17699  0 
atl1c                  36638  0 
ahci                   21634  2 
libahci                25761  1 ahci
0: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: asus-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
6: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
7: phy2: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```
07:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller [10ec:8171] (rev 10

Needs driver 
rtl8192se_pci


Please open up terminal and enter 
```
uname -a 
``` and paste here thanks

---

### Post by alfonzo97 on 2011-12-16
```
Linux My-PC 3.0.0-12-generic-pae #20-Ubuntu SMP Fri Oct 7 16:37:17 UTC 2011 i686 i686 i386 GNU/Linux
```

---

### Post by alfonzo97 on 2011-12-16
I tried the WiCD thing and it didnt work. thanks anyway tho

---

