---
title: "Internet Connection Issues"
date: 2012-01-12
forum: General Help
---

### Post by nakinaw on 2012-01-12
Hey all, 

I am having an issue with a desktop that I have dedicated to Ubuntu.  The desktop is older and I had it stored away for a while and now I am trying to set it up for my oldest daughter.  I am having an issue connecting to the internet with it though and I cant seem to figure it out.  I was reading some other posts and they had asked the OP to input a couple commands.  I went ahead and did that ahead of time to hopefully speed the process.  I really dont know what to look for in all this information though.  Any help would be greatly appreciated.  Here is what I get;

**nakinaw@Stephen-E-2000:~$ sudo iwconfig**
[sudo] password for nakinaw:
lo        no wireless extentions.

eth1      no wireless extensions

**nakinaw@Stephen-E-2000:~$ sudo lspci**
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 828456G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
oo:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
oo:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
oo:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
oo:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
oo:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

I hope that makes sense to someone.  I have no idea what that means.  Again, thank you in advance for any help.

Nakinaw

---

### Post by nakinaw on 2012-01-12
I did some more reading and it looks like its useful if I add a few more bits of information.  Here are a few more commands that I found;

**nakinaw@Stephen-E-2000:~$ cat /etc/lsb-release; uname -a**
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"
Linux Stephen-E-2000 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686 GNU/Linux

**nakinaw@Stephen-E-2000:~$ lspci -nnk | grep -iA2 net**
02:02.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C /8139C+ [10ec:8139] (rev 10)
 
**nakinaw@Stephen-E-2000:~$ sudo lsmod**
Module                  Size       Used by
pppoe                   9015       0
pppox                   2054       1 pppoe
aes_i586                7280       91
aes_generic            26875       1 aes_i586
binfmt_misc             6599       1
dm_crypt               11385       0
snd_intel8x0           25632       2
snd_ac97_codec         99227       1 snd_intel8x0
ac97_bus                1014       1 snd_ac97_codec
snd_pcm                71475       2 snd_intel8x0,snd_ac97_codec
snd_seq_midi            4588       0
snd_rawmidi            17783       1 snd_seq_midi
snd_seq_midi_event      6047       1 snd_seq_midi
snd_seq                47174       2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067       2 snd_pcm,snd_seq
ppdev                   5556       0
snd_seq_device          5744       3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    49006       11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             26058       1
psmouse                59033       0
soundcore                880       1 snd
serio_raw               4022       0
snd_page_alloc          7120       2 snd_intel8x0,snd_pcm
shpchp                 29886       0
lp                      7342       0
parport                31492       3 ppdev,parport_pc,lp
i915                  290938       2
drm_kms_helper         30200       1 i915
drm                   168054       2 i915,drm_kms_helper
8139too                19581       0
intel_agp              26360       2 i915
8139cp                 16934       0
mii                     4425       2 8139too,8139cp
floppy                 54311       0
i2c_algo_bit            5168       1 i915
video                  18712       1 i915
agpgart                32011       2 drm,intel_agp
output                  1883       1 video

---

### Post by spacecheck on 2012-01-12
Is Networking enabled?
Click the Network icon and see if thre is a check mark by "Networking enabled".
Do you have the PC set to connect automatically?
Go to : Settings, Network Connections, Wired Connection 1
and mark the connection & click "Edit" and put a check in the box for that.
Is is set to pull a IP address per DHCP from a provider or the DSL/cable modem or router?
Can you ping the address of the router? IF DSL/Cable modem, does the signal lamp shine for Internet? Does the LED shine to show LAN activity?
Does the LED for the Network card light up and blink?
Is the cable properly seated in the socket and have you tried different cables?

If any of these questions cum suggestions resolve the problem, be sure to use the thread tools to mark the thread Solved. If not report back for more input.

Good luck!

---

### Post by nakinaw on 2012-01-12
What I end up with when I click on the connection at the top right is: Disconnect, Auto Ethernet and VPN Connections.  There is no Wired Connection 1.  How do I go about setting up the connection to pull the IP address per DHCP from the modem?  What does it mean to ping the address of the router?  The LED's are both glowing and I am pretty sure I can connect to the network, but I cant get onto the internet.  I had it connected to where the two arrows that 
point away from eachother were visible, but I still could not access the internet.

