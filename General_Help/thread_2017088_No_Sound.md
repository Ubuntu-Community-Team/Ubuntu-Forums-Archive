---
title: "No Sound"
date: 2012-07-04
forum: General Help
---

### Post by SlasherIT on 2012-07-04
Hello,

I'm running a fresh install of Ubuntu 12.04 on my laptop, which is a HP Pavilion dv6-2020ev, has a Intel Core i7-720QM, NVIDIA GeForce GT230M, ect. Everything works great except that I can't get sound to work at all from the speakers. Haven't tested headphones or earphones or anything like that. And I think that sound did work from the Live CD. Help would be appreciated. Thanks.

---

### Post by msammels on 2012-07-04
OK. If you click the sound icon in the top right, then click on sound settings, make sure the output device is set to the correct one, it's unmuted and turned up. This should fix your issue.

---

### Post by SlasherIT on 2012-07-04
Already did that, didn't work. Its not muted, and its at 100%. Tested sound, no go :(.

---

### Post by msammels on 2012-07-04
Relax. Open Terminal and try this:

```
sudo alsamixer
```

Press M to mute/unmute it,and make sure all outputs are up full.

---

### Post by SlasherIT on 2012-07-04
I'm chill :). Um, I also did that before lol, all bars are full. Still not working.

---

### Post by jmfal on 2012-07-04
Run this in a terminal

```
 lspci -v   
```

And post the output of your sound card

---

### Post by SlasherIT on 2012-07-04
naimchahine@Slasher:~$  lspci -v
00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
	Subsystem: Hewlett-Packard Company Device 363e
	Flags: fast devsel
	Capabilities: <access denied>

00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00006000-00006fff
	Memory behind bridge: d2000000-d30fffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000d1ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
	Subsystem: Device 003c:003e
	Flags: fast devsel
	Capabilities: <access denied>

00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
	Subsystem: Device 003c:003e
	Flags: fast devsel
	Capabilities: <access denied>

00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
	Subsystem: Device 003c:003e
	Flags: fast devsel
	Capabilities: <access denied>

00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
	Subsystem: Device 003c:003e
	Flags: fast devsel

00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
	Flags: fast devsel

00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
	Flags: fast devsel

00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Device 363e
	Flags: bus master, medium devsel, latency 0, IRQ 16
	Memory at db105c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
	Subsystem: Hewlett-Packard Company Device 363e
	Flags: bus master, fast devsel, latency 0, IRQ 47
	Memory at db100000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: da100000-db0fffff
	Prefetchable memory behind bridge: 00000000d3100000-00000000d40fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: d9100000-da0fffff
	Prefetchable memory behind bridge: 00000000d4100000-00000000d50fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: d8100000-d90fffff
	Prefetchable memory behind bridge: 00000000d5100000-00000000d60fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.7 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 8 (rev 05) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=08, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: d7100000-d80fffff
	Prefetchable memory behind bridge: 00000000d6100000-00000000d70fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Device 363e
	Flags: bus master, medium devsel, latency 0, IRQ 21
	Memory at db105800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=32
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
	Subsystem: Hewlett-Packard Company Device 363e
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 05) (prog-if 01 [AHCI 1.0])
	Subsystem: Hewlett-Packard Company Device 363e
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 45
	I/O ports at 7048 [size=8]
	I/O ports at 7054 [size=4]
	I/O ports at 7040 [size=8]
	I/O ports at 7050 [size=4]
	I/O ports at 7020 [size=32]
	Memory at db105000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
	Subsystem: Hewlett-Packard Company Device 363e
	Flags: medium devsel, IRQ 5
	Memory at db106000 (64-bit, non-prefetchable) [size=256]
	I/O ports at 7000 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller: NVIDIA Corporation GT216 [GeForce GT 230M] (rev a2) (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Device 363e
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d2000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at d0000000 (64-bit, prefetchable) [size=32M]
	I/O ports at 6000 [size=128]
	[virtual] Expansion ROM at d3080000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia_current, nouveau, nvidiafb

01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
	Subsystem: Hewlett-Packard Company Device 363e
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d3000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

02:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
	Subsystem: Hewlett-Packard Company Device 3042
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at da100000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath9k
	Kernel modules: ath9k

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 363e
	Flags: bus master, fast devsel, latency 0, IRQ 46
	I/O ports at 4000 [size=256]
	Memory at d4104000 (64-bit, prefetchable) [size=4K]
	Memory at d4100000 (64-bit, prefetchable) [size=16K]
	Expansion ROM at d4110000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

04:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Device 363e
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d8100000 (32-bit, non-prefetchable) [size=2K]
	Memory at d8100d00 (32-bit, non-prefetchable) [size=128]
	Memory at d8100c80 (32-bit, non-prefetchable) [size=128]
	Memory at d8100c00 (32-bit, non-prefetchable) [size=128]
	Capabilities: <access denied>
	Kernel driver in use: firewire_ohci
	Kernel modules: firewire-ohci

04:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
	Subsystem: Hewlett-Packard Company Device 363e
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d8100b00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

04:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (prog-if 01)
	Subsystem: Hewlett-Packard Company Device 363e
	Flags: fast devsel, IRQ 16
	Memory at d8100a00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel modules: sdhci-pci

04:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
	Subsystem: Hewlett-Packard Company Device 363e
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d8100900 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: jmb38x_ms
	Kernel modules: jmb38x_ms

04:00.4 System peripheral: JMicron Technology Corp. xD Host Controller
	Subsystem: Hewlett-Packard Company Device 363e
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at d8100800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers (rev 04)
	Subsystem: Hewlett-Packard Company Device 363e
	Flags: bus master, fast devsel, latency 0

ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 04)
	Subsystem: Hewlett-Packard Company Device 363e
	Flags: bus master, fast devsel, latency 0

ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 04)
	Subsystem: Hewlett-Packard Company Device 363e
	Flags: bus master, fast devsel, latency 0
	Kernel modules: i7core_edac

ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 04)
	Subsystem: Hewlett-Packard Company Device 363e
	Flags: bus master, fast devsel, latency 0

