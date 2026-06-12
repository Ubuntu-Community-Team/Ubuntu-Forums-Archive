---
title: "Massive Help needed"
date: 2010-02-21
forum: General Help
---

### Post by uMany on 2010-02-21
Hi everyone,

I'm a total newbie in Linux in general and Ubuntu in particular, I came from OS X and I know some basic Unix and Terminal but I intend to switch to this wonderful softwarecology that is Ubuntu.
So I bought a new laptop Sony Vaio model VPCF111FD i7 intel and installed Ubuntu Karmic Koala 9.10.
Ununtu is working fine but there is a series of things that simple does not work, here is the list:
No wireless (I fix it reading this forum, so THANKS to all of you)
No sound at all (I've been trying to solve it more than a week with no results at all)
No webcam
No firewire port

Here is other list of the things I don't know yet if they work because lack of equipment
I have no way to try (yet) the HDMI port
I have no way to try (yet) the eSATA port
I have no way to try (yet) the ExpressCard port

Everything else seems to work as it should.
I can play BlueRay discs but no sound.

I unistalled PulseAudio and replaced with esound daemon but now I the sound option under System>Preferences don't even open.

Here is the lspci -v output
00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
    Subsystem: Sony Corporation Device 9067
    Flags: fast devsel
    Capabilities: <access denied>

00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: d0000000-e30fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
    Subsystem: Device 004d:0067
    Flags: fast devsel
    Capabilities: <access denied>

00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
    Subsystem: Device 004d:0067
    Flags: fast devsel
    Capabilities: <access denied>

00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
    Subsystem: Device 004d:0067
    Flags: fast devsel
    Capabilities: <access denied>

00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
    Subsystem: Device 004d:0067
    Flags: fast devsel

00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
    Subsystem: Device 004d:0067
    Flags: fast devsel

00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
    Subsystem: Device 004d:0067
    Flags: fast devsel

00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20)
    Subsystem: Sony Corporation Device 9067
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at e8e08000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
    Subsystem: Sony Corporation Device 9067
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at e8e00000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: e7a00000-e8dfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000b000-0000bfff
    Memory behind bridge: e6600000-e79fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 0000a000-0000afff
    Memory behind bridge: e5200000-e65fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=0c, sec-latency=0
    I/O behind bridge: 00009000-00009fff
    Memory behind bridge: e3200000-e51fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20)
    Subsystem: Sony Corporation Device 9067
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at e8e07000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0d, subordinate=0d, sec-latency=32
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
    Subsystem: Sony Corporation Device 9067
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>

00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 05) (prog-if 01)
    Subsystem: Sony Corporation Device 9067
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 34
    I/O ports at e070 [size=8]
    I/O ports at e060 [size=4]
    I/O ports at e050 [size=8]
    I/O ports at e040 [size=4]
    I/O ports at e020 [size=32]
    Memory at e8e06000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
    Subsystem: Sony Corporation Device 9067
    Flags: medium devsel, IRQ 4
    Memory at e8e05000 (64-bit, non-prefetchable) [size=256]
    I/O ports at e000 [size=32]
    Kernel modules: i2c-i801

01:00.0 VGA compatible controller: nVidia Corporation Device 0a75 (rev a2)
    Subsystem: Sony Corporation Device 9067
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at e2000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at e0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at d000 [size=128]
    Expansion ROM at e3000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel modules: nvidiafb

01:00.1 Audio device: nVidia Corporation Device 0be3 (rev a1)
    Subsystem: Sony Corporation Device 9067
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at e3080000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>

02:00.0 Network controller: Atheros Communications Inc. Device 002e (rev 01)
    Subsystem: Foxconn International, Inc. Device e030
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at e7a00000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath9k
    Kernel modules: ath9k

03:00.0 SD Host controller: Ricoh Co Ltd Device e822
    Subsystem: Sony Corporation Device 9067
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at e6603000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

03:00.1 System peripheral: Ricoh Co Ltd Device e230
    Subsystem: Sony Corporation Device 9067
    Flags: bus master, fast devsel, latency 0, IRQ 4
    Memory at e6602000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>

03:00.3 FireWire (IEEE 1394): Ricoh Co Ltd Device e832 (prog-if 10)
    Subsystem: Sony Corporation Device 9067
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at e6601000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

03:00.4 SD Host controller: Ricoh Co Ltd Device e822
    Subsystem: Sony Corporation Device 9067
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at e6600000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

04:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 4380 (rev 10)
    Subsystem: Sony Corporation Device 9067
    Flags: bus master, fast devsel, latency 0, IRQ 35
    Memory at e5220000 (64-bit, non-prefetchable) [size=16K]
    I/O ports at a000 [size=256]
    Expansion ROM at e5200000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: sky2
    Kernel modules: sky2

3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers (rev 04)
    Subsystem: Sony Corporation Device 9067
    Flags: bus master, fast devsel, latency 0

3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 04)
    Subsystem: Sony Corporation Device 9067
    Flags: bus master, fast devsel, latency 0

3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 04)
    Subsystem: Sony Corporation Device 9067
    Flags: bus master, fast devsel, latency 0

3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 04)
    Subsystem: Sony Corporation Device 9067
    Flags: bus master, fast devsel, latency 0

