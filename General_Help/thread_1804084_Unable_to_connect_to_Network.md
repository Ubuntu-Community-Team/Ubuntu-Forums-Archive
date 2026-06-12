---
title: "Unable to connect to Network"
date: 2011-07-14
forum: General Help
---

### Post by robperryuk on 2011-07-14
I'm a complete newbie to Ubunto so be gentle with me! 
 
I've just installed 11.04 Natty on an old Laptop (Dell Lattitude C400) and am unable to connect to my home network (wired LAN connection, no wireless). The laptop previously had WinXP installed and was able to connect (I have also double checked the cables and ports and they're all functioning ok).
 
Having read plenty of other posts of people with similar problems hopefully this info will also help.....
 
sudo lshw -C network
```

*-network
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 0
       bus info: pci@0000:02:00.0      
       logical name: eth0
       version: 78
       serial: 00:0b:db:08:f3:48
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
              configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full latency=32 link=yes maxlatency=10 mingnt=10 multicast=yes port=MII speed=100Mbit/s
       resources: irq:11 ioport:ec80(size=128) memory:fafffc00-fafffc7f memory:fb000000-fb01ffff

```
 
lspci -nn
```

00:00.0 Host bridge [0600]: Intel Corporation 82830 830 Chipset Host Bridge [8086:3575] (rev 04)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82830 CGC [Chipset Graphics Controller] [8086:3577] (rev 04)
00:02.1 Display controller [0380]: Intel Corporation 82830 CGC [Chipset Graphics Controller] [8086:3577]
00:1d.0 USB Controller [0c03]: Intel Corporation 82801CA/CAM USB Controller #1 [8086:2482] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 42)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801CAM ISA Bridge (LPC) [8086:248c] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801CAM IDE U100 Controller [8086:248a] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801CA/CAM AC'97 Audio Controller [8086:2485] (rev 02)
00:1f.6 Modem [0703]: Intel Corporation 82801CA/CAM AC'97 Modem Controller [8086:2486] (rev 02)
02:00.0 Ethernet controller [0200]: 3Com Corporation 3c905C-TX/TX-M [Tornado] [10b7:9200] (rev 78)
02:01.0 CardBus bridge [0607]: Texas Instruments PCI1410 PC card Cardbus Controller [104c:ac50] (rev 02)

```
 
ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:0b:db:08:f3:48  
          inet6 addr: fe80::20b:dbff:fe08:f348/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:85 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:13166 (13.1 KB)  TX bytes:11160 (11.1 KB)
          Interrupt:11 Base address:0xcc00
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:216 errors:0 dropped:0 overruns:0 frame:0
          TX packets:216 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:16896 (16.8 KB)  TX bytes:16896 (16.8 KB)

```
 
lsmod
```

Module                  Size  Used by
parport_pc             32111  1 
ppdev                  12849  0 
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80244  2 snd_intel8x0,snd_ac97_codec
i915                  450944  2
snd_seq_midi           13132  0
snd_rawmidi            25269  1 snd_seq_midi
binfmt_misc            13213  1 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
joydev                 17322  0 
drm_kms_helper         40745  1 i915
pcmcia                 39671  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   180037  2 i915,drm_kms_helper
yenta_socket           27230  0 
dcdbas                 14054  0 
psmouse                73312  0 
pcmcia_rsrc            18292  1 yenta_socket
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              12990  0 
i2c_algo_bit           13184  1 i915
shpchp                 32345  0 
soundcore              12600  1 snd
video                  18951  1 i915
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
floppy                 60032  0
3c59x                  37398  0

```
 
contents of /etc/network/interfaces/
```

auto lo
iface lo inet loopback

```
 
Anyone got any ideas??
 
Thanks!!

---

### Post by Bucky Ball on 2011-07-14
Static or dynamic IP address? Plugged into a router or modem? Network manager or something else (wicd, madwifi)?

You provided a lot of good info there, BTW, so well sniffed out. ;)

---

### Post by robperryuk on 2011-07-14
Hi, thanks for helping out...
 
I would assume DHCP IP address (I haven't tried to create a fixed one and all other computers on the network pick up a DHCP address). Connected to a router (BT Home Hub2). Not sure if it makes a difference but it appears the router recognised the laptop and assigned a DHCP address at some point after I re-built it with Ubunto (the laptop, with it's post-rebuild name appeared in the device list but showing as disconnected)
 
Not sure what your last question is asking for!! If it refers to what software I'm using or anything like that then I haven't changed (or added) anything since installing. It is running GNOME 2.32.1

---

### Post by Wim Sturkenboom on 2011-07-14
You can try to edit /etc/network/interfaces following the instructions on [http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html](http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html)

```

