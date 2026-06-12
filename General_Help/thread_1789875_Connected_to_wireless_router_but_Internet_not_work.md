---
title: "Connected to wireless router but Internet not working"
date: 2011-06-24
forum: General Help
---

### Post by maggle66 on 2011-06-24
Hi,
 
I am a complete newbie to Ubuntu and have installed 11.04 on a Samsung Netbook N145 plus from USB and dual boot with Windows 7. Everything installed fine and looked good but I am unable to browse the Internet. Windows 7 connects and browses fine.
I've done some of my own research and can see my WLAN0 card in ifconfig and can see that I have an IP assigned from my router. I have tried to ping google by name and IP without success. I tried adding nameservers to resolv.conf but didn't expect this to work as pinging IPs fails also.
I tried disabling IPV6 in /etc/sysctl.conf with the following code to no avail as suggested on another forum.
 
#disable ipv6
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1
 
 
Some suggestions made have been to use a different network driver and I have looked at 'additional drivers' but nothing comes up.
It looks like a common issue but I still haven't found a definitive solution with newbie instructions on how to fix.
I am a complete Linux novice, trying to learn at the moment but I am a Windows consultant so quite happy to try anything as long as I get step by step instructions.
For further info, I also had the same issue with Jolicloud. 
 
As a further test I installed Jolicloud and Ubuntu onto my wife's MSI Netbook and it worked perfectly first time so do suspect the wireless card driver.
 
Any help would be greatly appreciated as I really want to use Ubuntu, thanks.

---

### Post by cprofitt on 2011-06-24
I would not suspect the wireless card if you are really getting an IP address from the wireless router.  can you post the output of your ifconfig for your wireless card?

---

### Post by maggle66 on 2011-06-25
> **cprofitt said:**
> I would not suspect the wireless card if you are really getting an IP address from the wireless router. can you post the output of your ifconfig for your wireless card?
 
Hi cprofitt, thanks for the reply. I've gathered a fair bit of info to help, please see below. 
 
ifconfig
 
eth0      Link encap:Ethernet  HWaddr e8:11:32:40:9c:96  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:500 (500.0 B)  TX bytes:500 (500.0 B)
wlan0     Link encap:Ethernet  HWaddr b4:74:9f:71:4b:33  
          inet addr:192.168.1.69  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:54 errors:0 dropped:0 overruns:0 frame:0
          TX packets:61 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6741 (6.7 KB)  TX bytes:7039 (7.0 KB)
          Interrupt:16 Memory:f82d0000-f82d0100

sudo lshw -C network
 
  *-network               
       description: Wireless interface
       product: RTL8192SE Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: [EMAIL="pci@0000:05:00.0"]pci@0000:05:00.0[/EMAIL]
       logical name: wlan0
       version: 10
       serial: b4:74:9f:71:4b:33
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xSE driverversion=0017.0507.2010 firmware=63 ip=192.168.1.69 latency=0 link=yes multicast=yes wireless=802.11bgn
       resources: irq:16 ioport:2000(size=256) memory:f0100000-f0103fff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: [EMAIL="pci@0000:09:00.0"]pci@0000:09:00.0[/EMAIL]
       logical name: eth0
       version: 00
       serial: e8:11:32:40:9c:96
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:f0200000-f0203fff ioport:3000(size=256)

lspci -nn
 
00:00.0 Host bridge [0600]: Intel Corporation N10 Family DMI Bridge [8086:a010]
00:02.0 VGA compatible controller [0300]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a011]
00:02.1 Display controller [0380]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a012]
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 4 [8086:27d6] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation NM10 Family LPC Controller [8086:27bc] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation N10/ICH7 Family SATA AHCI Controller [8086:27c1] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
05:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192SE Wireless LAN Controller [10ec:8174] (rev 10)
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354]

lsmod
 
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17335  1 
fat                    55505  1 vfat
usb_storage            43946  1 
uas                    17676  0 
michael_mic            12540  8 
arc4                   12473  4 
cryptd                 19801  0 
aes_i586               16956  1 
aes_generic            38023  1 aes_i586
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_realtek   255820  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
i915                  450944  3 
binfmt_misc            13213  1 
snd_rawmidi            25269  1 snd_seq_midi
r8192se_pci           482505  0 
joydev                 17322  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
drm_kms_helper         40745  1 i915
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              156212  1 r8192se_pci
drm                   180037  4 i915,drm_kms_helper
uvcvideo               66851  0 
psmouse                73312  0 
videodev               75143  1 uvcvideo
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              12990  0 
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  2 
libahci                25548  1 ahci
sky2                   49172  0 
 
Thanks
 
Maggle

---

### Post by maggle66 on 2011-06-25
A bit further info. 
 
Testing today after a few reboots now manages to get some info from the Internet so DNS seems to be fine. I am getting a lot of packet loss though, see below.
 