Nakinaw

---

### Post by imachavel on 2012-01-12
you are connected to an internal network? that is what it looks like you are saying. you are connected to an internal network, and you have internet access wireless but can't connect to your dhcp server through a hard wired router. Is this right?

---

### Post by spacecheck on 2012-01-12
When "Disconnect" is visible, that means you are connected to something.

When you click that icon, you should see an entry for "Connection Information" and that should tell you which connection, if any, is active and for how long.

From that icon, you should also be able to "Edit connections" and you would select the active connection to view/modify its settings.

You can also open the terminal and enter:
 
 ifconfig
 
Does it show you have an IP address?

BTW, are you connecting per DSL or cable modem? For some connections providers require access daa (account/user, password). Does your provider require these? If so, have you entered this data?

IF you have entered such data, you may get access to the provider. Are you getting access to the provider's website? If so, you may need to look for the provider's DNS server addresses, so you can enter these into the Connection information.

---

### Post by nakinaw on 2012-01-12
Heres what I get when I type ifconfig in the terminal;
eth1    Link encap:Ethernet HWaddr 00:40:2b:6f:d3:16
        inet6 addr: fe80::240:2bff:fe6f:d316/64 Scope:Link
        UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
        RX packets:0 errors:1856 dropped:0 overruns:0 frame:0
        TX packets:198 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:1000
        RX Bytes:0 (0.0 B) TX bytes:46234 (46.2 KB)
        Interrupt:17 Base Address:0x2000

lo      Link encap:Local Lopback
        inet addr:127.0.0.1 Mask:255.0.0.0
        inet6 addr: ::1/128 Scope:Host
        UP LOOPBACK RUNNING MTU:16436 Metric:1
        RX packets:460 errors:0 dropped:0 overruns:0 frame:0
        TX packets:460 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:0
        RX bytes35184 (35.1 KB) TX bytes:35184 (35.1 KB)

I again have no clue what that means, hopefully one of you guys can make sense of that.

Nakinaw

---

### Post by spacecheck on 2012-01-12
The first section means you are not receiving any data nor an IP address from the provider. The second sections mean the laptop sent itself data and the data was received, indicating the card is actively transmitting (TX) and receiving (RX).

What about some answers to my other questions?

---

### Post by sailor2001 on 2012-01-12
your ethernet card might be the problem. You can purchase a usb ethernet dongle cheap ($18-$24) at your local local computer store, (hanging on the rack) Those listed as BLUE TOOTH are the same...

---

### Post by sailor2001 on 2012-01-12
your ethernet card (wlan) might be the problem. You can purchase a usb ethernet dongle cheap ($18-$24) at your local local computer store, (hanging on the rack) Those listed as BLUE TOOTH are the same...

---

### Post by nakinaw on 2012-01-12
*"When "Disconnect" is visible, that means you are connected to something."*

The disconnect is not visible.

*"When you click that icon, you should see an entry for "Connection Information" and that should tell you which connection, if any, is active and for how long."*

The only thing that shows up is Auto Ethernet and that is under "Available" Networks.
 
[I]"From that icon, you should also be able to "Edit connections" and you would select the active connection to view/modify its settings.

BTW, are you connecting per DSL or cable modem? For some connections providers require access daa (account/user, password). Does your provider require these? If so, have you entered this data?"[/I]

It is a wireless modem with DSL capabilities.  I would/have entered the information from my ISP, but I am unsure if I did it correctly.  That may me part of my problem.

*"IF you have entered such data, you may get access to the provider. Are you getting access to the provider's website?"*

I am not able to access anything online.

---

### Post by spacecheck on 2012-01-13
So, are you trying to connect to the "wireless modem with DSL capabilities" per cable or per wireless?
IF per wireless, you should be selecting "Available Networks".
Have you clicked on that and, if so, do you see ANY available networks?
Is the device you are using to post these messages attached to the same "wireless modem with DSL capabilities"?
If so, you would need to select the same available network name, and enter the same secret WPA/WPA2 key you use for this connection into the other PC, in order for it to access the same "wireless modem with DSL capabilities".

Good luck!

---

### Post by nakinaw on 2012-01-14
Hey all, 

I appreciate all of your help, but I just decided to install Mint instead.  I have the internet working now and all is good.

---

