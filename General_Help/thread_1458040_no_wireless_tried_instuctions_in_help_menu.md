---
title: "no wireless: tried instuctions in help menu"
date: 2010-04-19
forum: General Help
---

### Post by jadu on 2010-04-19
hi, I have Ubuntu 9.10. I woke up today and the internet doesn't work.

When I right click on the wireless icon (the four bars, which are empty and have an X by them now). I click information about the connection, and it says "no active valid connection found" (or something like that, it's in spanish).
I right clic and clic "edit connections" and it shows me five tabs: cabled, wireless, broad band, vpn, and dsl. The wireless tab is empty, there are no connections.

I looked at ubuntu help, and it says to put this in terminal:
> sudo lshw -C network

and that it should say either "CLAIMED, UNCLAIMED, ENABLED or DISABLED"

but instead it says, really fast, 
CPUID
PCI (sysfs)
(and something else too fast to read)

I put in another series of commands to the terminal to give information-- I read these on another post, that they're necessary for someone (you! I hope) to tell me what's wrong and how to fix it.

(I got these results by copying them and putting them on a USB, obviously)

any ideas would be welcome!!
(in non technical language if possible, I don't know much about computers, though I'm learning!)



lspci
SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP61 SMU (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6150SE nForce 430] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control


lsmod
çModule                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
snd_hda_codec_realtek   203328  1 
xt_limit                2176  1 
xt_tcpudp               2780  7 
xt_state                1820  6 
ipt_addrtype            2204  4 
ip6table_filter         3164  1 
ip6_tables             13004  1 ip6table_filter
nf_nat_irc              2012  0 
nf_conntrack_irc        4992  1 nf_nat_irc
nf_nat_ftp              2652  0 
nf_nat                 18096  2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4      13352  8 nf_nat
nf_defrag_ipv4          1756  1 nf_conntrack_ipv4
nf_conntrack_ftp        6880  1 nf_nat_ftp
nf_conntrack           67484  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter          3100  1 
ip_tables              11692  1 iptable_filter
x_tables               16544  6 xt_limit,xt_tcpudp,xt_state,ipt_addrtype,ip6_tables,ip_tables
lp                      8964  0 
parport                35340  2 ppdev,lp
psmouse                56500  0 
serio_raw               5280  0 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
nvidia               9586440  36 
agpgart                34988  1 nvidia
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
k8temp                  4188  0 
snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
i2c_nforce2             6784  0 
usb_storage            52768  0 
floppy                 54916  0 
forcedeth              54152  0 

-------
uname -a
Linux ipo2 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux
---

ifconfig     
eth0      Link encap:Ethernet  direcciónHW 00:1d:92:f3:6b:bd  
          Direc. inet:192.168.0.3  Difus.:192.168.0.255  Másc:255.255.255.0
          Dirección inet6: fe80::21d:92ff:fef3:6bbd/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:1050 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:300 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:132881 (132.8 KB)  TX bytes:31911 (31.9 KB)
          Interrupción:27 Dirección base: 0xe000 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO LOOPBACK FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:40 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:40 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:4154 (4.1 KB)  TX bytes:4154 (4.1 KB)
-------------
 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by _0R10N on 2010-04-19
If you're dealing with a fresh installation, I extremely recommend you to update your system. I went through the same problem, and that actually worked!...

Kind regards!

_0R10N >>

---

### Post by jadu on 2010-04-19
thanks for the response. I upgraded to ubuntu 9.10 a month ago, but it seemed that the internet was working fine. and I have been doing routine system updates. I can't update again now, because I don't have internet connection to do it.

---

### Post by _0R10N on 2010-04-19
Well, it seems like you're getting a valid IP address (192.168.0.3). Ping your router, maybe there's a problem there. 

Is there another PC in your home network?

Please, post the content of your /etc/network/interfaces file.

Kind regards!

_0R10N >>

---

### Post by jadu on 2010-04-19
hi,
I pinged the router, and it came back that 100% of packets were successfull
I didn't know what the "interfaces" was, but I found a gedit document called interfaces in the /etc/network folders, I assume that's what you mean? It says

auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.0.3
netmask 255.255.255.0
gateway 192.168.0.1

auto eth0


it's swedish to me! mean anything to you?

---

### Post by Iowan on 2010-04-19
If you use the Applications>Accessories>Terminal, you should be able to scroll back to see what **sudo lshw -C network** has printed (or you can dump it to a file):```
sudo lshw -C network > hardware.txt
``` Have you tried using Network Manager to configure eth0 as well as the wireless?  It appears that only eth0 has an address.

---

### Post by jadu on 2010-04-20
I entered the command 
> sudo lshw -C network > hardware.txt

in terminal. But when I scroll back, to try to see the results, it just shows me previous comands. I'm afraid I don't know how to dump it into a file.

I haven't tried configuring the network manager, I looked at it some (if you see my first post) but didn't know how to do it.

---

### Post by P4man on 2010-04-20
> **jadu said:**
> I entered the command 


in terminal. But when I scroll back, to try to see the results, it just shows me previous comands. I'm afraid I don't know how to dump it into a file.

You already did :). The command you typed redirected the output to a textfile called *hardware.txt*, and the idea is you attach that file to your post here, or upload it somewhere.

