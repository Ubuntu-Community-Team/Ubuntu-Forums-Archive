---
title: "WiFi not working on Compaq Presario C500"
date: 2012-04-06
forum: General Help
---

### Post by Chakyl on 2012-04-06
I'm extremely new to Linux and my WiFi button wont work on my Compaq Presario C500 laptop. Is there any solution?

---

### Post by wildmanne39 on 2012-04-06
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

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

### Post by Chakyl on 2012-04-07
```
chakyl@chakyl-Presario-C500-GF572UA-ABA:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux chakyl-Presario-C500-GF572UA-ABA 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux
chakyl@chakyl-Presario-C500-GF572UA-ABA:~$ lspci -nnk | grep -iA2 net
06:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
	Subsystem: Hewlett-Packard Company BCM4311 802.11b/g Wireless LAN Controller [103c:1363]
	Kernel driver in use: b43-pci-bridge
--
08:08.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
	Subsystem: Hewlett-Packard Company Device [103c:30a5]
	Kernel driver in use: 8139too
chakyl@chakyl-Presario-C500-GF572UA-ABA:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
chakyl@chakyl-Presario-C500-GF572UA-ABA:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
chakyl@chakyl-Presario-C500-GF572UA-ABA:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
chakyl@chakyl-Presario-C500-GF572UA-ABA:~$ lsmod
Module                  Size  Used by
xt_limit               12541  8 
xt_tcpudp              12531  10 
ipt_LOG                12783  8 
ipt_MASQUERADE         12663  0 
xt_DSCP                12549  0 
ipt_REJECT             12512  1 
nf_conntrack_irc       13138  0 
nf_conntrack_ftp       13183  0 
xt_state               12514  6 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
joydev                 17393  0 
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_conexant    52418  1 
binfmt_misc            17292  1 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
arc4                   12473  2 
iptable_nat            13016  0 
nf_nat                 24958  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19084  9 iptable_nat,nf_nat
nf_conntrack           70103  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
iptable_mangle         12646  0 
iptable_filter         12706  1 
ip_tables              18106  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               21975  11 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,iptable_mangle,iptable_filter,ip_tables
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
b43                   318816  0 
i915                  505108  3 
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
drm_kms_helper         32889  1 i915
drm                   192226  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              272785  1 b43
psmouse                73673  0 
snd                    55902  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              12990  0 
cfg80211              172392  2 b43,mac80211
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
wmi                    18744  1 hp_wmi
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
ahci                   21634  2 
libahci                25727  1 ahci
8139too                23283  0 
8139cp                 22636  0 
ssb                    50682  1 b43
chakyl@chakyl-Presario-C500-GF572UA-ABA:~$ 

```

---

### Post by wildmanne39 on 2012-04-07
Hi, try this please:
```
sudo apt-get install --reinstall b43-fwcutter firmware-b43-installer
```
```
sudo modprobe b43
```
```
rfkill unblock all
```
Thanks

---

### Post by Chakyl on 2012-04-07
thanks man!

---

### Post by wildmanne39 on 2012-04-07
Hi, your welcome! please use thread tools at the top of the page to mark the thread solved.
Thanks

---

### Post by nimrodwebdesign on 2012-09-22
This works for me to, except that I have to do it every time I reboot. Is there a way to make it stick?

Thanks.

---

### Post by MugOfUbuntu on 2012-09-23
Thanks a lot man, this helped me c:

---

### Post by amarilis777 on 2012-10-10
I'm new in this forum and i have the same problem, my wireless don't work, i can do something to resolve that? Thanks

---

