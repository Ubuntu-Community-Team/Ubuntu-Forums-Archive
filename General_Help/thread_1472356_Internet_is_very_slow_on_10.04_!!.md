---
title: "Internet is very slow on 10.04 !!"
date: 2010-05-04
forum: General Help
---

### Post by ibrahim.k on 2010-05-04
Hi,


I am browsing the internet using firefox but browsing is very slow comparing to 9.10 ?

What can I do ?

---

### Post by madverb on 2010-05-04
Wireless? I had a problem with the wireless settings when going to 10.04. I just had to install some wireless extras. Just search in Synaptic for wireless kernel

---

### Post by ibrahim.k on 2010-05-04
> **madverb said:**
> Wireless? I had a problem with the wireless settings when going to 10.04. I just had to install some wireless extras. Just search in Synaptic for wireless kernel


Yes I am using wireless and after searching for wireless kernel I got many results !

I don't know which one should I install ?


My laptop is 
Hp dv6 1045ee

---

### Post by Smart Viking on 2010-05-04
Hey madverb you avatar didn't have transparent background, so i configured it a little(I just had too). :)
[IMG]http://img526.imageshack.us/img526/7325/tiy.png[/IMG]

---

### Post by P4man on 2010-05-04
before messing with kernels and what not, lets first find out what is happening exactly as "slow browsing" can be a lot of things (ipv6, DNS, etc).

Is you wireless connection good (how many bars) ?
If you download a large a file, is download speed normal or not?
If you connect wired ethernet (if you can), does that solve the problem?

Have you tried disabling IPv6? in the address bar type
```
about:config
```

search for
```
network.dns.disableIPv6
```

enable it. Does it make a difference?

---

### Post by ibrahim.k on 2010-05-04
> **P4man said:**
> before messing with kernels and what not, lets first find out what is happening exactly as &quot;slow browsing&quot; can be a lot of things (ipv6, DNS, etc).

Is you wireless connection good (how many bars) ?
If you download a large a file, is download speed normal or not?
If you connect wired ethernet (if you can), does that solve the problem?

Have you tried disabling IPv6? in the address bar type
```
about:config
```search for
```
network.dns.disableIPv6
```enable it. Does it make a difference?

  I have two of three bars 80%  Downloading is slow as well very very slow with all files  Am sorry I can't connect using an ethernet cable I only have wireless  and I didn't know how to use that codes !!

---

### Post by ibrahim.k on 2010-05-04
Ipv6 is ignored by default.

---

### Post by P4man on 2010-05-04
ok lets see which wifi card you have.
Open a terminal (applications > accessories > terminal) and type in these 2 commands:

```
lspci
```

```
lsusb
```

(LSPCI and LSUSB in lowercase). Copy paste the output here.

---

### Post by ibrahim.k on 2010-05-04
Please see this results.