ping [www.google.com]("http://www.google.com")
PING [www.l.google.com]("http://www.l.google.com") (209.85.147.103) 56(84) bytes of data.
64 bytes from bru01m01-in-f103.1e100.net (209.85.147.103): icmp_req=11 ttl=49 time=28.8 ms
64 bytes from 209.85.147.103: icmp_req=13 ttl=49 time=29.4 ms
64 bytes from 209.85.147.103: icmp_req=14 ttl=49 time=29.2 ms
^C64 bytes from 209.85.147.103: icmp_req=15 ttl=49 time=29.1 ms
--- [www.l.google.com]("http://www.l.google.com") ping statistics ---
15 packets transmitted, 4 received, 73% packet loss, time 46234ms
rtt min/avg/max/mdev = 28.882/29.160/29.407/0.226 ms

---

### Post by coldraven on 2011-06-25
I cannot help you with your wi-fi but if you are new to Linux this is a good tip.
[http://codeinthehole.com/archives/17-The-most-important-command-line-tip-incremental-history-searching-with-.inputrc.html](http://codeinthehole.com/archives/17-The-most-important-command-line-tip-incremental-history-searching-with-.inputrc.html)
Reading your post I thought to myself "What was that ping command I used about 3 months ago?"
All I had to do was type "p" and press the up arrow twice to find it, which returned the following output.
```
coldraven@happy:~$ ping -c 5 www.google.com
PING www.l.google.com (74.125.79.99) 56(84) bytes of data.
64 bytes from ey-in-f99.1e100.net (74.125.79.99): icmp_req=1 ttl=53 time=46.9 ms
64 bytes from ey-in-f99.1e100.net (74.125.79.99): icmp_req=2 ttl=50 time=46.9 ms
64 bytes from ey-in-f99.1e100.net (74.125.79.99): icmp_req=3 ttl=50 time=48.3 ms
64 bytes from ey-in-f99.1e100.net (74.125.79.99): icmp_req=4 ttl=53 time=46.2 ms
64 bytes from ey-in-f99.1e100.net (74.125.79.99): icmp_req=5 ttl=53 time=47.6 ms

--- www.l.google.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4005ms
rtt min/avg/max/mdev = 46.258/47.248/48.348/0.707 ms

```Now, is that a good tip or what?
I hope you sort your problem.

---

### Post by maggle66 on 2011-06-28
> **maggle66 said:**
> A bit further info. 
 
Testing today after a few reboots now manages to get some info from the Internet so DNS seems to be fine. I am getting a lot of packet loss though, see below.
 
ping [www.google.com]("http://www.google.com")
PING [www.l.google.com]("http://www.l.google.com") (209.85.147.103) 56(84) bytes of data.
64 bytes from bru01m01-in-f103.1e100.net (209.85.147.103): icmp_req=11 ttl=49 time=28.8 ms
64 bytes from 209.85.147.103: icmp_req=13 ttl=49 time=29.4 ms
64 bytes from 209.85.147.103: icmp_req=14 ttl=49 time=29.2 ms
^C64 bytes from 209.85.147.103: icmp_req=15 ttl=49 time=29.1 ms
--- [www.l.google.com]("http://www.l.google.com") ping statistics ---
15 packets transmitted, 4 received, 73% packet loss, time 46234ms
rtt min/avg/max/mdev = 28.882/29.160/29.407/0.226 ms
 
 
Still unable to successfully connect to the Internet, any ideas anyone?

---

### Post by shymega on 2011-06-28
Can you connect to the internet via an Ethernet cable (wired connection)?

Also, maybe you can try moving closer to the router?

---

### Post by maggle66 on 2011-06-29
> **shymega said:**
> Can you connect to the internet via an Ethernet cable (wired connection)?
 
Also, maybe you can try moving closer to the router?
 
Hi, 
 
Yes it works connected via cable. 
The router is close enough with a very strong signal and Windows 7 on the same machine connects and surfs fine.  If it helps the router is the new BT homehub3.
I have an MSI netbook running Jolicloud that works fine on the Internet as well so definitely not a router problem.

---

### Post by shymega on 2011-06-29
Well, I searched for any issues with the BT Home Hub and Ubuntu with dual-boot with Windows and It looks like because your laptop with a dual-boot setup has got the same Media Access Control address (MAC), the home hub might be confused with different computer name trying to connect with the same Media Access Control addresses. My suggestion would be to try to:
1. Press ALT + F2 on your keyboard at the same time.
2. Type into the box on the screen: gnome-terminal and press the enter key.
3. After that, type into the terminal: "sudo gedit /etc/network/interfaces" (without the speech marks) 
4. If you scroll down the list until you find a line saying something like this: "iface wlan0 inet" (there should be something after the inet part of the line)
5. Start a new line after the "iface wlan0 inet" line.
6. Then type into this new line: "hwaddress ether b4:74:9f:71:4b:34" (That is your old Media Access Control address but with the last digit increased by 1.
7. Then save and close the file.
8. Then reboot your computer.
That should let you connect to the internet. Just a thought.

---