Anyway, im slightly confused about what we are looking at. Eth0 is clearly connected, do you have a network cable plugged in? I do not see a wireless connection (unless that would be eth0), which might mean the radio is turned off. Does your laptop have a button to enable/disable wifi?

---

### Post by jadu on 2010-04-20
thanks for continuing to work with me on this.
I kind of thought that might be the case-- that I had already sent the results to a text file. But just now, when I search in file system for "hardware.txt", I found the document, but it's zero bytes and has nothing in it!
We have a network cable that used to be used as a network between this computer and another, but we had problems and stopped using it. So the computer I'm working on was just using the wireless. I know it's working because other computers here are working fine with the wireless. The computer I'm working on isn't a laptop, it's a desktop. I don't know if it has an off button for the wireless, but I looked and didn't see anything.

---

### Post by P4man on 2010-04-20
To clarify, the output you posted on your initial post, was made on that computer, with no ethernet cable connected? Im asking because it shows a (apparently working) network connection on "eth0", which usually refers to a wired network connection, not a wireless one.

More questions: is this an USB device? I see no wireless cards in your lspci output. If its a USB device, please provide the output of

```
lsusb

```

(LSUSB in lowercase) and copy/paste or type the relevant lines referring to the wireless network controllers.

Next question: did you try installing a windows driver using NDIS wrapper (also known as "windows wireless drivers". It looks like this:[http://quilombo.files.wordpress.com/2008/03/pantallazo-wireless-network-drivers.png](http://quilombo.files.wordpress.com/2008/03/pantallazo-wireless-network-drivers.png)) ? Im asking this because ndiswrapper I think creates a eth0 even for wireless, which would help explain a bit. Ndiswrapper might be a last resort to get this working, but lets see if we cant get it up with a native linux driver first.

---

### Post by jadu on 2010-04-20
Yes, the output on my first post was on that computer. But with the ethernet cable connected. The thing is, the ethernet cable has been connected but kind of forgotten on that computer, the internet was (I think) through wireless. though I guess we could use the cable instead, right? But it's strange that the wireless stopped working.
It's not a USB device.
And I haven't tried installing a windows driver using NDIS wrapper.

---

### Post by P4man on 2010-04-20
If its an internal card, then its not showing up in lspci, which points to the hardware simply not being installed or working. Try opening the pc and reseat the card, or move it to another slot. If you have windows on that machine, does it work on windows?

If its not a card, but something on the motherboard, then go in to your bios and make sure its enabled there. At this point, I dont think its an ubuntu problem.

---

### Post by jadu on 2010-04-20
thanks to all who helped us out. It's working again now.
We tried opening the computer to find the card, but (said my friends who know a little more) it's not a card, but on the motherboard.
I entered BIOS (after finding out what it is online!) but didn't see anything about wireless.
Then another friend tried. He opened network connections, and chose the ethernet connection, edit, IPv4 adjustment. he changed it to "share with others". And now it works. Don't know if it was what he did, or what. But thanks again for your advice. at least I learned a few things in the process!

---