ff:03.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller (rev 04)
	Subsystem: Hewlett-Packard Company Device 363e
	Flags: bus master, fast devsel, latency 0

ff:03.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder (rev 04)
	Subsystem: Hewlett-Packard Company Device 363e
	Flags: bus master, fast devsel, latency 0

ff:03.4 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Test Registers (rev 04)
	Subsystem: Hewlett-Packard Company Device 363e
	Flags: bus master, fast devsel, latency 0

ff:04.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers (rev 04)
	Subsystem: Hewlett-Packard Company Device 363e
	Flags: bus master, fast devsel, latency 0

ff:04.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers (rev 04)
	Subsystem: Hewlett-Packard Company Device 363e
	Flags: bus master, fast devsel, latency 0

ff:04.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers (rev 04)
	Subsystem: Hewlett-Packard Company Device 363e
	Flags: bus master, fast devsel, latency 0

ff:04.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers (rev 04)
	Subsystem: Hewlett-Packard Company Device 363e
	Flags: bus master, fast devsel, latency 0

ff:05.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers (rev 04)
	Subsystem: Hewlett-Packard Company Device 363e
	Flags: bus master, fast devsel, latency 0

ff:05.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers (rev 04)
	Subsystem: Hewlett-Packard Company Device 363e
	Flags: bus master, fast devsel, latency 0

ff:05.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers (rev 04)
	Subsystem: Hewlett-Packard Company Device 363e
	Flags: bus master, fast devsel, latency 0

ff:05.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers (rev 04)
	Subsystem: Hewlett-Packard Company Device 363e
	Flags: bus master, fast devsel, latency 0

---

### Post by jmfal on 2012-07-04
Try this it should load the sound kernal till you restart or log out

```
 sudo modprobe snd-hda-intel   
```

check again that everything is unmuted,, play some music, try another jack (headphones,etc) just to be sure. 

helped another the other day and found out he had speaker in wrong jack

---

### Post by SlasherIT on 2012-07-04
Didn't work. And I'm using a laptop :). Also, AlsaMixer says this:

Card: HDA Intel
Chip: IDT 92HD75B3X5 

Maybe this helps... Or not.

---

