---
title: "No Wired Internet Access"
date: 2011-09-09
forum: General Help
---

### Post by z33z49 on 2011-09-09
I recently installed Ubuntu 10.04 64bit alongside windows 7, but I can't connect to the internet via ethernet cable in my apartment. It doesn't show anything in the networks menu except "windows network" which I think is always there. I can connect to the Internet just fine in windows, and not to long ago I connected in Ubuntu through a wireless network.

Is there anything I can try? It would be nice if I didn't have to switch to windows to access the internet.

---

### Post by tehchibipanda on 2011-09-09
Hi there! When you disconnect the WiFi and plug in an ethernet cable, under networks, do you have anything listed? Can you disconnect wifi and connect an ethernet cable and run

```
ifconfig
```and post your results please? To see if its listed as Eth0,1, etc.

---

### Post by z33z49 on 2011-09-09
Thanks for the quick response. I didn't see anything listed under networks on the taskbar. And as I said if I select "Networks" from one of the menus and it just shows one thing called "windows network".

here's the ifconfig:

ifconfig
lo        
Link encap:Local Loopback  
inet addr:127.0.0.1  Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING  MTU:16436  Metric:1
RX packets:20 errors:0 dropped:0 overruns:0 frame:0 
TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0           
RX bytes:1272 (1.2 KB)  TX bytes:1272 (1.2 KB)

Sorry if its lines are weird, I saved it in Ubuntu and accessed it on windows, and the line breaks were messed up.

---

### Post by tehchibipanda on 2011-09-09
That's weird...its not even showing up any networks except local O.o; 

```
lspci -v
```Post the output of that, please. I'm curious to see if its even recognizing your wifi/ethernet cards...

Edit: Doesn't need to be the whole thing you post; Just what says "Broadcom" or "Atheros" etc. Whichever your company card is; It will say wired/wireless controller beside it

---

### Post by fdrake on 2011-09-09
can you also post the results for:

```

less /etc/lsb-release
uname -a |less
lshw -c Network
nm-tool
lsmod
less /etc/modprobe.d/blacklist

```

make sure you devide the results by a line of ############################
to make it easier for us to read. thanks.

---

### Post by z33z49 on 2011-09-09
Here are the results for lspci -v, This seemed to be the relevant selection.


07:00.0 Ethernet controller: Atheros Communications Device 1083 (rev c0)
	Subsystem: Dell Device 0491
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at d9800000 (64-bit, non-prefetchable) [size=256K]
	I/O ports at 4000 [size=128]
	Capabilities: <access denied>


The access denied part looks like a big hint to me.
I'll get back on those other tests soon.

---

### Post by fdrake on 2011-09-09
> **z33z49 said:**
> 
The access denied part looks like a big hint to me.


you need to use sudo to see the full description of the device:
you can try :

```
sudo lspci -vvvs 07:0.0
```

---

### Post by z33z49 on 2011-09-09
On all those other tests I was asked to run, here is what I got.


less /etc/lsb-release:
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.3 LTS"

##################################################################

uname -a |less:
Linux TobyComp 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:13:52 UTC 2011 x86_64 GNU/Linux

###################################################################

lshw -c Network:
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Ethernet controller
       product: Atheros Communications
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:07:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:d9800000-d983ffff ioport:4000(size=128)
  *-network DISABLED
       description: Wireless interface
       product: WiFi Link 1000 Series
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0d:00.0
       logical name: wlan0
       version: 00
       serial: 22:b5:0c:2d:76:63
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:30 memory:d8800000-d8801fff

##########################################################################

nm-tool:

NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlagn
  State:             unavailable
  Default:           no
  HW Address:        74:E5:0B:1A:89:80

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points

############################################################################

lsmod:
Module                  Size  Used by
binfmt_misc             7960  1 
snd_hda_codec_realtek   279008  0 
ppdev                   6375  0 
joydev                 11104  0 
snd_hda_intel          25805  2 
snd_hda_codec          85759  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
arc4                    1473  2 
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iwlagn                123060  0 
iwlcore               125250  1 iwlagn
nouveau               515227  0 
snd                    71283  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
fbcon                  39270  71 
uvcvideo               62851  0 
tileblit                2487  1 fbcon
videodev               40518  1 uvcvideo
psmouse                65040  0 
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    11892  1 videodev
ttm                    61007  1 nouveau
drm_kms_helper         30742  1 nouveau
sdhci_pci               6700  0 
mac80211              238896  2 iwlagn,iwlcore
serio_raw               4918  0 
font                    8053  1 fbcon
cfg80211              148341  3 iwlagn,iwlcore,mac80211
soundcore               8052  1 snd
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
drm                   198886  3 nouveau,ttm,drm_kms_helper
i2c_algo_bit            6024  1 nouveau
sdhci                  17960  1 sdhci_pci
led_class               3764  2 iwlcore,sdhci
xhci                   42519  0 
vga16fb                12757  1 
vgastate                9857  1 vga16fb
video                  20623  0 
output                  2503  1 video
lp                      9336  0 
parport                37160  2 ppdev,lp
usbhid                 41116  0 
hid                    83888  1 usbhid
ahci                   38030  3 

##########################################################################

less /etc/modprobe.d/blacklist
/etc/modprobe.d/blacklist: No such file or directory

##########################################################################

I'll try that sudo command now.

---

### Post by z33z49 on 2011-09-09
Here's the results of that last command.


sudo lspci -vvvs 07:0.0

