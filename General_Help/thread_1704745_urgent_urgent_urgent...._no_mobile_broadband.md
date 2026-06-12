---
title: "urgent urgent urgent.... no mobile broadband"
date: 2011-03-11
forum: General Help
---

### Post by vivek.pandey on 2011-03-11
hey everyone
  i dont know where to post this into ubuntu forums as there is an option for other os.
  i have ubuntu 10.10 though there is nothing to do with that. i am trying to boot backtrack 4 from a dvd. everything is fine but the problem is it is not recognising my 3g modem. its really urgent. i posted in backtrack forums too but seems nobody cares going there . i googled without any success. its a usb broadband modem . when i type lsusb it lists the modem as one of the devices but neither mounts it nor let me see its software so that i can install it . in new connection also there is no option for mobile broadband
so please somebody help . its really important. i am undergoing an online course and i need to use the cd to learn stuffs

please

thanx in advance

---

### Post by DanneStrat on 2011-03-11
> **neo_aryan said:**
> hey everyone
  i dont know where to post this into ubuntu forums as there is an option for other os.
  i have ubuntu 10.10 though there is nothing to do with that. i am trying to boot backtrack 4 from a dvd. everything is fine but the problem is it is not recognising my 3g modem. its really urgent. i posted in backtrack forums too but seems nobody cares going there . i googled without any success. its a usb broadband modem . when i type lsusb it lists the modem as one of the devices but neither mounts it nor let me see its software so that i can install it . in new connection also there is no option for mobile broadband
so please somebody help . its really important. i am undergoing an online course and i need to use the cd to learn stuffs

please

thanx in advance

Hi!

Could you post the output of:

```
lsusb
```

```
sudo lshw -c network
```

and

```
lsmod
```

---

### Post by grahammechanical on 2011-03-11
Have you looked at the backtrack wiki? There is a page there under Getting Started>Basic Usage>Getting Networking to Work. There is not any mention of Mobile networking but some of the information may be useful. And you may become the expert on the subject. It is all part of learning.

Regards.

---

### Post by vivek.pandey on 2011-03-11
> **DanneStrat said:**
> Hi!

Could you post the output of:

```
lsusb
```

```
sudo lshw -c network
```

and

```
lsmod
```

thanx for your reply . 
here are the output
lsusb
```

Bus 002 Device 079: ID 230d:0001  
Bus 002 Device 078: ID 1c4f:0003 SiGma Micro 
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 007: ID 413c:8162 Dell Computer Corp. 
Bus 001 Device 006: ID 413c:8161 Dell Computer Corp. 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 005: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 004: ID 0c45:641d Microdia 
Bus 001 Device 003: ID 0a5c:4500 Broadcom Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

lshw -c network
```

 *-network UNCLAIMED
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: b8:ac:6f:5b:26:60
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s

```

lsmod

```

Module                  Size  Used by
ipv6                  242292  14 
rfkill                 13644  0 
input_polldev           7304  0 
iptable_filter          6656  0 
ip_tables              14992  1 iptable_filter
x_tables               16644  1 ip_tables
firewire_sbp2          18060  0 
firewire_core          40096  1 firewire_sbp2
parport_pc             28196  0 
lp                     13572  0 
parport                34924  2 parport_pc,lp
joydev                 13760  0 
video                  20624  0 
snd_seq_dummy           6660  0 
output                  6656  1 video
snd_hda_intel         406928  0 
snd_pcm_oss            42016  0 
snd_mixer_oss          18432  1 snd_pcm_oss
snd_pcm                72068  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         12168  2 snd_hda_intel,snd_pcm
snd_hwdep              11012  1 snd_hda_intel
snd_seq_oss            33792  0 
psmouse                45840  0 
snd_seq_midi           10272  0 
serio_raw               9220  0 
snd_rawmidi            23200  1 snd_seq_midi
snd_seq_midi_event     10112  2 snd_seq_oss,snd_seq_midi
snd_seq                51824  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
sg                     28724  0 
snd_timer              23176  2 snd_pcm,snd_seq
wmi                     9896  0 
snd_seq_device         10252  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    52388  10 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9952  1 snd
dcdbas                 11168  0 
shpchp                 35860  0 
evdev                  13344  15 
fuse                   55068  6 
aufs                  139272  1 
squashfs               45060  11 
sqlzma                  6916  1 squashfs
unlzma                  8448  1 sqlzma