### Post by jmfal on 2012-07-04
Try changing the sound card in the alsamixer and see if they are muted and go to sound settings and  select the analog card.

---

### Post by SlasherIT on 2012-07-04
Both Speakers and Digital don't work, and the NVIDIA Audio in alsamixer is not muted :(. Still not working :(.

---

### Post by msammels on 2012-07-04
nVidia Audio? I thought it was Intel...?

---

### Post by jmfal on 2012-07-04
Are you trying to play a cd if so you have to turn up the cd control in the alsamixer.

Have you tried any of the stickies in the multimedia/video  section of the forum?

Also in the mixer if you use the right arrow navigate and try to go past the last control, there may be more there if pcm is there turn it up.

---

### Post by SlasherIT on 2012-07-04
I think the GPU has it for outputting to TV and other displays, but normally yes it does use the Intel IDT one or whatever that is.

---

### Post by SlasherIT on 2012-07-04
> **jmfal said:**
> Are you trying to play a cd if so you have to turn up the cd control in the alsamixer.

Have you tried any of the stickies in the multimedia/video  section of the forum?

Also in the mixer if you use the right arrow navigate and try to go past the last control, there may be more there if pcm is there turn it up.

Minecraft, Ubuntu system = no sound. The mixers are all topped, still no sound.

---

### Post by jmfal on 2012-07-04
I have to leave, there is a snd-hda-intel sound base thread in the multimedia section by markbuntu, I bumped to the top for you, you can ask question there.

Sorry I can't help you further

Good Luck

---

### Post by idoitprone on 2012-07-04
> **msammels said:**
> nVidia Audio? I thought it was Intel...?

intel help make the extremely overly complex hd audio standard which will always break our sound

Nvidia just puts out a rebranded card. 

test this first

```
sudo modprobe -r snd-hda-intel

sudo modprobe snd-hda-intel model=hp 
pulseaudio -k
pulseaudio --start
```then it does not work then