3f:03.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller (rev 04)
    Subsystem: Sony Corporation Device 9067
    Flags: bus master, fast devsel, latency 0

3f:03.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder (rev 04)
    Subsystem: Sony Corporation Device 9067
    Flags: bus master, fast devsel, latency 0

3f:03.4 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Test Registers (rev 04)
    Subsystem: Sony Corporation Device 9067
    Flags: bus master, fast devsel, latency 0

3f:04.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers (rev 04)
    Subsystem: Sony Corporation Device 9067
    Flags: bus master, fast devsel, latency 0

3f:04.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers (rev 04)
    Subsystem: Sony Corporation Device 9067
    Flags: bus master, fast devsel, latency 0

3f:04.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers (rev 04)
    Subsystem: Sony Corporation Device 9067
    Flags: bus master, fast devsel, latency 0

3f:04.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers (rev 04)
    Subsystem: Sony Corporation Device 9067
    Flags: bus master, fast devsel, latency 0

3f:05.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers (rev 04)
    Subsystem: Sony Corporation Device 9067
    Flags: bus master, fast devsel, latency 0

3f:05.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers (rev 04)
    Subsystem: Sony Corporation Device 9067
    Flags: bus master, fast devsel, latency 0

3f:05.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers (rev 04)
    Subsystem: Sony Corporation Device 9067
    Flags: bus master, fast devsel, latency 0

3f:05.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers (rev 04)
    Subsystem: Sony Corporation Device 9067
    Flags: bus master, fast devsel, latency 0

Thanks in advance for your help

---

### Post by lidex on 2010-02-21
Right-click the alsa-info link in my sig and "save as" to your user directory. Then run this command in a terminal (Applications>Accessories>Terminal):
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide the link to the uploaded file here.

---

### Post by uMany on 2010-02-21
Hi lidex, thanks for your help.
Here is the url:
[http://www.alsa-project.org/db/?f=35d9a02b6c52fa86d99856ad93c1a4988c3b1f71](http://www.alsa-project.org/db/?f=35d9a02b6c52fa86d99856ad93c1a4988c3b1f71)

---

### Post by lidex on 2010-02-21
Firstly, you have no sound server running. Removing pulse audio is not something I would recommend until all else has failed. I suggest you re-install it. Not sure of all the packages but this command should do the trick:
```
sudo apt-get install ubuntu-desktop
```

Once done, reboot, then go here and follow guide for Karmic:
[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")

---

### Post by mr clark25 on 2010-02-21
1.is there anything under "recommended drivers"? you will need to have internet if you want to install any of them.

2.did you test for audio without pulseaudio or esound? i have neither right now, and it works.

---

### Post by uMany on 2010-02-22
Hi,

I uninstalled esound, reinstalled pulseaudio and here is my ALSA information:
[http://www.alsa-project.org/db/?f=7f163793f28ad84e50b08dbfd578d9dbdcdce4ee](http://www.alsa-project.org/db/?f=7f163793f28ad84e50b08dbfd578d9dbdcdce4ee)

Still no sound at all but now the sound preferences is working

Any help is appreciated

Thanks

---

### Post by lidex on 2010-02-22
Very good. So you followed the pulseaudio thread, checked your mixer levels, selected default sound card, etc? Next step is upgrading alsa. You can click the alsa-upgrade link in my signature.

---

### Post by uMany on 2010-02-23
lidex:
Fantastic! it worked nicely, I have sound now. I'll study PulseAudio to exploit (try) all its features.
You are the best!

For now only rest to get the webcam working. If you can point me some threat I will be much more grateful

Thanks

---

### Post by Gionux on 2010-02-27
Hey uMany. I have the same laptop as you (Sony vpcf111fd) and I've been looking for a solution to the wireless problem. Could you tell me how you got ubuntu to detect your wireless card please?

---

### Post by uMany on 2010-02-27
Sure!
Gionux, I followed the instructions posted by [2hot6ft2]("http://ubuntuforums.org/member.php?u=568708") here:

[http://ubuntuforums.org/showthread.php?t=1309605&highlight=atheros+](http://ubuntuforums.org/showthread.php?t=1309605&highlight=atheros+)[SOLVED]&page=2

when you get to the installation of the linux-backports you can do it using the System>Administration>Synaptic Package Manager if you want

Hope you can do it.

Still I have no webcam on skype or any other application althoug I get to use it installing Cheese webcam Booth. So it works but not with skype and that is the main use I want it do it... for me a minor issue but I'll appreciate if you can point me to a solution.

---

### Post by Gionux on 2010-02-27
Hey uMany!

Thanks for the link, but it doesn't send me to any page where 2hot6ft2 has replied to anything :-\.

---

### Post by uMany on 2010-02-27
> **Gionux said:**
> Hey uMany!

Thanks for the link, but it doesn't send me to any page where 2hot6ft2 has replied to anything :-\.
Don't worry,
Here you have it again:
[http://ubuntuforums.org/showthread.php?t=1309605&highlight=atheros&page=2](http://ubuntuforums.org/showthread.php?t=1309605&highlight=atheros&page=2)

---

