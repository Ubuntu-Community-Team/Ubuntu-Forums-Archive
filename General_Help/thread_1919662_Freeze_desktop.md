---
title: "Freeze desktop"
date: 2012-02-03
forum: General Help
---

### Post by PatronMaster on 2012-02-03
Hi
i have ubuntu 11.10 and i try install the driver for my card alfa network rtl8187. 
I install the driver but for kernel 2.6.

Now i have huge problems when the card connect to internet my desktop freeze and i need reboot manual (press the button).

I try remove the drive i have installed (make unistall), but blaclist.conf give one warning. 
I try install compact-wireless 3.3-rtc-2 
make
make install
make unload 
make wunload
first i have warning blacklist but i see one tutorial to remove the warning and now i don't have.

But when the card connect to internet my desktop freeze.
Is other way or i need format and install again.

The best regards

this is tutorial i use to install the drive
[http://forum.aircrack-ng.org/index.php?topic=5755.0](http://forum.aircrack-ng.org/index.php?topic=5755.0)

Drive ALFA-AWUS036H

tutorial i do
sudo dpkg --configure -a && sudo apt-get install -f && sudo apt-get update
sudo apt-get install linux-headers-$(uname -r) build-essential make patch gettext autoconf python-psyco subversion tcl8.5 openssl zlib1g zlib1g-dev libssh2-1-dev libssl-dev libnl1 libnl-dev libpcap0.8 libpcap0.8-dev python-scapy cracklib-runtime macchanger-gtk tshark
sudo mkdir /usr/src/drivers
cd /usr/src/drivers
sudo wget [http://wireless.kernel.org/download/iw/iw-0.9.22.tar.bz2](http://wireless.kernel.org/download/iw/iw-0.9.22.tar.bz2)
sudo tar jxvf iw-0.9.22.tar.bz2
cd iw-0.9.22
sudo make
sudo make install

sudo mkdir /usr/src/drivers
cd /usr/src/drivers
sudo unzip RT2870_Firmware_V22.zip
sudo cp RT2870_Firmware_V22/rt2870.bin /lib/firmware/$(uname -r)

sudo cp /etc/modprobe.d/blacklist.conf /etc/modprobe.d/blacklist_orig.conf~
echo "blacklist rtl8187" | sudo tee -a /etc/modprobe.d/blacklist.conf
echo "blacklist mac80211" | sudo tee -a /etc/modprobe.d/blacklist.conf
echo "blacklist r8187" | sudo tee -a /etc/modprobe.d/blacklist.conf
echo "blacklist rt2870sta" | sudo tee -a /etc/modprobe.d/blacklist.conf
echo "blacklist rt3070sta" | sudo tee -a /etc/modprobe.d/blacklist.conf
echo "blacklist rt2800usb" | sudo tee -a /etc/modprobe.d/blacklist.conf
----------------------------------------------------------------------------------------------
sudo rmmod rtl8187 mac80211
sudo mkdir /usr/src/drivers
cd /usr/src/drivers
sudo wget [http://download.aircrack-ng.org/drivers/compat-wireless-aircrack-alfa036h-050nh.tar.bz2](http://download.aircrack-ng.org/drivers/compat-wireless-aircrack-alfa036h-050nh.tar.bz2)
sudo tar jxvf compat-wireless-aircrack-alfa036h-050nh.tar.bz2
cd compat-wireless-aircrack-alfa036h-050nh
sudo wget [http://patches.aircrack-ng.org/mac80211_2.6.28-rc4-wl_frag+ack_v3.patch](http://patches.aircrack-ng.org/mac80211_2.6.28-rc4-wl_frag+ack_v3.patch)
cat mac80211_2.6.28-rc4-wl_frag+ack_v3.patch | patch -p1
sudo make
sudo make install
sudo make unload

lspc------------------------------------------

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 82801 PCI Bridge (rev b5)
00:1c.6 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 7 (rev b5)
00:1c.7 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 8 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation Z68 Express Chipset Family LPC Controller (rev 05)
00:1f.2 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 4 port SATA IDE Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
00:1f.5 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 2 port SATA IDE Controller (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Cayman XT [AMD Radeon HD 6900 Series]
01:00.1 Audio device: ATI Technologies Inc Device aa80
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
04:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
05:00.0 PCI bridge: ASMedia Technology Inc. Device 1080 (rev 01)
06:02.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)
07:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
08:00.0 IDE interface: Marvell Technology Group Ltd. Device 91a3 (rev 11)

---

### Post by Bucky Ball on 2012-02-03
Welcome.

At the bottom of this list there a three drivers for the various 8187s.

[http://www.realtek.com/search/default.aspx?keyword=rtl8187](http://www.realtek.com/search/default.aspx?keyword=rtl8187)

Which one did you go for? In the output of 'lspci' in a terminal look for 'Network Controller'. What exactly does it say?

---

