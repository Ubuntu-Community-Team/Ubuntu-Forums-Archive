---
title: "problem with internet"
date: 2012-03-01
forum: General Help
---

### Post by asamay81 on 2012-03-01
hi all
i have recently upgraded my PC to this configuration

intel core i3-2100 3.1 GHz processor
intel DH67GD motherboard
GSkill NT DDR3 4 GB RAM

my system is installed with two OS viz. ubuntu 10.04 LTS and MS WinXP SP 3

before the up-gradation i was in Pentium 4

the problem is after i upgraded my system, the network devise has been deactivated in ubuntu although it is working fine in windows. at present there is no active network devise. i do not understand why this problem has happened and need your kind help.

thanks in advance

~asamay~

---

### Post by MG&amp;TL on 2012-03-01
What network device?

Can you post the output of:

```
lspci
``` from the terminal.

---

### Post by Lokireloaded on 2012-03-01
Scratch that. Just noticed the other message

---

### Post by asamay81 on 2012-03-02
thanks for your reply....

here is the lspci output

> 00:00.0 Host bridge: Intel Corporation Device 0100 (rev 09)
    00:02.0 VGA compatible controller: Intel Corporation Sandy Bridge Integrated Graphics Controller (rev 09)
    00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)
    00:19.0 Ethernet controller: Intel Corporation Device 1503 (rev 05)
    00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 05)
    00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 05)
    00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b5)
    00:1c.3 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 4 (rev b5)
    00:1c.4 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 5 (rev b5)
    00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 05)
    00:1f.0 ISA bridge: Intel Corporation Device 1c4a (rev 05)
    00:1f.2 IDE interface: Intel Corporation Cougar Point 4 port SATA IDE Controller (rev 05)
    00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 05)
    00:1f.5 IDE interface: Intel Corporation Cougar Point 2 port SATA IDE Controller (rev 05)
    01:00.0 PCI bridge: Integrated Technology Express, Inc. Device 8892 (rev 30)
    03:00.0 USB Controller: NEC Corporation Device 0194 (rev 03)
    04:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. Device 3403 (rev 01)



also i am facing problem with the graphics....i am not getting more than 800 x 600 resolution after the up-gradation...

---

