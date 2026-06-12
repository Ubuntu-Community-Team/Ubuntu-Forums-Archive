---
title: "The wireless never worked since I install linux Broadcom Corp. Device 4727"
date: 2011-03-22
forum: General Help
---

### Post by heckleberry on 2011-03-22
Hello everybody,

I just bought a new computer (hp 425) without OS and I installed linux 10.4 on it.
Everything works exept the wireless.
I spent 3 full days trying to fix my problem with no result, thats why I m asking you for help.
I m new on Ubuntu, but I really want to learn using it, like that, one day I could also help people of the community.(Im not english sorry for the writting).

I send you the return of some commands who can help you(to help me) :

lspci + lsmod

```
heckleberry@heckleberry-laptop:~$ lspci|grep Network
06:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)

heckleberry@heckleberry-laptop:~$ lsmod
...
lib80211_crypt_tkip     7596  0 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54180  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
fglrx                2092908  31 
agpgart                31724  1 fglrx
video                  17375  0 
output                  1871  1 video
uvcvideo               57310  0 
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
ndiswrapper           184677  0 
vga16fb                11385  1 
vgastate                8961  1 vga16fb
psmouse                63245  0 
serio_raw               3978  0 
soundcore               6620  1 snd
i2c_piix4               8335  0 
wl                   1959598  0 
lib80211                5046  2 lib80211_crypt_tkip,wl
```iwconfig

```
heckleberry@heckleberry-laptop:~$ sudo iwconfig
[sudo] password for heckleberry: 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:8 Mb/s   Tx-Power:off   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```cat  /etc/network/interfaces + sudo lshw -C network

```
heckleberry@heckleberry-laptop:~$ sudo cat  /etc/network/interfaces
auto loniface lo inet loopbackn
iface lo inet loopback


heckleberry@heckleberry-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 64:31:50:73:5e:f6
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.102 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:27 ioport:3000(size=256) memory:90010000-90010fff(prefetchable) memory:90000000-9000ffff(prefetchable) memory:90020000-9003ffff(prefetchable)
  *-network
       description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth1
       version: 01
       serial: e0:2a:82:48:21:49
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:92100000-92103fff

```Tell me If you need more Codes, I try to understand but Im beginner for using the Terminal and Im lost.
I follow so many post and none could help me.
sorry again for my english and thank you for what you doing.

Michel.

---

### Post by heckleberry on 2011-03-23
Hello everybody,

my internet works, I dont know why, but it works.
Its very slow but that an other problem.
Thank you again.

---

