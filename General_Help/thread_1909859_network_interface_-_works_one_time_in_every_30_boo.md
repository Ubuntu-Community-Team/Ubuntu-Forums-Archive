---
title: "network interface - works one time in every 30 boots"
date: 2012-01-16
forum: General Help
---

### Post by FernandoLB on 2012-01-16
lspci shows:
```
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```The modules 8139too and 8139cp are always being loaded, still, the network only works about one time in every 30 boots.

ifconfig does show that the card is up, but it gets no ip. I have tried setting a static ip, then nm-applet icon shows as connected but still no connection.

I also have tried removing network-manager from boot and configure everything from
/etc/network/interfaces, one time with static ip, other with dhcp but it didn't solve anything.

Other thing I tried to do was to remove one of the aforementioned modules and load only the other (I have tried the two possible combinations) but also no luck.

And as a last resource, I tried creating an alias in /etc/modules.conf, with
```
alias eth0 8139too
```and also tried with 8139cp as well.

Nothing of the things mentioned so far seem to make difference. 

It is my son's computer, and it also runs XP besides ubuntu. In XP, the network never gives problems (I hate having to put it that way). So, I would say the problem is not with the network card, which is onboard, by the way.

Any help would be appreciated. Thanks in advance.

---

### Post by xc3RnbFO8P on 2012-01-16
Try to change channel in router.

---

### Post by FernandoLB on 2012-01-16
> **Ringi said:**
> Try to change channel in router.

Would you mind explaining why that would make any difference?

I'll do that as soon as I get home. Thanks for helping.

---

### Post by xc3RnbFO8P on 2012-01-16
> **FernandoLB said:**
> Would you mind explaining why that would make any difference?


Here is a explication:
[http://www.howtogeek.com/howto/21132/change-your-wi-fi-router-channel-to-optimize-your-wireless-signal/]("http://www.howtogeek.com/howto/21132/change-your-wi-fi-router-channel-to-optimize-your-wireless-signal/")
My solution was to buy new router.

---

### Post by FernandoLB on 2012-01-16
> **Ringi said:**
> Here is a explication:
[http://www.howtogeek.com/howto/21132/change-your-wi-fi-router-channel-to-optimize-your-wireless-signal/](http://www.howtogeek.com/howto/21132/change-your-wi-fi-router-channel-to-optimize-your-wireless-signal/)
My solution was to buy new router.

I live in a house, and there isn't a single other wireless network near here. Also, all the other computers (three more, two running only linux and one more running windows and ubuntu - my other son's computer) are working fine. Moreover , the computer with network problems in connected through cable.

I forgot to mention before, the computer presenting problems used to work fine until about one year ago, and the modem and router were the same, with the very same config.

---

### Post by varunendra on 2012-01-16
@Ringi,
Probably you missed the fact that the interface in question is "Ethernet", not a wifi. So the channel factor doesn't exist here.


@FernandoLB,
At the moment do you have Network Manager installed? If yes, does "Enable networking" option in its drop-down menu appear to be 'ticked' each time?

Although you have tried to provide enough details with a thorough description, I think posting them all in a standard form will make it easier for us to analyze the problem (maybe your description is enough for a real expert, but I'm just a learner). Accordingly, please post the outputs of the following commands:
```
ifconfig -a
lshw -C network
lsmod
cat /etc/network/interfaces
cat /etc/resolv.conf
route -n
```

Also, when it fails to connect (it seems that now it permanently is):
```
dmesg | grep -i eth0
```

To post the outputs, please click on **#** symbol at the top of edit box (in which you type your posts) to automatically create [noparse]```
..and..
```[/noparse] tags. Then copy-paste the output between the generated 'code' tags.

Post each set of output in separate sets of code tags.

Thank you.

---

### Post by xc3RnbFO8P on 2012-01-16
> @Ringi,
Probably you missed the fact that the interface in question is "Ethernet", not a wifi. So the channel factor doesn't exist here.
Yes :redface:

---

### Post by FernandoLB on 2012-01-16
> **varunendra said:**
> 


@FernandoLB,
At the moment do you have Network Manager installed? If yes, does "Enable networking" option in its drop-down menu appear to be 'ticked' each time?
Yes, it is installed and it appears to be ticked every time.


ifconfig -a:
```

eth0      Link encap:Ethernet  HWaddr 00:1e:90:f6:ea:62  
          inet addr:192.168.1.133  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:90ff:fef6:ea62/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0xe800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:61 errors:0 dropped:0 overruns:0 frame:0
          TX packets:61 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5558 (5.5 KB)  TX bytes:5558 (5.5 KB)


```lshw -C network:
```


  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth0
       version: 10
       serial: 00:1e:90:f6:ea:62
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half ip=192.168.1.133 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:20 ioport:e800(size=256) memory:febffc00-febffcff


```lsmod:
```

Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
binfmt_misc            17292  1 
vesafb                 13489  1 
ppdev                  12849  0 
nvidia              10390874  40 
joydev                 17393  0 
snd_hda_codec_idt      60049  1 
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
parport_pc             32114  1 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
usb_storage            44173  1 
uas                    17699  0 
8139too                23283  0 
8139cp                 22636  0 

```cat /etc/network/interfaces:
```


auto lo
    iface lo inet loopback

# It didn't work with either dhcp or static ip, so I disabled 
# them here and enabled network-manager again.

#auto eth0
#    iface eth0 inet dhcp

#iface eth0 inet static
#    address 192.168.1.2
#    netmask 255.255.255.0
#    network 192.168.1.0
#    broadcast 192.168.1.255
#    gateway 192.168.1.1

```cat /etc/resolv.conf:
```


# Generated by NetworkManager
nameserver 208.67.222.222


```route -n:
```


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

```dmesg | grep -i 'eth0':
```


[    1.431181] 8139too 0000:02:05.0: eth0: RealTek RTL8139 at 0xe800, 00:1e:90:f6:ea:62, IRQ 20
[   15.943872] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   26.040049] eth0: no IPv6 routers present
[   27.824037] NETDEV WATCHDOG: eth0 (8139too): transmit queue 0 timed out
[   30.832097] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   42.832075] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   54.832078] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   66.832076] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   78.832087] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   90.832079] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  102.832099] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  114.832097] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  126.832079] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  138.832076] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  150.832075] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  162.832070] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  174.832070] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  186.832080] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  198.832082] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  210.832096] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  222.832077] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  234.832105] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  246.832075] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  258.832070] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  270.832076] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  282.832078] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  294.832074] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  306.848095] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  319.024056] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  331.024072] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  343.024076] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  355.024097] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  367.024075] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  379.024068] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  391.024084] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  403.024056] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  415.024135] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  427.024063] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  439.024095] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  451.024134] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1