ibrahim@ibrahim-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 9200M GS] (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
06:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
06:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
06:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
06:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
06:00.4 System peripheral: JMicron Technology Corp. xD Host Controller


ibrahim@ibrahim-laptop:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 004: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 09da:000a A4 Tech Co., Ltd Port Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 05c8:010f Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
ibrahim@ibrahim-laptop:~$

---

### Post by P4man on 2010-05-04
OK try this.

System > administration > software sources. 
Make sure "proprietary drivers for devices (restricted)" is enabled.

Then open a terminal and type:

```
sudo aptitude update
sudo aptitude install bcmwl-kernel-source
```

When its finished doing that:

System > administration > Hardware Drivers

Enable the broadcom restricted drivers in the list.

---

### Post by ibrahim.k on 2010-05-04
the terminal is not moving ! but I am waiting anyway is this normal ?

ibrahim@ibrahim-laptop:~$ sudo aptitude update
[sudo] password for ibrahim: 
Writing extended state information... Done
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                       
Hit [http://sy.archive.ubuntu.com](http://sy.archive.ubuntu.com) lucid Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://sy.archive.ubuntu.com/ubuntu/](http://sy.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://sy.archive.ubuntu.com/ubuntu/](http://sy.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://sy.archive.ubuntu.com/ubuntu/](http://sy.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Ign [http://sy.archive.ubuntu.com/ubuntu/](http://sy.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release
Get:1 [http://sy.archive.ubuntu.com](http://sy.archive.ubuntu.com) lucid-updates Release.gpg [189B]           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                    
Ign [http://sy.archive.ubuntu.com/ubuntu/](http://sy.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Ign [http://sy.archive.ubuntu.com/ubuntu/](http://sy.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Ign [http://sy.archive.ubuntu.com/ubuntu/](http://sy.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Ign [http://sy.archive.ubuntu.com/ubuntu/](http://sy.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Hit [http://sy.archive.ubuntu.com](http://sy.archive.ubuntu.com) lucid Release                                  
Get:2 [http://sy.archive.ubuntu.com](http://sy.archive.ubuntu.com) lucid-updates Release [38.5kB]               
Hit [http://sy.archive.ubuntu.com](http://sy.archive.ubuntu.com) lucid/main Packages                            
Hit [http://sy.archive.ubuntu.com](http://sy.archive.ubuntu.com) lucid/restricted Packages                      
Hit [http://sy.archive.ubuntu.com](http://sy.archive.ubuntu.com) lucid/main Sources      
Hit [http://sy.archive.ubuntu.com](http://sy.archive.ubuntu.com) lucid/restricted Sources
Hit [http://sy.archive.ubuntu.com](http://sy.archive.ubuntu.com) lucid/universe Packages 
Hit [http://sy.archive.ubuntu.com](http://sy.archive.ubuntu.com) lucid/universe Sources  
Hit [http://sy.archive.ubuntu.com](http://sy.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://sy.archive.ubuntu.com](http://sy.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://sy.archive.ubuntu.com](http://sy.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://sy.archive.ubuntu.com](http://sy.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://sy.archive.ubuntu.com](http://sy.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://sy.archive.ubuntu.com](http://sy.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://sy.archive.ubuntu.com](http://sy.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://sy.archive.ubuntu.com](http://sy.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://sy.archive.ubuntu.com](http://sy.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://sy.archive.ubuntu.com](http://sy.archive.ubuntu.com) lucid-updates/multiverse Sources
Fetched 38.6kB in 1min 22s (469B/s)
Reading package lists... Done             

ibrahim@ibrahim-laptop:~$ sudo aptitude install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following NEW packages will be installed:
  bcmwl-kernel-source dkms{a} fakeroot{a} patch{a} 
The following packages will be REMOVED:
  linux-backports-modules-wireless-2.6.32-21-generic{u} 
0 packages upgraded, 4 newly installed, 1 to remove and 2 not upgraded.
Need to get 896kB/1,187kB of archives. After unpacking 3,604kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://sy.archive.ubuntu.com/ubuntu/](http://sy.archive.ubuntu.com/ubuntu/) lucid/restricted bcmwl-kernel-source 5.60.48.36+bdcom-0ubuntu3 [896kB]
Fetched 896kB in 3min 32s (4,214B/s)                                            
(Reading database ... 122944 files and directories currently installed.)
Removing linux-backports-modules-wireless-2.6.32-21-generic ...(nothing after this)

---

### Post by ibrahim.k on 2010-05-04
the terminal stoped responding now ! what should I do please ? please see my reply above to see the latest steps

---

### Post by Smart Viking on 2010-05-04
ctrl+alt+f2

ps -e
# Find bash, i think it is bash, and notice the 4 first numbers, that is the "id", if they was 7356:
kill -9 7356

EDIT: Oh if you are doing something important with the terminal, don't do that.

---

### Post by P4man on 2010-05-04
If you are sure it froze (give it a few minutes), then abort it (control+C, or if needed kill the terminal) and try running

```
sudo aptitude clean
```

then try again. 

If that still fails, do not reboot. try this

```
sudo dpkg --configure -a
```

---

### Post by P4man on 2010-05-04
> **Smart Viking said:**
> ctrl+alt+f2

ps -e
# Find bash, i think it is bash, and notice the 4 first numbers, that is the "id", if they was 7356:
kill -9 7356

I guess thats the easy way, but you could also click the the close button on the terminal and confirm :)

---

### Post by ibrahim.k on 2010-05-04
I have closed it (force quit):( now should I do that steps again ?? because bradcom is not on the hardware drivers list yet

---

### Post by tjeremiah on 2010-05-04
> **P4man said:**
> OK try this.

System > administration > software sources. 
Make sure "proprietary drivers for devices (restricted)" is enabled.

Then open a terminal and type:

```
sudo aptitude update
sudo aptitude install bcmwl-kernel-source
```

When its finished doing that:

System > administration > Hardware Drivers

Enable the broadcom restricted drivers in the list.
im having the same issue as the thread creator. I did what you said above and dont see anything to select in the Hardware Drivers section. The installation worked too. Can it be because I am using wubi?

---

### Post by P4man on 2010-05-04
> **ibrahim.k said:**
> I have closed it (force quit):( now should I do that steps again ?? because bradcom is not on the hardware drivers list yet


Yes, see my post above.

---

### Post by P4man on 2010-05-04
> **tjeremiah said:**
> im having the same issue as the thread creator. I did what you said above and dont see anything to select in the Hardware Drivers section. The installation worked too. Can it be because I am using wubi?

No not likely wubi related, but what makes you think you have a broadcom 43xx wifi card? You have the same laptop?

---

### Post by ibrahim.k on 2010-05-04
I did the steps again and everything was fine but nothing appeared in the hardware drivers

---

### Post by P4man on 2010-05-04
Did you rerun 

```
sudo aptitude install bcmwl-kernel-source
```

(or does it say its already installed?)

---

### Post by ibrahim.k on 2010-05-04
yes everything was fine but nothing appeared ! i followed all the steps it was easy

ibrahim@ibrahim-laptop:~$ sudo aptitude install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

---

### Post by P4man on 2010-05-04
and you are still connected to the internet?
If so, well lets see the output of this

```
lshw -c network
```

---

### Post by ibrahim.k on 2010-05-04
lshw -c network

ibrahim@ibrahim-laptop:~$ sudo su
[sudo] password for ibrahim: 
root@ibrahim-laptop:/home/ibrahim# lshw -c network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 00:21:6b:5f:7d:1e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.0.103 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:32 memory:dc000000-dc001fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:23:8b:6a:8f:d4
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.10.1 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:31 ioport:5000(size=256) memory:d4010000-d4010fff(prefetchable) memory:d4000000-d400ffff(prefetchable) memory:d4020000-d402ffff(prefetchable)
root@ibrahim-laptop:/home/ibrahim#

---

### Post by tjeremiah on 2010-05-04
> **P4man said:**
> No not likely wubi related, but what makes you think you have a broadcom 43xx wifi card? You have the same laptop?

im willing to try anything because all through beta and till now, i have been having slow internet. Not just Firefox but system wide where it even affects updating the system. Tried the DNS solution in one old thread and that didnt work. Anyway, heres my specs :

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
08:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

```

---

### Post by dino99 on 2010-05-04
On some connections, the ipv6 kernel module may cause significant slowdowns and fail to connect to IPv6 servers. The Ubuntu Community wiki has instructions on disabling IPv6 to fix this issue. 

[https://wiki.ubuntu.com/IPv6](https://wiki.ubuntu.com/IPv6)

[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

---

### Post by P4man on 2010-05-04
> **ibrahim.k said:**
> lshw -c network

ibrahim@ibrahim-laptop:~$ sudo su
[sudo] password for ibrahim: 
root@ibrahim-laptop:/home/ibrahim# lshw -c network
  *-network               
       description: Wireless interface
       **product: PRO/Wireless 5100 AGN **[Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 00:21:6b:5f:7d:1e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet 

Ow, thats not what I was expecting. googling on your laptop and PCI ids I was convinced you had a broadcom wireless card, not an intel one. For that card, there are no proprietary drivers, but you shouldnt need them either. This card is well supported, it doesnt need any tricks as far as I know.

I concur with the above poster ( and what I said earlier). Look in to ipv6 issues, I dont think there is anything wrong with the wifi card or its drivers.

---

### Post by P4man on 2010-05-04
> **tjeremiah said:**
> im willing to try anything because all through beta and till now, i have been having slow internet. Not just Firefox but system wide where it even affects updating the system. Tried the DNS solution in one old thread and that didnt work. Anyway, heres my specs :

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
06:00.0 Network controller:** Intel Corporation PRO/Wireless 3945ABG **[Golan] Network Connection (rev 02)
08:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

```

Same comment to you as to the OP. You have an intel wifi card, there are no proprietary drivers for it, nor are they needed. Check out the ipv6 links dino99 posted a few posts up.

---

### Post by tjeremiah on 2010-05-04
> **P4man said:**
> Same comment to you as to the OP. You have an intel wifi card, there are no proprietary drivers for it, nor are they needed. Check out the ipv6 links dino99 posted a few posts up.
yeah, i read throughout the links in his post. Apparently after following directions to see if ipv6 is even enabled on my pc, it turns out that it isnt.

---

### Post by P4man on 2010-05-04
I didnt check the links, but it seems they are outdated. IPv6 is definately enabled on lucid, here is an up to date howto to check and disable it:

[http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html](http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html)

---

### Post by tjeremiah on 2010-05-04
> **P4man said:**
> I didnt check the links, but it seems they are outdated. IPv6 is definately enabled on lucid, here is an up to date howto to check and disable it:

[http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html](http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html)

thanks :)

---

### Post by ram4nd on 2010-05-08
> **tjeremiah said:**
> thanks :)

Did it work, i have slow wifi aswell. I even needed to write manually wifi conf so it would work. By that i mean i had to assign manual ip gw and dns

---

### Post by ibrahim.k on 2010-05-08
> **ram4nd said:**
> Did it work, i have slow wifi aswell. I even needed to write manually wifi conf so it would work. By that i mean i had to assign manual ip gw and dns

No my friend it didn't work, and I am still suffering :(

---

