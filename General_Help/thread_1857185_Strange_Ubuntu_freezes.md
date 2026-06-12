---
title: "Strange Ubuntu freezes"
date: 2011-10-09
forum: General Help
---

### Post by MichaelYammer on 2011-10-09
Hello all.

I will try to include as much information as I can about my problem, but I'm afraid I don't have much in the way of it owning the nature of the problem itself. I don't even know if this is the right place to report this, but if someone points me in the right direction I will post there.

I have a new Toshiba Satellite C665D-S5200. I first installed Ubuntu 10.04 LTS 64-bit version on it, but it didn't recognize my build-in wireless or Ethernet. *sigh* So I ended up downloading Super OS (11.04 64 bit amd) and installing via USB. It installed alright and found all my hardware without a hitch, even the AMD video card. I am dual-booting with Windows 7.

My problem is that Ubuntu has started to outright freeze. The first time was last night. I was playing a game on Facebook using Chrome, and it was a total lock-up. I had to hot-boot my machine. I rebooted into Ubuntu again, went back to Facebook to the game (again using Chrome), and it froze again. I figured it might be Chrome doing it, so I went into Win7 and fished my game then shutdown for the night.

Today I decided to submit a profile using Ubuntu's built-in system testing program. While doing that I was setting up my Ubuntu One account, and again my machine totally froze. Hot-booted and went back into Ubuntu to log into this forum, and when I clicked the link to take me here form the Ubuntu homepage, it froze yet again. :( I wasn't doing anything else at the time.

I have no problems with my laptop using Win7, so I don't think the freezes are hardware related. If they where, I'd return this thing in a heartbeat. It just seems to be Ubuntu. I could re-install of course, but I want to try and trouble shoot the problem first and see if it's a bug with Ubuntu that might as of yet be unknown. This laptop hasn't been on the market for a long time, and I don't think there are many people with my model using Ubuntu.

Here is the webpage including my laptop's specs:
[http://us.toshiba.com/computers/laptops/satellite/C650/C655D-S5200/](http://us.toshiba.com/computers/laptops/satellite/C650/C655D-S5200/)

More detailed information on my hardware gathered with  Belarc Advisor:

*System Model:
TOSHIBA Satellite C655D PSC0YU-018001
System Serial Number: 5B013665Q
Enclosure Type: Notebook

*Processor:
1000 megahertz AMD C-50
No memory cache
64-bit ready
Multi-core (2 total)
Not hyper-threaded

*Main Circuit Board:
Board: TOSHIBA Portable PC Base Board Version
BIOS: Insyde Corp. 1.40 02/18/2011

*Drives:
286.27 Gigabytes Usable Hard Drive Capacity
183.60 Gigabytes Hard Drive Free Space

MATSHITA DVD-RAM UJ8A0AS SATA CdRom Device [Optical drive]

TOSHIBA MK3265GSXN [Hard drive] (320.07 GB) -- drive 0, s/n 31JZBH1NB, rev GH101M, SMART Status: Healthy

*Memory Modules
2664 Megabytes Usable Installed Memory
(It's DD3, 3 GB installed)

*Controllers:
AMD SATA Controller

*Display
AMD Radeon HD 6250 Graphics [Display adapter]
LGD LP156WH2-TLAA [Monitor] (15.3"vis)

*Bus Adapters
A2R3PVSM IDE Controller
Standard Enhanced PCI to USB Host Controller (3x)
Standard OpenHCD USB Host Controller (3x)

*Multimedia
Conexant SmartAudio HD

*Communications
Atheros AR8152/8158 PCI-E Fast Ethernet Controller (NDIS 6.20)
 primary 	Auto IP Address: 	192.168.1.4 / 24
Gateway: 	192.168.1.1
Dhcp Server: 	192.168.1.1
Physical Address: 	00:26:6C:BA:CF:CC
Connection Speed: 	100 Mbps

Realtek RTL8188CE Wireless LAN 802.11n PCI-E NIC
Auto IP Address: 	192.168.1.12 / 24
Gateway: 	192.168.1.1
Dhcp Server: 	192.168.1.1
Physical Address: 	68:A3:C4:8A:5A:B9
Connection Speed: 	54 Mbps
Teredo Tunneling Pseudo-Interface

*Other Devices
Microsoft AC Adapter
Microsoft ACPI-Compliant Control Method Battery
Microsoft Composite Battery
HID-compliant consumer control device
HID-compliant device (2x)
USB Input Device (2x)
TOSHIBA Web Camera
Standard PS/2 Keyboard
ELAN PS/2 Port Touch-Pad [Mouse]
HID-compliant mouse
USB Composite Device (2x)
USB Mass Storage Device
USB Root Hub (6x)
Generic volume shadow copy

I didn't bother to include the software information, that's all Windows stuff, and took out the information for virtual drives and such, again Windows stuff.

---

### Post by TeoBigusGeekus on 2011-10-10
Try to log in in the ubuntu classic session and see if the problem persists.

---

### Post by deserthowler on 2011-10-10
I have been using Unity 2D on my 2 laptops for about 4 months with no problem.  You can find it in synaptic.

YMMV

Earl

---

### Post by MichaelYammer on 2011-10-17
Thanks, but I am using Ubuntu Classic.

---

### Post by MichaelYammer on 2011-10-17
Thanks, but I have tried Unity and frankly don't like it. The "Classic" Ubuntu Teo was talking about is Gnome, Super OS installs both Unity and Gnome.

---

### Post by diablo465 on 2012-03-17
I have the exact problem as you mentioned above with the same machine. at the beginning 11.10 works fine then it totally gets freezed before logging in. then I decided to go for 10.04. Getting the wifi work is miserable but you can do it by installing wifi drivers(before doing that, you need also download build-essential from installing disk, remember usb installing is not working here) then you can make the wiki work.
however. you will still face lots of problem as now i don't know how to make my microphone work.
so what's yr situation now?

---

### Post by Rebelli0us on 2012-03-17
Both my machines were crashing randomly. I removed the **proprietary** AMD Radeon HD___ graphics driver and the problem is gone.

---

### Post by Andrew_P on 2012-03-17
> **diablo465 said:**
> ... as now i don't know how to make my microphone work. so what's yr situation now?

With Ubuntu 10.04.1 (Lucid Lynx) I occasionally have problems with the microphone just "going away" for no apparent reason.  Sometimes it can be fixed by opening the ALSA mixer, where I find the microphone has been muted by some rogue process.  Other times I need to reboot the machine and the microphone functionality mysteriously reappears without doing anything else at all.  (My Shuttle XPC actually has *two* microphone inputs — one on the back of the box and one on the front, and they have separate controls in the mixer.)

---

### Post by hakermania on 2012-03-17
Hello, sometimes I had this problem to, and then I was giving:
Ctrl+Alt+F1
Ctrl+Alt+F7
and the problem went away....
See if this temporary solution matches you.

---

