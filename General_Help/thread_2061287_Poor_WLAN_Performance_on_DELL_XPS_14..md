---
title: "Poor WLAN Performance on DELL XPS 14."
date: 2012-09-22
forum: General Help
---

### Post by detl_ on 2012-09-22
Hello everybody,
since a few weeks I have got a new DELL XPS 14. ([http://www.dell.com/ch/unternehmen/p/xps-14-l421x/pd?c=ch&cs=chbsdt1&l=de&s=bsd&~ck=mn](http://www.dell.com/ch/unternehmen/p/xps-14-l421x/pd?c=ch&cs=chbsdt1&l=de&s=bsd&~ck=mn))
And since a few days I installed Ubuntu 12.04 on it.

Yesterday I was surfing the web with my new laptop and realized that it takes very long for any website to load.
I first thought its my private WLAN network so I rebooted my router. 
The problem persisted.
Then I took my old Dell Latitude 4300 to see if that has got the same issue.
But that one works perfect. The full WLAN performance gets picked up. (1,200 MB/s)
On my DELL XPS I get (0,300 MB/s) the very most.

I checked a ping to google and the comparison was surprising to me:
DELL XPS 14 : 150ms
DELL Latitude: 15ms

Its about 10 times slower than my old Laptop.
I must say that on my old Laptop I installed Windows 7 but that should not matter here.

On my new system I see the following cards when doing lspci:

00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Ivy Bridge PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.2 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 3 (rev c4)
00:1c.3 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 4 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
01:00.0 3D controller: NVIDIA Corporation Device 1140 (rev a1)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 07)
08:00.0 Network controller: Intel Corporation Centrino Advanced-N 6235 (rev 24)
09:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)
09:00.1 SD Host controller: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)


I remember long back to my first Ubuntu, there were issues with non Intel Ethernet cards where I needed to install drivers for it. And that Realtek controller makes me a bit nervous. 
I thought I have a Intel® Centrino® Advanced-N 6235 Controller in it.


Does anybody have got an idea how to figure out where the problem might be ?
Or maybe somebody else encountered the same. 


Thanks,
detlef

---

### Post by krishna.988 on 2012-09-22
> **detl_ said:**
> Hello everybody,
since a few weeks I have got a new DELL XPS 14. ([http://www.dell.com/ch/unternehmen/p/xps-14-l421x/pd?c=ch&cs=chbsdt1&l=de&s=bsd&~ck=mn](http://www.dell.com/ch/unternehmen/p/xps-14-l421x/pd?c=ch&cs=chbsdt1&l=de&s=bsd&~ck=mn))
And since a few days I installed Ubuntu 12.04 on it.

Yesterday I was surfing the web with my new laptop and realized that it takes very long for any website to load.
I first thought its my private WLAN network so I rebooted my router. 
The problem persisted.
Then I took my old Dell Latitude 4300 to see if that has got the same issue.
But that one works perfect. The full WLAN performance gets picked up. (1,200 MB/s)
On my DELL XPS I get (0,300 MB/s) the very most.

I checked a ping to google and the comparison was surprising to me:
DELL XPS 14 : 150ms
DELL Latitude: 15ms

Its about 10 times slower than my old Laptop.
I must say that on my old Laptop I installed Windows 7 but that should not matter here.

On my new system I see the following cards when doing lspci:

00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Ivy Bridge PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.2 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 3 (rev c4)
00:1c.3 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 4 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
01:00.0 3D controller: NVIDIA Corporation Device 1140 (rev a1)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 07)
08:00.0 Network controller: Intel Corporation Centrino Advanced-N 6235 (rev 24)
09:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)
09:00.1 SD Host controller: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)


I remember long back to my first Ubuntu, there were issues with non Intel Ethernet cards where I needed to install drivers for it. And that Realtek controller makes me a bit nervous. 
I thought I have a Intel® Centrino® Advanced-N 6235 Controller in it.


Does anybody have got an idea how to figure out where the problem might be ?
Or maybe somebody else encountered the same. 


Thanks,
detlef


Check weather your Dell laptop is listed here in the Ubuntu Certified hardware list

[http://www.ubuntu.com/certification/desktop/models/?release=12.04%20LTS&category=Desktop&category=Laptop&category=Netbook](http://www.ubuntu.com/certification/desktop/models/?release=12.04%20LTS&category=Desktop&category=Laptop&category=Netbook)

If it is listed then download the relevant ISO and re- install 12.04 in it..

Everything should work fine

---

