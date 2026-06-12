---
title: "installing driver for wireless internet adapter"
date: 2012-04-12
forum: General Help
---

### Post by stookin on 2012-04-12
Hello Ubuntu

My computer lags a lot while playing online games (eg. Open Arena), and while watching YouTube videos loading sometimes gets stuck.
Also during a speedtest at [www.speedtest.net]("http://www.speedtest.net"), my connection seems to fluctuate.

I think I don't have the correct drivers installed for my sitecom wireless USB adapter.
I'm on a desktop.

How do I install the correct driver on ubuntu?

The command "lsusb" in terminal gave me the below output:

Bus 001 Device 005: ID 0df6:0042 Sitecom Europe B.V. WL-345 Wireless USB adapter 300N X3


Please Help.:popcorn:

---

### Post by PhantomTurtle on 2012-04-12
It could just be because you have a wireless connection. Try a wired connection for a while. There might be something that could be interfering with the wireless signal. If it already works then you don't need to install any more drivers.

---

### Post by gandaran on 2012-04-12
> **stookin said:**
> Hello Ubuntu

My computer lags a lot while playing online games (eg. Open Arena), and while watching YouTube videos loading sometimes gets stuck.
Also during a speedtest at [www.speedtest.net]("http://www.speedtest.net"), my connection seems to fluctuate.

I think I don't have the correct drivers installed for my sitecom wireless USB adapter.
I'm on a desktop.

How do I install the correct driver on ubuntu?

The command "lsusb" in terminal gave me the below output:

Bus 001 Device 005: ID 0df6:0042 Sitecom Europe B.V. WL-345 Wireless USB adapter 300N X3


Please Help.:popcorn:
which ubuntu version do you have?
if I'm not wrong the sitecom adapter has a ralink chipset and if this is correct then you could blacklist the driver used so it will load a another ralink driver/module no need to install anything as ralink drivers are already built in the kernel you just need the correct one that works best with the adapter.
post the output of these commands
```
lsmod
```
```
sudo lshw -C network
```

---

### Post by stookin on 2012-04-13
> **PhantomTurtle said:**
> It could just be because you have a  wireless connection. Try a wired connection for a while. There might be  something that could be interfering with the wireless signal. If it  already works then you don't need to install any more drivers.

I had it with windows as well at first, but then I installed it with the  sitecom CD (Which came with the adapter) and it worked correctly.




> **gandaran said:**
> which ubuntu version do you have?
if I'm not wrong the sitecom adapter has a ralink chipset and if this is correct then you could blacklist the driver used so it will load a another ralink driver/module no need to install anything as ralink drivers are already built in the kernel you just need the correct one that works best with the adapter.
post the output of these commands
```
lsmod
``````
sudo lshw -C network
```

lsmod:

```
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55577  1 vfat
snd_hrtimer            12648  1 
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
dm_crypt               22565  1 
binfmt_misc            17292  1 
arc4                   12473  2 
rt2800usb              22222  0 
rt2800lib              48909  1 rt2800usb
crc_ccitt              12595  1 rt2800lib
rt2x00usb              20092  1 rt2800usb
rt2x00lib              48146  3 rt2800usb,rt2800lib,rt2x00usb
snd_hda_codec_realtek   254163  1 
ip6t_LOG               16846  4 
mac80211              393421  3 rt2800lib,rt2x00usb,rt2x00lib
xt_hl                  12465  6 
snd_hda_intel          24262  4 
ip6t_rt                12473  3 
snd_hda_codec          91859  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
cfg80211              172427  2 rt2x00lib,mac80211
nf_conntrack_ipv6      13581  7 
nf_defrag_ipv6         13139  1 nf_conntrack_ipv6
snd_pcm                80435  3 snd_hda_intel,snd_hda_codec
ipt_REJECT             12512  1 
ipt_LOG                12783  5 
xt_limit               12541  12 
xt_tcpudp              12531  18 
xt_addrtype            12596  4 
snd_seq_midi           13132  0 
xt_state               12514  14 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  3 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  3 snd_hrtimer,snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  17 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73673  0 
serio_raw              12990  0 
ip6table_filter        12711  1 
ip6_tables             22528  3 ip6t_LOG,ip6t_rt,ip6table_filter
nf_conntrack_netbios_ns    12585  0 
nf_conntrack_broadcast    12541  1 nf_conntrack_netbios_ns
nf_nat_ftp             12595  0 
nf_nat                 24958  1 nf_nat_ftp
nf_conntrack_ipv4      19084  9 nf_nat
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
nf_conntrack_ftp       13183  1 nf_nat_ftp
nf_conntrack           70103  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         12706  1 
ip_tables              18106  1 iptable_filter
x_tables               21975  13 ip6t_LOG,xt_hl,ip6t_rt,ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
i2c_viapro             12969  0 
shpchp                 32356  0 
lm63                   13998  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
radeon                929507  2 
firewire_ohci          35854  0 
usb_storage            44173  1 
ttm                    65224  1 radeon
firewire_core          56937  1 firewire_ohci
drm_kms_helper         32889  1 radeon
uas                    17699  0 
crc_itu_t              12627  1 firewire_core
drm                   192194  4 radeon,ttm,drm_kms_helper
via_rhine              27413  0 
i2c_algo_bit           13199  1 radeon
pata_via               13398  2 
sata_via               13534  0 

```sudo lshw -C network
```
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 7c
       serial: 00:19:db:2f:e0:dc
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.0 duplex=half latency=64 link=no maxlatency=8 mingnt=3 multicast=yes port=MII speed=10Mbit/s
       resources: irq:23 ioport:d000(size=256) memory:dfffe000-dfffe0ff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:8
       logical name: wlan0
       serial: 00:0c:f6:8d:d6:72
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=3.0.0-17-generic firmware=0.29 ip=192.168.2.1 link=yes multicast=yes wireless=IEEE 802.11bgn

```Edit: I just checked speedtest.net again, my download speed fluctuates (pretty randomly I believe), however my upload speed is steady.

Edit #2: Ubuntu 11.10 Oneiric Ocelot

---

### Post by stookin on 2012-04-14
Bump for Angelina Jolie's x-rated movies!

---

### Post by stookin on 2012-04-14
How exactly do I blacklist a driver
and how do I know which driver is good for this computer?

---

### Post by stookin on 2012-04-15
can I start a new thread pl0x.. or is that against the rules..?

---

### Post by PhantomTurtle on 2012-04-15
I don't think blacklisting the driver will help. Since you can actually connect to the internet, it is mostly likely a problem with your wireless router or something wrong with your usb adapter. Try it on another computer. See if it makes a difference. Try it on Windows, see if it makes a difference.

---

### Post by gordintoronto on 2012-04-15
> **stookin said:**
> can I start a new thread pl0x.. or is that against the rules..?

Yes, it is.

Have you tried using a different channel? There's a program called inSSIDer which can help you find the cleanest channel. Made a difference for me.

---

### Post by stookin on 2012-04-16
> **PhantomTurtle said:**
> I don't think blacklisting the driver will help. Since you can actually connect to the internet, it is mostly likely a problem with your wireless router or something wrong with your usb adapter. Try it on another computer. See if it makes a difference. Try it on Windows, see if it makes a difference.

In windows it works fine, but only after I installed it with the CD that came with it.

If windows installs it itself it's the same as in ubuntu.

I can show the speedtest graph if you want, to compare connectivity between ubuntu and windows.

in windows it's high and stable, in ubuntu it's lower and with sporadic ups and downs.

---

### Post by PhantomTurtle on 2012-04-16
> **stookin said:**
> In windows it works fine, but only after I installed it with the CD that came with it.

If windows installs it itself it's the same as in ubuntu.

I can show the speedtest graph if you want, to compare connectivity between ubuntu and windows.

in windows it's high and stable, in ubuntu it's lower and with sporadic ups and downs.

Did Linux drivers come with the CD you got? try changing the channel as the comment above yours says. If it actually connects then there is something wrong with your wireless router.

---

### Post by wildmanne39 on 2012-04-16
Hi, you are using the right driver please do and just copy and paste for accuracy:
```
gksudo gedit /etc/modprobe.d/rt2800usb.conf
```

Add a single line:

```
options rt2800usb nohwcrypt=1
```

Proofread carefully, save and close.

Then make your wireless settings look like the screenshots.
Then reboot.
Thanks

---