### Post by asamay81 on 2012-03-02
experts, please visit my thread to solve my problem :-(

---

### Post by MG&amp;TL on 2012-03-02
Ooops! Never mind, thanks varuenda.

---

### Post by varunendra on 2012-03-02
See if this post can help you: [http://ubuntuforums.org/showthread.php?p=10587566](http://ubuntuforums.org/showthread.php?p=10587566)

If not, please post the outputs of:
```
lspci -nnk | grep -iA2 net
lsmod
```Wrap the output in 'Code' tags (using **'#'** at the top of edit box) instead of 'Quote' (as you did in the 2nd last post). That is the correct way to post output codes.


**_PS_:**
*MG&TL,* the OP didn't say 'wireless' as far as I could notice, just 'network device'. Since it is a PC (not a laptop), I don't think there is a wireless device available (of course unless a PCI or USB one is used).

*@asamay81,*
Please post a different thread for the graphics issues. Different problems => different threads.

---

### Post by imachavel on 2012-03-02
"The DH67GD Motherboard only supports - Intel Core i5 Processor
- Intel Core i7 Processor"

Gigabit (10/100/1000 Mb/s) LAN subsystem using the Intel® 82579V Gigabit Ethernet Controller

[http://www.costcentral.com/proddetail/Intel_Desktop_Board_DH67GD_Media_Series/BOXDH67GDB3/11310873/](http://www.costcentral.com/proddetail/Intel_Desktop_Board_DH67GD_Media_Series/BOXDH67GDB3/11310873/)

no matter where I look on the internet it won't tell me what your onboard gpu specs are, it just says over and over hit after hit again:

Graphics	Intel HD Graphics

how did you fit an i3 on there? same number of pins? Same dimensions that fit into the socket? You have given us little information

what network problem are you facing? host to router? host to server? host to host? 


lspci -nnk | grep -iA2 net
03:08.0 Ethernet controller [0200]: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller [8086:1064] (rev 03)
	Subsystem: Dell Device [1028:0181]
	Kernel driver in use: e100


lsmod
Module                  Size  Used by
nls_utf8               12493  1 
udf                    83826  1 
crc_itu_t              12627  1 udf
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             13328  0 
vboxnetflt             27211  0 
vboxdrv               251814  3 vboxpci,vboxnetadp,vboxnetflt
dm_crypt               22565  0 
ppdev                  12849  0 
joydev                 17393  0 
snd_usb_audio         100930  1 
snd_usbmidi_lib        24558  1 snd_usb_audio
r8712u                163310  0 
gspca_sonixj           32391  0 
gspca_main             27610  1 gspca_sonixj
dcdbas                 14098  0 
videodev               85626  1 gspca_main
snd_hda_codec_hdmi     31426  1 
snd_hda_intel          24262  1 
snd_hda_codec          91859  2 snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13276  2 snd_usb_audio,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  2 snd_usbmidi_lib,snd_seq_midi
ip6t_LOG               16846  4 
xt_hl                  12465  6 
ip6t_rt                12473  3 
nf_conntrack_ipv6      13581  7 
nf_defrag_ipv6         13139  1 nf_conntrack_ipv6
ipt_REJECT             12512  1 
ipt_LOG                12783  5 
psmouse                73673  0 
xt_limit               12541  12 
xt_tcpudp              12531  23 
xt_addrtype            12596  4 
xt_state               12514  14 
snd_seq_midi_event     14475  1 snd_seq_midi
ip6table_filter        12711  1 
ip6_tables             22528  3 ip6t_LOG,ip6t_rt,ip6table_filter
nf_conntrack_netbios_ns    12585  0 
nf_conntrack_broadcast    12541  1 nf_conntrack_netbios_ns
nf_nat_ftp             12595  0 
nf_nat                 24958  1 nf_nat_ftp
nf_conntrack_ipv4      19084  9 nf_nat
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
nf_conntrack_ftp       13183  1 nf_nat_ftp
nf_conntrack           70103  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         12706  1 
ip_tables              18106  1 iptable_filter
x_tables               21975  13 ip6t_LOG,xt_hl,ip6t_rt,ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
binfmt_misc            17292  1 
serio_raw              12990  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_intel8x0           33318  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80435  6 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_intel8x0,snd_ac97_codec
fglrx                2756852  128 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_timer              28932  2 snd_seq,snd_pcm
parport_pc             32114  1 
snd                    55902  21 snd_usb_audio,snd_usbmidi_lib,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_seq,snd_intel8x0,snd_ac97_codec,snd_pcm,snd_seq_device,snd_timer
soundcore              12600  1 snd
snd_page_alloc         14115  3 snd_hda_intel,snd_intel8x0,snd_pcm
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
vesafb                 13489  1 
usb_storage            44173  0 
usbhid                 41905  0 
hid                    77367  1 usbhid
uas                    17699  0 
e100                   36289  0 
floppy                 60310  0 

there are my specs, lspci will only explain what drivers are installed and which aren't, as far as I know. Your screen resolution won't go any higher then 800 x 600 resolution? I can't say I understand that. Ubuntu uses opengl graphics library api to load and cache graphic processing bits from the interface, which I believe includes photo and video formats, not including codecs, but supporting java for things such as flash plug ins, as far as I know, instead of what windows uses which is directx11 for 7, directx10 for vista, and directx9 for xp.

But if your gpu with installed windows drivers could easily do a higher resolution then 800 x 600, then maybe it's a configuration with the interface you are using, gnome or unity of kde, or possibly you could use an updated driver. And possibly it's another issue I'm unaware of.

have you tried

sudo apt-get install update in the terminal? Anyway, sorry the specs for the intel gpu aren't up to date, maybe there is lack of driver support for your intel gpu, which is prohibiting your resolution issue. I'd say otherwise it's a configuration issue, but I'm not sure how to toggle around the settings to fix it.

what network issue are you having?

ifconfig in terminal as well please, thanks

I'm not an expert at reading lspci, we can see all your devices, but I can't tell which drivers are installed correctly.

---

### Post by varunendra on 2012-03-02
> **imachavel said:**
> "The DH67GD Motherboard only supports - Intel Core i5 Processor
- Intel Core i7 Processor"
The best place to look for specs is the [manufacturer's site]("http://www.intel.com/content/www/us/en/motherboards/desktop-motherboards/desktop-board-dh67gd.html").
Evidently, it not only support i3's, but also some xeons, pentiums, even some celeron processors (full list [here]("http://processormatch.intel.com/CompDB/SearchResult.aspx?BoardName=DH67GD"))

> **imachavel said:**
> no matter where I look on the internet it won't tell me what your onboard gpu specs are, it just says over and over hit after hit again:

Graphics    Intel HD GraphicsIt is the new Intel HD (2000/3000) graphics that is embedded in the processor, not an 'onboard' graphics. And that is (the one in sandy-bridge CPUs) a really nice graphics chip, capable of producing really cool high definition graphics.

> **imachavel said:**
> lspci will only explain what drivers are installed and which aren't, as far as I know. You can get to know more by simply looking at the man page of any command. As in case of lspci:
```
man lspci
```It can tell a lot more than just listing the associated driver(s). Without additional options/parameters, it only lists all the detected PCI buses, and devices connected to them.

As for the OP's graphics problems, I think it should be discussed in a separate thread to avoid distraction (and confusion) from the original problem here.

I hope this post answers a few of your doubts. Happy learning :)

---

### Post by Vpc on 2012-03-26
> **asamay81 said:**
> hi all
i have recently upgraded my PC to this configuration

intel core i3-2100 3.1 GHz processor
intel DH67GD motherboard
GSkill NT DDR3 4 GB RAM

my system is installed with two OS viz. ubuntu 10.04 LTS and MS WinXP SP 3

before the up-gradation i was in Pentium 4

the problem is after i upgraded my system, the network devise has been deactivated in ubuntu although it is working fine in windows. at present there is no active network devise. i do not understand why this problem has happened and need your kind help.

thanks in advance

~asamay~

> **imachavel said:**
> "The DH67GD Motherboard only supports - Intel Core i5 Processor
- Intel Core i7 Processor"

Gigabit (10/100/1000 Mb/s) LAN subsystem using the **Intel® 82579V Gigabit Ethernet Controller**

[http://www.costcentral.com/proddetail/Intel_Desktop_Board_DH67GD_Media_Series/BOXDH67GDB3/11310873/](http://www.costcentral.com/proddetail/Intel_Desktop_Board_DH67GD_Media_Series/BOXDH67GDB3/11310873/)



I also wasn't able to get the Intel 82579V Gigabit Ethernet Controller (on the Intel DP67DE motherboard) working with Ubuntu 10.04. Upgrading to Ubuntu 11.10 solved the problem. Looking online and in this forum, there seems to be a compatibility problem with older versions of Ubuntu and the onboard Intel 82579V ethernet controller and some of the newer ethernet cards.

---