```

One thing to notice is that when it doesn't work, I can't even ping the router. I get "Destination Host Unreachable" (even nm icon showing as connected).

---

### Post by varunendra on 2012-01-16
Before drawing any assumptions/conclusions, I would also like to see outputs of:
```
lspci -nnk | grep -iA2 net
dmesg | grep -iE 'eth | 8139'
```..when it fails to connect.

Also, have you tried replacing the cable? I think a bad connection can also trigger similar issues.


**_Edit_:**
Requested *dmesg *command changed. Please post results of the modified one.

---

### Post by dino99 on 2012-01-16
my interface settings:

auto eth0
iface eth0 inet dhcp


# The loopback network interface
auto lo
iface lo inet loopback

So add dhcp to see if its making a difference
By the way i dont use network-manager as it have lot of issues, but wicd.

And the logs might help you know about the issues.

---

### Post by FernandoLB on 2012-01-17
Sorry for the delay.
EDIT: the following information was taken when the network **fails**.

> **varunendra said:**
> Before drawing any assumptions/conclusions, I would also like to see outputs of:
```
lspci -nnk | grep -iA2 net
dmesg | grep -iE 'eth | 8139'
```..when it fails to connect.


**lspci -nnk | grep -iA2 'net'**:
```

02:05.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139]
    Kernel driver in use: 8139too

```**dmesg | grep -iE 'eth | 8139'**:
```