```

---

### Post by vivek.pandey on 2011-03-11
sorry i am bumping it so soon but its really urgent so cant help. hope you understand

---

### Post by vivek.pandey on 2011-03-13
bump?

---

### Post by vivek.pandey on 2011-03-21
can no one solve this problem?

---

### Post by uRock on 2011-03-21
Have you posted in BT's forums? I have had problems in the past with getting their OS to see my NICs as well.

---

### Post by vivek.pandey on 2011-03-21
> **uRock said:**
> Have you posted in BT's forums? I have had problems in the past with getting their OS to see my NICs as well.

well it seems there forum is no that active and you gotta wait for days for even the first reply
and anyways if there is a solution to this problem in ubuntu it must work in back track also..

---

### Post by Script Warlock on 2011-03-21
> **neo_aryan said:**
> well it seems there forum is no that active and you gotta wait for days for even the first reply
and anyways if there is a solution to this problem in ubuntu it must work in back track also..

try this one [http://www.backtrack-linux.org/forums/old-backtrack-4-working-hardware/19666-huawei-e156g-3g-usb-modem-works-bt4-pre-final.html](http://www.backtrack-linux.org/forums/old-backtrack-4-working-hardware/19666-huawei-e156g-3g-usb-modem-works-bt4-pre-final.html) or visit backtrack irc channel.

---

### Post by jdeslaur on 2011-03-21
the legal implications of a backtrack dvd and mobile broadband is questionable so i am not going to ask :D

Everytime I have booted backtrack I have had to edit the /etc/networking/interfaces and then /etc/init.d/network restart, also under ifconfig make sure that it is using the broadband card.

---

### Post by vivek.pandey on 2011-03-21
> **Script Warlock said:**
> try this one [http://www.backtrack-linux.org/forums/old-backtrack-4-working-hardware/19666-huawei-e156g-3g-usb-modem-works-bt4-pre-final.html](http://www.backtrack-linux.org/forums/old-backtrack-4-working-hardware/19666-huawei-e156g-3g-usb-modem-works-bt4-pre-final.html) or visit backtrack irc channel.

thanx for your reply .. the problem is i need to first of all install wvdial..now since modem is not configured i cant connect to net and so cant install wvdial..its like who came first chicken or hen ;-)

---

### Post by jdeslaur on 2011-03-21
Yea that might be hard to do especially with the dvd, might want to invest in a persistant usb install so that all your changes stick.  Just my two cents.

---

### Post by vivek.pandey on 2011-03-21
> **jdeslaur said:**
> the legal implications of a backtrack dvd and mobile broadband is questionable so i am not going to ask :D

Everytime I have booted backtrack I have had to edit the /etc/networking/interfaces and then /etc/init.d/network restart, also under ifconfig make sure that it is using the broadband card.

can you please explain in detail what to edit /etc/networking/interfaces to make it work

---

### Post by Script Warlock on 2011-03-21
let me try this method... perhaps sakis3g can help me.

---

### Post by vivek.pandey on 2011-03-21
ok know i have thought of installing BT in my 4 gb sandisk pen drive using my BT4 dvd . after that i will install it in my virtual box and since in virtual box it will be like wired network i can then download wvdial and then try to configure my modem... anyone knows how can i install it in my pen drive and is this idea worth giving a try?

---

### Post by jdeslaur on 2011-03-21
[URL="http://www.infosecramblings.com/backtrack/backtrack-4-bootable-usb-thumb-drive-with-full-disk-encryption/"]LINK!!!
[/URL]

---