op i hope this helps
[https://bbs.archlinux.org/viewtopic.php?pid=1051419#p1051419](https://bbs.archlinux.org/viewtopic.php?pid=1051419#p1051419)



if all that does not work then post the exact card

```
aplay -l
```

---

### Post by SlasherIT on 2012-07-05
Modprobe didn't work.


naimchahine@Slasher:~$ sudo modprobe -r snd-hda-intel
[sudo] password for naimchahine: 
FATAL: Module snd_hda_intel is in use.
naimchahine@Slasher:~$ sudo modprobe snd-hda-intel model=hp 
naimchahine@Slasher:~$ pulseaudio -k
naimchahine@Slasher:~$ pulseaudio --start

Didn't fix it.

The thing from archlinux website didn't work as well.


naimchahine@Slasher:~$ pcm.!default {
bash: !default: event not found
naimchahine@Slasher:~$     type plug
bash: type: plug: not found
naimchahine@Slasher:~$     slave.pcm "swmixer"
slave.pcm: command not found
naimchahine@Slasher:~$     #card Intel
naimchahine@Slasher:~$     #device 0
naimchahine@Slasher:~$ }
bash: syntax error near unexpected token `}'
naimchahine@Slasher:~$ 
naimchahine@Slasher:~$ pcm.swmixer {
pcm.swmixer: command not found
naimchahine@Slasher:~$     type dmix
bash: type: dmix: not found
naimchahine@Slasher:~$     ipc_key 1234
ipc_key: command not found
naimchahine@Slasher:~$     slave {
No command 'slave' found, did you mean:
 Command 'slave1' from package 'pvm-examples' (universe)
 Command 'save' from package 'atfs' (universe)
slave: command not found
naimchahine@Slasher:~$         pcm "hw:0,0"
No command 'pcm' found, but there are 17 similar ones
pcm: command not found
naimchahine@Slasher:~$         period_time 0
period_time: command not found
naimchahine@Slasher:~$         period_size 1024
period_size: command not found
naimchahine@Slasher:~$         buffer_size 4096
buffer_size: command not found
naimchahine@Slasher:~$         rate 44100
No command 'rate' found, did you mean:
 Command 'kate' from package 'kate' (main)
 Command 'rats' from package 'rats' (universe)
 Command 'gate' from package 'libgtkada2-bin' (universe)
 Command 'date' from package 'coreutils' (main)
 Command 'late' from package 'late' (universe)
 Command 'rake' from package 'rake' (main)
 Command 'rdate' from package 'rdate' (main)
 Command 'rat' from package 'rat' (universe)
 Command 'yate' from package 'yate' (universe)
rate: command not found
naimchahine@Slasher:~$     }
bash: syntax error near unexpected token `}'
naimchahine@Slasher:~$ }
bash: syntax error near unexpected token `}'
naimchahine@Slasher:~$ 
naimchahine@Slasher:~$ ctl.swmixer {
ctl.swmixer: command not found
naimchahine@Slasher:~$     type hw
bash: type: hw: not found
naimchahine@Slasher:~$     card 0
The program 'card' is currently not installed.  You can install it by typing:
sudo apt-get install a2ps
naimchahine@Slasher:~$ }sudo apt-get install a2ps
No command '}sudo' found, did you mean:
 Command 'sudo' from package 'sudo' (main)
 Command 'sudo' from package 'sudo-ldap' (universe)
}sudo: command not found
naimchahine@Slasher:~$ sudo apt-get install a2ps
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libqca2 libpolkit-qt-1-1 libqca2-plugin-ossl libfprint0 libfakekey0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  psutils wdiff
Suggested packages:
  emacsen-common groff gv html2ps graphicsmagick-imagemagick-compat
  imagemagick texlive-base-bin t1-cyrillic
The following NEW packages will be installed:
  a2ps psutils wdiff
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,117 kB of archives.
After this operation, 4,983 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) precise/main psutils amd64 1.17-31 [95.3 kB]
Get:2 [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) precise/universe a2ps amd64 1:4.14-1.1 [943 kB]
Get:3 [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) precise/main wdiff amd64 0.6.5-1 [78.8 kB]
Fetched 1,117 kB in 26s (42.0 kB/s)                                            
Selecting previously unselected package psutils.
(Reading database ... 166678 files and directories currently installed.)
Unpacking psutils (from .../psutils_1.17-31_amd64.deb) ...
Selecting previously unselected package a2ps.
Unpacking a2ps (from .../a2ps_1%3a4.14-1.1_amd64.deb) ...
Selecting previously unselected package wdiff.
Unpacking wdiff (from .../wdiff_0.6.5-1_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Setting up psutils (1.17-31) ...
Setting up a2ps (1:4.14-1.1) ...
Setting up wdiff (0.6.5-1) ...
naimchahine@Slasher:~$ pcm.!default {
bash: !default: event not found
naimchahine@Slasher:~$     type plug
bash: type: plug: not found
naimchahine@Slasher:~$     slave.pcm "swmixer"
slave.pcm: command not found
naimchahine@Slasher:~$     #card Intel
naimchahine@Slasher:~$     #device 0
naimchahine@Slasher:~$ }
bash: syntax error near unexpected token `}'
naimchahine@Slasher:~$ 
naimchahine@Slasher:~$ pcm.swmixer {
pcm.swmixer: command not found
naimchahine@Slasher:~$     type dmix
bash: type: dmix: not found
naimchahine@Slasher:~$     ipc_key 1234
ipc_key: command not found
naimchahine@Slasher:~$     slave {
No command 'slave' found, did you mean:
 Command 'slave1' from package 'pvm-examples' (universe)
 Command 'save' from package 'atfs' (universe)
slave: command not found
naimchahine@Slasher:~$         pcm "hw:0,0"
No command 'pcm' found, but there are 17 similar ones
pcm: command not found
naimchahine@Slasher:~$         period_time 0
period_time: command not found
naimchahine@Slasher:~$         period_size 1024
period_size: command not found
naimchahine@Slasher:~$         buffer_size 4096
buffer_size: command not found
naimchahine@Slasher:~$         rate 44100
No command 'rate' found, did you mean:
 Command 'kate' from package 'kate' (main)
 Command 'rats' from package 'rats' (universe)
 Command 'gate' from package 'libgtkada2-bin' (universe)
 Command 'date' from package 'coreutils' (main)
 Command 'late' from package 'late' (universe)
 Command 'rake' from package 'rake' (main)
 Command 'rdate' from package 'rdate' (main)
 Command 'rat' from package 'rat' (universe)
 Command 'yate' from package 'yate' (universe)
rate: command not found
naimchahine@Slasher:~$     }
bash: syntax error near unexpected token `}'
naimchahine@Slasher:~$ }
bash: syntax error near unexpected token `}'
naimchahine@Slasher:~$ 
naimchahine@Slasher:~$ ctl.swmixer {
ctl.swmixer: command not found
naimchahine@Slasher:~$     type hw
bash: type: hw: not found
naimchahine@Slasher:~$     card 0
card: could not find help message for 0

It needed card so I installed that but still not working.

Here's the results from aplay -l:

naimchahine@Slasher:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by idoitprone on 2012-07-05
sighhhhh

i guess i have to do the long step by step process


first method did not work because the sound was in use

the second method did not work because it was not meant to be added to the command line but a file in your home directory call ```
.asoundrc
```

ok let try this again, i guess i will make this easier

```
sudo bash -c 'echo "options snd-hda-intel model=hp" >> /etc/modprobe.d/alsa.conf'
```reboot

if not then 

post the output of this 
```
cat /proc/asound/card0/codec*
```aplay -l is not display the exact card

---

### Post by SlasherIT on 2012-07-05
I tried the modprobe thing in the terminal and then rebooted, but sound still doesn't work.

Here.


naimchahine@Slasher:~$ cat /proc/asound/card0/codec*
Codec: IDT 92HD75B3X5
Address: 0
AFG Function Id: 0x1 (unsol 1)
Vendor Id: 0x111d7603
Subsystem Id: 0x103c363e
Revision Id: 0x100202
No Modem Function Group found
Default PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
Default Amp-Out caps: ofs=0x7f, nsteps=0x7f, stepsize=0x02, mute=1
GPIO: io=8, o=0, i=0, unsolicited=1, wake=1
  IO[0]: enable=1, dir=1, wake=0, sticky=0, data=1, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[3]: enable=1, dir=1, wake=0, sticky=0, data=1, unsol=0
  IO[4]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[5]: enable=1, dir=1, wake=0, sticky=0, data=1, unsol=0
  IO[6]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[7]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Power-Map: 0x07
Analog Loopback: 0x00
Node 0x0a [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x0000001c: OUT HP Detect
  Pin Default 0x40f100f0: [N/A] Other at Ext N/A
    Conn = 1/8, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=03, enabled=1
  Connection: 3
     0x10 0x11 0x17*
Node 0x0b [Pin Complex] wcaps 0x400081: Stereo
  Control: name="Mic Jack Mode", index=0, device=0
    ControlAmp: chs=0, dir=In, idx=0, ofs=0
  Control: name="Mic Jack", index=0, device=0
  Pincap 0x00001724: IN Detect
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x02a11020: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Black
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=02, enabled=1
Node 0x0c [Pin Complex] wcaps 0x400081: Stereo
  Pincap 0x00001724: IN Detect
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x40f000f1: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x1
  Pin-ctls: 0x00: VREF_HIZ
  Unsolicited: tag=00, enabled=0
Node 0x0d [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x00000014: OUT Detect
  Pin Default 0x90170010: [Fixed] Speaker at Int N/A
    Conn = Analog, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=04, enabled=1
  Connection: 3
     0x10 0x11* 0x17
Node 0x0e [Pin Complex] wcaps 0x400081: Stereo
  Pincap 0x00001724: IN Detect
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x40f100f2: [N/A] Other at Ext N/A
    Conn = 1/8, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x2
  Pin-ctls: 0x00: VREF_HIZ
  Unsolicited: tag=00, enabled=0
Node 0x0f [Pin Complex] wcaps 0x400181: Stereo
  Control: name="Front Line-Out Jack", index=0, device=0
  Pincap 0x00000014: OUT Detect
  Pin Default 0x02014040: [Jack] Line Out at Ext Front
    Conn = 1/8, Color = Green
    DefAssociation = 0x4, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=01, enabled=1
  Connection: 3
     0x10* 0x11 0x17
Node 0x10 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
  Control: name="Front Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=63
  Control: name="Front Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="STAC92xx Analog", type="Audio", device=0
  Amp-Out caps: N/A
  Amp-Out vals:  [0x7f 0x7f]
  Converter: stream=0, channel=0
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x11 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
  Control: name="Speaker Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=63
  Control: name="Speaker Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: N/A
  Amp-Out vals:  [0x7f 0x7f]
  Converter: stream=0, channel=0
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x12 [Audio Input] wcaps 0x1d0541: Stereo
  Device: name="STAC92xx Analog", type="Audio", device=0
  Converter: stream=4, channel=0
  SDI-Select: 0
  Power: setting=D3, actual=D3
  Delay: 13 samples
  Connection: 1
     0x1c
  Processing caps: benign=0, ncoeff=0
Node 0x13 [Audio Input] wcaps 0x1d0541: Stereo
  Converter: stream=0, channel=0
  SDI-Select: 0
  Power: setting=D0, actual=D0
  Delay: 13 samples
  Connection: 1
     0x1d
  Processing caps: benign=0, ncoeff=0
Node 0x14 [Pin Complex] wcaps 0x400100: Mono
  Pincap 0x00000030: IN OUT
  Pin Default 0x40f000f0: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Connection: 1
     0x16
Node 0x15 [Audio Selector] wcaps 0x300101: Stereo
  Connection: 3
     0x10 0x11 0x17*
Node 0x16 [Audio Mixer] wcaps 0x200100: Mono
  Connection: 1
     0x15
Node 0x17 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97]
  Connection: 5
     0x10 0x11 0x14 0x1a 0x1b
Node 0x18 [Pin Complex] wcaps 0x40000b: Stereo Amp-In
  Control: name="Internal Mic Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x03 0x03]
  Pincap 0x00000020: IN
  Pin Default 0x90a60350: [Fixed] Mic at Int N/A
    Conn = Digital, Color = Unknown
    DefAssociation = 0x5, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x19 [Pin Complex] wcaps 0x40000b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00000020: IN
  Pin Default 0x40f000f4: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x4
  Pin-ctls: 0x00:
Node 0x1a [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Control: name="Mux Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 3
     0x0b* 0x0c 0x0e
Node 0x1b [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 3
     0x0b* 0x0c 0x0e
Node 0x1c [Audio Selector] wcaps 0x30090d: Stereo Amp-Out R/L
  Control: name="Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Capture Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x0f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x00 0x00]
  Connection: 4
     0x1a 0x17 0x18* 0x19
Node 0x1d [Audio Selector] wcaps 0x30090d: Stereo Amp-Out R/L
  Amp-Out caps: ofs=0x00, nsteps=0x0f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x80 0x80]
  Connection: 4
     0x1b* 0x17 0x18 0x19
Node 0x1e [Pin Complex] wcaps 0x400301: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x024511a0: [Jack] SPDIF Out at Ext Front
    Conn = Optical, Color = Black
    DefAssociation = 0xa, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x24
Node 0x1f [Pin Complex] wcaps 0x400701: Stereo Digital
  Pincap 0x00010010: OUT EAPD
  EAPD 0x0:
  Pin Default 0x40f000f5: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x5
  Pin-ctls: 0x00:
  Power: setting=D0, actual=D0
  Connection: 2
     0x24* 0x25
Node 0x20 [Pin Complex] wcaps 0x400301: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x40f000f0: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Connection: 1
     0x25
Node 0x21 [Audio Output] wcaps 0x40211: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="IEC958 Default PCM Playback Switch", index=0, device=0
  Device: name="STAC92xx Digital", type="SPDIF", device=1
  Converter: stream=8, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Delay: 4 samples
Node 0x22 [Audio Output] wcaps 0x40211: Stereo Digital
  Converter: stream=8, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Delay: 4 samples
Node 0x23 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x24 [Audio Selector] wcaps 0x300101: Stereo
  Connection: 3
     0x21* 0x1c 0x1d
Node 0x25 [Audio Selector] wcaps 0x300101: Stereo
  Connection: 3
     0x22* 0x1c 0x1d
Node 0x26 [Beep Generator Widget] wcaps 0x70000c: Mono Amp-Out
  Control: name="Beep Playback Switch", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Control: name="Beep Playback Volume", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x03, nsteps=0x03, stepsize=0x17, mute=1
  Amp-Out vals:  [0x00]
Node 0x27 [Volume Knob Widget] wcaps 0x600000: Mono
  Volume-Knob: delta=1, steps=127, direct=0, val=127
  Connection: 2
     0x10 0x11

---

### Post by idoitprone on 2012-07-05
> **SlasherIT said:**
> I tried the modprobe thing in the terminal and then rebooted, but sound still doesn't work.

??? what do you mean???

did you run this command?
```
sudo bash -c 'echo "options snd-hda-intel model=hp" >> /etc/modprobe.d/alsa.conf'
```In light of this information

change this command slightly to 


```
sudo bash -c 'echo "options snd-hda-intel model=hp-dv5" >> /etc/modprobe.d/alsa.conf'
```However if you did run it  before, then you have to manually edit alsa.conf and change the model to hp-dv5
```
sudo gedit /etc/modprobe.d/alsa.conf 
```reboot
> naimchahine@Slasher:~$ cat /proc/asound/card0/codec*
Codec: IDT 92HD75B3X5hmm this is your card


if all of that does not work, then remove all the changes i made
```

pcm.!default {
     type plug
     slave.pcm "swmixer"
     #card Intel
     #device 0 
}
pcm.swmixer {
     type dmix
     ipc_key 1234
     slave {
         pcm "hw:0,0"
         period_time 0
         period_size 1024
         buffer_size 4096
         rate 44100
    }
}
ctl.swmixer {
     type hw
     card 0
}
```save all these in a file called```
 .asoundrc 
``` in you home directory.

ex. /home/username
 NOTE: there is a period in front of asoundrc

---

### Post by SlasherIT on 2012-07-05
None of that worked. I put that file in my home directory but it did nothing. What I do now?

---

### Post by SlasherIT on 2012-07-06
Bump.

---

### Post by idoitprone on 2012-07-06
> **SlasherIT said:**
> Bump.

```
cat /etc/modprobe.d/alsa.conf
```

?

did you remove it after you added the asound conf

Your sound card is detected however alsa and hdaudio love throwing curve balls, they have a tendency of always having complex config issues


btw, i hate both hdaudio and alsa stack

---

### Post by SlasherIT on 2012-07-06
Sorry, I'm confused now. How do I remove it?

---

### Post by SlasherIT on 2012-07-08
Bump

---

### Post by idoitprone on 2012-07-08
> **SlasherIT said:**
> Bump

```
sudo rm /etc/modprobe.d/alsa.conf
```

---

### Post by SlasherIT on 2012-07-08
Ok, done. Next?

---

### Post by idoitprone on 2012-07-09
> **SlasherIT said:**
> Ok, done. Next?

if asound and configuring the modules does not work, then i am out of ideas. Fixing alsa was never easy

---

### Post by SlasherIT on 2012-07-15
Well sound still ain't working :(.

---

### Post by jmfal on 2012-07-15
Try thi in a terminal
```
  sudo modprobe snd-     
```

Press and hold down "tab" key and press enter,  enter psswrd >> enter
If error shows, run again,
this will bring up list of drivers existing (should be I found it)
Look for  "IDT' or "idt"
and enter it at end of "sudo modeprobe snd-idt"  as it is listed
Press enter ,, make sure speaker controls are unmuted for that card in alsamixer
Play some music
If you're going to play cd make sure it is not muted in mixer.

---

### Post by jmfal on 2012-07-15
Scrap that last reply and try 

```
 sudo modprobe snd-hda- codec-idt      
```

This should give you sound till you logout or restart

If this works  install nano
```
  sudo apt-get install nano
```

And run this
```
 sudo nano /etc/modules   
```
Press enter, and navigate to end of file using down arrow and add this:
snd-hda-codec-idt

---

### Post by SlasherIT on 2012-08-06
Hello,

after 3 weeks of not touching ubuntu, I booted into it, and ran update manager, which found over 200 updates!! So after the update, which involved an update to the kernel, the sound works again :).

---

### Post by zhanglini on 2012-08-10
what kernel version is that?

I use 3.2.0.29, HDMI audio never worked on my Nvidia...

---