# The primary network interface - use DHCP to find our address
auto eth0
iface eth0 inet dhcp

```

By the way, my networkcard is a 3C905B so I would expect yours to work as well

---

### Post by robperryuk on 2011-07-14
Thanks Wim
 
I added those three lines to the end of /etc/network/interfaces so it now contains:
```

auto lo
iface lo inet loopback
 
# The primary network interface - use DHCP to find our address
auto eth0
iface eth0 inet dhcp

```
 
This doesn't appear to have resolved the problem. One thing has changed, it now says "device not managed" under Wired connections in the network menu and I no longer see auto eth0 in the list to pick!

---

### Post by Bucky Ball on 2011-07-14
I would perhaps take the added code out again so you don't confuse the issue too much. You shouldn't need them.

Try the fix from post #4 here:

[http://ubuntuforums.org/showthread.php?t=951563](http://ubuntuforums.org/showthread.php?t=951563)

You might also get some clues from this search:

[http://www.google.com.au/#hl=en&q=3Com+Corporation+3c905C-TX%2FTX-M+](http://www.google.com.au/#hl=en&q=3Com+Corporation+3c905C-TX%2FTX-M+)[Tornado]+ubuntu+10.04&oq=3Com+Corporation+3c905C-TX%2FTX-M+[Tornado]+ubuntu+10.04&aq=f&aqi=&aql=1&gs_sm=e&gs_upl=2677l4348l0l4632l6l6l0l5l0l0l332l332l3-1l1&bav=on.2,or.r_gc.r_pw.&fp=6e35740dee461c14&biw=1366&bih=596

---

### Post by robperryuk on 2011-07-14
Yeah, good idea, didn't look like that additon had helped. Have reverted  /etc/network/interfaces back to it's original state
 
I tried the fix from the thread you suggested but i encountered a number of problems: in that ""pci-config: command not found" and when I try to install nictools-pci it says "unable to locate package". I assume this is because I have no connectivity.
 
Any other ideas??
 
You'll have to excuse my ignorance, have be a windows slave all my life so this is all very new to me!

---

### Post by Bucky Ball on 2011-07-14
> **robperryuk said:**
> You'll have to excuse my ignorance, have be a windows slave all my life so this is all very new to me!

No problem. We all start somewhere and you're in the right place. ;)

Yea, that would be because you can't get online that you're getting those errors, sorry. Brain melt on my part.

Awfully strange the wired connection not working 'out of the box.' I'll have a bit more of a dig or hopefully someone who knows the issue will chime in ...

Did you 'Try Ubuntu' from the LiveCD (the install CD) before installing? If so, did you have a wired connection then no problem? If you didn't try that, boot from the LiveCD and give it a go. If it fails, then I would perhaps suggest trying the current long-term support release (10.04 LTS) as it is a good place to start anyhow; a bit more stable and likely to 'just work'.

---

### Post by Wim Sturkenboom on 2011-07-14
//Edit

never mind, this was bull

---

### Post by robperryuk on 2011-07-15
I attempted the "try ubunto" option however I couldn't get it to run, I did however get the laptop fired up from a linux boot disk and ran ifconfig, and it gave me a DHCP IP address and I was able to ping my router. Downloading 10.04 LTS now and will try that and see what happens......!

---

### Post by robperryuk on 2011-07-15
update.... have tried going back to 10.04, same symptoms!

---

### Post by robperryuk on 2011-07-16
Woo Hoo, finally got it working.
 
It appears the problem was an incompatibility with my BT Home Hub 2 and the fact it doesn't like having multiple DHCP addresses with the same MAC address (I have previously connected using XP so still had an entry in the DHCP table). So I went in to the Network Manager and set a fixed IP address and bingo we have connectivity!!

---

### Post by Bucky Ball on 2011-07-16
Double woo hoo! So it was never us or Ubuntu in the first place! That connection was working 'out of the box', as we say.

Welcome to the forums, Linux, and Ubuntu. Yes, there is a learning curve, but ain't that what it's about? Enjoy. ;)

---