[    1.278978] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    1.279006] 8139cp 0000:02:05.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    1.279586] 8139too: 8139too Fast Ethernet driver 0.9.28
[    1.279638] 8139too 0000:02:05.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.301356] 8139too 0000:02:05.0: eth0: RealTek RTL8139 at 0xe800, 00:1e:90:f6:ea:62, IRQ 20
[   10.949954] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   22.832054] Modules linked in: vesafb nvidia(P) ppdev bnep rfcomm bluetooth snd_hda_codec_idt snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi joydev binfmt_misc snd_seq_midi_event snd_seq snd_timer parport_pc snd_seq_device snd soundcore snd_page_alloc lp parport usbhid hid usb_storage uas 8139too 8139cp
[   25.840114] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   37.840060] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   49.840059] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   61.840079] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   73.840068] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   85.840097] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   97.840116] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  109.840074] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  121.840068] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  133.840068] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  145.840097] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  157.840054] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  169.840076] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  181.840077] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  193.840077] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  205.840095] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  217.840097] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  229.840073] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  241.840077] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  253.840076] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  265.840096] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  277.840075] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  289.840072] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  301.840071] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  314.016069] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  326.016062] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  338.016097] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  350.016061] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  362.016088] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  374.016064] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  386.016063] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  398.016214] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  410.016062] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  422.016100] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  434.016043] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  446.016063] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  458.016061] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  470.016061] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  482.016087] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  494.016070] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  506.016050] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  518.016061] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  530.016048] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  542.016062] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  554.016050] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  566.016069] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  578.016061] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  590.016068] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  602.016061] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  614.016088] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  626.016061] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  638.016062] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  650.016061] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  662.016062] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  674.016088] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  686.016070] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1

```> **varunendra said:**
> 
Also, have you tried replacing the cable? I think a bad connection can also trigger similar issues.

Yes, I have.

---

### Post by gsgleason on 2012-01-17
All those link up messages are suspect.  Do you see them when it works, or only when it does not?

Similar threads for different realtek hardware involve various fixes, from removing power and batter and letting it sit for a while to using the module provided by realtek.

This could be a hardware problem.  Have you tried re-seating your nic in your motherboard? (I don't know if this is a desktop or laptop or what).

What is your cable connected to?  Have you tried swapping ports on your switch?

---

### Post by varunendra on 2012-01-18
> **FernandoLB said:**
> 
Other thing I tried to do was to remove one of the aforementioned modules and load only the other (I have tried the two possible combinations) but also no luck.

How did you do it? The temporary way would be:
```
sudo modprobe -rv 8139cp
sudo modprobe -rv 8139too
sudo modprobe -v 8139too
```
(-v just for verbose to see what's happening)

After doing this, you may (or may not) have to:
```
sudo /etc/init.d/networking restart
```

Or

```
sudo ifconfig eth0 down
```
then after a few seconds:
```
sudo ifconfig eth0 up
```

Permanent way to prevent 8139cp from being loaded 'should' be to include it in /etc/modprobe.d/blacklist.conf , but some googling suggests that for some reason, the blacklist method doesn't work with 8139cp.

But whatever method you chose to remove one of the modules, did you make sure with *lsmod* that it was actually removed?


Also, assuming your last post displayed outputs when it 'failed' to connect, it seems the device is correctly detected and the correct driver is loaded even this time. So this makes me wonder if this can be a DHCP issue (even though you've clearly stated that you've tried static IP, sorry if I'm being paranoid). Accordingly, a few more questions-

[LIST]
[*]When you assigned static IP, did you manually set and verify all of these - IP, Netmask, Gateway and DNS?
[*]If so, did you try pinging all of these - gateway, DNS and any other IP on the network (if any exist)? Which ones failed? Was there an error message, or no reply at all?
[/LIST]


**_PS_:**

Another possible solution to a similar problem I found was to use mii-tool to 'force' "10baseT-FD" mode on eth0, but it doesn't seem relevant in your case, since module 'mii' is not loaded as per your lsmod - suggesting your eth0 is almost certainly not a supported interface.
The link to above solution (if you wish to try it anyway): [http://ubuntuforums.org/showpost.php?p=6873299&postcount=1](http://ubuntuforums.org/showpost.php?p=6873299&postcount=1) (the ###**edit**### part at the bottom of the post)
The commands are:
```
sudo mii-tool eth0 -F 10baseT-FD
sudo rmmod 8139too
sudo modprobe 8139too

```

---

### Post by FernandoLB on 2012-01-18
Well, to keep this short, I tried everything posted above (I had already done very similar things myself before). None have worked.

When I remove the module, then the nm-applet icon shows as disconnected, when I load the module again, it shows as connected. If I try to edit the connection, it says "Name = eth0" (I set that name) and "Last Used = **now**", but it doesn't connect. For example, firefox says "looking up for www.google.com" until it gives up, like if it were a dns issue, however, even if I try with a ip (or ping) as 74.125.234.50 it just fails.

About the ping, I can't ping anything. Not even a single pc or even the router (which I indeed can ping from other machines). I'm pretty sure the route, DNS, and everything else is set properly (it is the same config I use on the other machines, except the ip). It is set to static ip. 

I have also tried again disabling network-manager and doing everything from the command line and from /etc/network/interfaces.

---