07:00.0 Ethernet controller: Atheros Communications Device 1083 (rev c0)
	Subsystem: Dell Device 0491
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 10
	Region 0: Memory at d9800000 (64-bit, non-prefetchable) [size=256K]
	Region 2: I/O ports at 4000 [size=128]
	Capabilities: [40] Power Management version 3
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [48] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
		Address: 0000000000000000  Data: 0000
	Capabilities: [58] Express (v1) Endpoint, MSI 00
		DevCap:	MaxPayload 4096 bytes, PhantFunc 0, Latency L0s unlimited, L1 unlimited
			ExtTag- AttnBtn+ AttnInd+ PwrInd+ RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr+ UncorrErr+ FatalErr- UnsuppReq+ AuxPwr+ TransPend-
		LnkCap:	Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 unlimited, L1 unlimited
			ClockPM+ Suprise- LLActRep- BwNot-
		LnkCtl:	ASPM L0s L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM+ AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
	Capabilities: [6c] Vital Product Data <?>
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [180] Device Serial Number 4f-0s-e6-3a-e9-da-45-6f

---

### Post by fdrake on 2011-09-09
It looks like your device does not have any driver assigned to it:
lets see if you kernel has it already:
post here the output
```

sudo su
modprobe atl1c 
echo "1083" > /sys/bus/pci/drivers/atl1c/new_id 
exit
lsmod
less /etc/modprobe.d/blacklist.conf

```

also are you able to connect with wireless. If not check you switcher maybe is off or something.If those commands do not work we need to download some packages online.

---

### Post by z33z49 on 2011-09-10
Oops, I missed that last line, well I'll post my results anyways.
It basically came out like this:

modprobe atl1c 

echo "1083" > /sys/bus/pci/drivers/atl1c/new_id 
bash: echo: write error: Invalid argument

exit

lsmod
Module                  Size  Used by
atl1c                  32975  0 
binfmt_misc             7960  1 
ppdev                   6375  0 
snd_hda_codec_realtek   279008  0 
joydev                 11104  0 
snd_hda_intel          25805  2 
snd_hda_codec          85759  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
arc4                    1473  2 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iwlagn                123060  0 
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               62851  0 
videodev               40518  1 uvcvideo
sdhci_pci               6700  0 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
nouveau               515227  0 
ttm                    61007  1 nouveau
iwlcore               125250  1 iwlagn
drm_kms_helper         30742  1 nouveau
snd                    71283  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              238896  2 iwlagn,iwlcore
sdhci                  17960  1 sdhci_pci
vga16fb                12757  1 
vgastate                9857  1 vga16fb
psmouse                65040  0 
v4l1_compat            15495  2 uvcvideo,videodev
xhci                   42519  0 
serio_raw               4918  0 
v4l2_compat_ioctl32    11892  1 videodev
drm                   198886  3 nouveau,ttm,drm_kms_helper
soundcore               8052  1 snd
i2c_algo_bit            6024  1 nouveau
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
led_class               3764  2 iwlcore,sdhci
cfg80211              148341  3 iwlagn,iwlcore,mac80211
video                  20623  0 
output                  2503  1 video
lp                      9336  0 
parport                37160  2 ppdev,lp
usbhid                 41116  0 
hid                    83888  1 usbhid
ahci                   38030  3 

I doubt that last line was critical to the functionality of the previous ones, and it looks like there was errors, so I probably need to download some stuff as you say. Wireless internet still works, so I'll be able to get on the internet with Ubuntu next time I go somewhere with wifi.

---

### Post by fdrake on 2011-09-10
yes i added that command after sorry. i noticed i mistyped it in my first post.

> **z33z49 said:**
> atl1c 32975 0 
the driver is being loaded. Did you reboot already?
after the reboot can you post the results for
```

ifconfig
lshw -c Network

```
also can you try if the wired connection works?

---

### Post by z33z49 on 2011-09-11
I've been away from my apartment right now and have wifi here, but also a network cable. After turning off wifi and plugging in the cable I got these results:

ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:684 errors:0 dropped:0 overruns:0 frame:0
          TX packets:684 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:52496 (52.4 KB)  TX bytes:52496 (52.4 KB)

wlan0     Link encap:Ethernet  HWaddr 74:e5:0b:1a:89:80  
          inet6 addr: fe80::76e5:bff:fe1a:8980/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1481 errors:0 dropped:0 overruns:0 frame:0
          TX packets:889 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:940376 (940.3 KB)  TX bytes:143343 (143.3 KB)

lshw -c Network

WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Ethernet controller
       product: Atheros Communications
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:07:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:d9800000-d983ffff ioport:4000(size=128)
  *-network
       description: Wireless interface
       product: WiFi Link 1000 Series
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0d:00.0
       logical name: wlan0
       version: 00
       serial: 22:b5:0c:2d:76:63
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:30 memory:d8800000-d8801fff

I hope the different connection location doesn't change anything.

---

### Post by fdrake on 2011-09-12
still Unclaimed hm,,,
can you run some updates for me:
```

sudo modprobe -r atl1c
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-2.6-amd64 linux-headers-generic
sudo apt-get install --reinstall linux-backports-modules-wireless-$(less /etc/lsb-release | grep "DISTRIB_CODENAME=" | cut -d "=" -f 2)-$(uname -r | cut -d "-" -f 3)
sudo apt-get update && sudo apt-get upgrade
sudo modprobe atl1c
<and reboot>

```
if you have still no luck. do :
```

sudo modprobe -r atl1c
sudo modprobe atl1e
<and reboot>
```
if you still cannot connect please post output for
```
lshw -c network 
dmesg | egrep 'atl1|Ethernet'
```

---

