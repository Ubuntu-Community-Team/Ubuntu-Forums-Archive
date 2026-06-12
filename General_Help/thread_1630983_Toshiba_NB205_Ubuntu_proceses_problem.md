---
title: "Toshiba NB205 Ubuntu proceses problem"
date: 2010-11-26
forum: General Help
---

### Post by BryanMtdt on 2010-11-26
Hi, I just installed Ubuntu Netbook Remix 10.10 on my Toshiba NB205, I had a couple problems on runtime.

1) Any process (including boot, shutdown, download, open programs, etc) is freeze (don't have any progress) until I move the mouse or hit any button, so for install and use my ubuntu I have to keep moving my mouse and as you imagine is VERY TIRED.

2) I get some general freeze on random times, neither the mouse, keyboard or process move, I notice that if I unplug power it unfreze, and I can work for some time.

This 2 problems annoy me a lot, and I suspect is a problem related to my Netbook Model, I read about someone that has the same problem but no solution there.

This is what I did:

I Try Ubuntu loading from my USB memory (1GB), run very good but with the 2 problems, but I thought it can be resolved installing.

I installed along side with W7, couldn't boot Ubuntu, so I configured GRUB2 and it could enter now, but if I don't press **** after selecting Ubuntu it give me the BusyBox, and then the same 2 problems.

I get rid of my W7 and did a Full Install on my 160GB HDD, hoping it can work fine, but no.

I install all updates and no effect on that.

So I'm looking for an answer that give me a light on this. ;)

Another points, my sound, wireless and other features seems to work fine.

---

### Post by BryanMtdt on 2010-11-26
:KS It seems I fixed following this

```

linux    ${rel_dirname}/${basename} root=${linux_root_device_thisversion} ro $2 nohz=off 
Then run the following from the Terminal to complete the fix: 
sudo update-grub 
A reboot will be required to apply the change. 

```

At this thread

[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks/ToshibaNB205](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks/ToshibaNB205)

I had to open gedit with ```
sudo gedit
``` to modify 10_linux (root)

I'm new at Ubuntu but hope to learn alot, so I'll write if I found something more.

---

### Post by BryanMtdt on 2010-12-01
Hi Ubuntu is working very good, even get Compiz working, no problems with sound, Fn buttons, backlight, booting and ohers.

But I have a major problem for me

**Wireless is no working anymore**

Before the problem I could see networks by clicking on the icon and now

It tells me "Wireless Network Deactivated", 

The red light of Wireless is on.

Bios Wireless Com SW is ON.

I've been searching for solutions but non of the seems to work, maybe cause the old of those threats, 

**Can someone help me with this?**, I described a litlle more of my situation on the first post, now I'm using the Ubuntu Desktop on the boot. I didn't like Unity to work.

---

### Post by BryanMtdt on 2010-12-02
Can someone give me a light?

I'll soon need to use wireless and I don't want to go back to Windows.

---

### Post by gandaran on 2010-12-02
> **BryanMtdt said:**
> Can someone give me a light?

I'll soon need to use wireless and I don't want to go back to Windows.
have you checked system » administration » hardware drivers!
you may need to enable the wireless driver.
post here the results from running this command in terminal
```
lspci
```
and
```
lsusb
```

---

### Post by lrgmmc on 2010-12-02
are you dual booting? if i remember right you have to enable wireless on windose first.
also have a look here seems to help a few [http://www.uluga.ubuntuforums.org/showthread.php?t=1491379](http://www.uluga.ubuntuforums.org/showthread.php?t=1491379)

---

### Post by BryanMtdt on 2010-12-03
Thanks for the replays, this is my lspci

```

00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

```

And my lsusb

```

Bus 005 Device 002: ID 0930:0508 Toshiba Corp. Integrated Bluetooth HCI
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b128 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Is an internal Atheros Wifi device (for the Toshiba NB205)

I'm not using dual boot, but I can tell the Wireless was working like a couple days or so, but stop working and looks like deactivated.

I switch OFF ON the Wireless COM SW on the Bios, and the Bios is up to date.

About the drivers I don't have any proprietary drivers listed, maybe I should get them?

---

### Post by gandaran on 2010-12-04
> Is an internal Atheros Wifi device (for the Toshiba NB205)

I'm not using dual boot, but I can tell the Wireless was working like a couple days or so, but stop working and looks like deactivated.

I switch OFF ON the Wireless COM SW on the Bios, and the Bios is up to date.

About the drivers I don't have any proprietary drivers listed, maybe I should get them?
atheros cards work well with the default ubuntu driver, if you want to try the proprietary diver install the mad-wifi driver, you can install the source code from package manager and compile it.
before you install anything try deleting every existing wireless configurations in network manager » wireless tab then reboot the computer, see if it can detect wireless connections now.

---

### Post by BryanMtdt on 2010-12-04
[INDENT]A tried that but nothing.

I run this con terminal maybe it can help.

```

~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
vboxnet0  no wireless extensions.


```
[/INDENT]

---

### Post by BryanMtdt on 2010-12-04
I opted for install MadWifi, it seems good, but I came up with this during install

```

bryanmtdt@bryanmtdt-TOSHIBA-NB205:~/Escritorio/madwifi-hal-0.10.5.6-r4126-20100324$ ls
ath            COPYRIGHT        Makefile         README      SNAPSHOT
ath_hal        hal              Makefile.inc     README.dfs  THANKS
ath_rate       include          Makefile.kernel  regression  tools
BuildCaps.inc  INSTALL          net80211         release.h
contrib        kernelversion.c  patch-kernel     scripts
bryanmtdt@bryanmtdt-TOSHIBA-NB205:~/Escritorio/madwifi-hal-0.10.5.6-r4126-20100324$ sudo make
[sudo] password for bryanmtdt: 
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.35-23-generic/build SUBDIRS=/home/bryanmtdt/Escritorio/madwifi-hal-0.10.5.6-r4126-20100324 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-23-generic'
  CC [M]  /home/bryanmtdt/Escritorio/madwifi-hal-0.10.5.6-r4126-20100324/ath/if_ath.o
/home/bryanmtdt/Escritorio/madwifi-hal-0.10.5.6-r4126-20100324/ath/if_ath.c: In function 'ath_merge_mcast':
/home/bryanmtdt/Escritorio/madwifi-hal-0.10.5.6-r4126-20100324/ath/if_ath.c:4268: error: 'struct net_device' has no member named 'mc_list'
/home/bryanmtdt/Escritorio/madwifi-hal-0.10.5.6-r4126-20100324/ath/if_ath.c:4268: error: dereferencing pointer to incomplete type
/home/bryanmtdt/Escritorio/madwifi-hal-0.10.5.6-r4126-20100324/ath/if_ath.c:4270: error: dereferencing pointer to incomplete type
/home/bryanmtdt/Escritorio/madwifi-hal-0.10.5.6-r4126-20100324/ath/if_ath.c:4270: error: dereferencing pointer to incomplete type
/home/bryanmtdt/Escritorio/madwifi-hal-0.10.5.6-r4126-20100324/ath/if_ath.c:4270: error: dereferencing pointer to incomplete type
/home/bryanmtdt/Escritorio/madwifi-hal-0.10.5.6-r4126-20100324/ath/if_ath.c:4270: error: dereferencing pointer to incomplete type
/home/bryanmtdt/Escritorio/madwifi-hal-0.10.5.6-r4126-20100324/ath/if_ath.c:4272: error: dereferencing pointer to incomplete type
/home/bryanmtdt/Escritorio/madwifi-hal-0.10.5.6-r4126-20100324/ath/if_ath.c:4272: error: dereferencing pointer to incomplete type
/home/bryanmtdt/Escritorio/madwifi-hal-0.10.5.6-r4126-20100324/ath/if_ath.c:4272: error: dereferencing pointer to incomplete type
/home/bryanmtdt/Escritorio/madwifi-hal-0.10.5.6-r4126-20100324/ath/if_ath.c:4272: error: dereferencing pointer to incomplete type
make[3]: *** [/home/bryanmtdt/Escritorio/madwifi-hal-0.10.5.6-r4126-20100324/ath/if_ath.o] Error 1
make[2]: *** [/home/bryanmtdt/Escritorio/madwifi-hal-0.10.5.6-r4126-20100324/ath] Error 2
make[1]: *** [_module_/home/bryanmtdt/Escritorio/madwifi-hal-0.10.5.6-r4126-20100324] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-23-generic'
make: *** [modules] Error 2

```

seems like a problem on the building

this is my uname -r
2.6.35-23-generic

I'll keep looking

---

### Post by BryanMtdt on 2010-12-04
I run this

```

su -
sudo gedit /etc/apt/sources.list
sudo apt-get update && sudo apt-get upgrade   sudo apt-get install build-essential libssl-dev
sudo apt-get install linux-headers-`uname -r`
sudo apt-get install subversion
sudo -i
sudo svn checkout http://svn.madwifi-project.org/madwifi/trunk/ madwifi-ng
cd madwifi-ng
echo "" >> /etc/modprobe.d/blacklist
echo "#Remove To Install MadWIFI Drivers" >> /etc/modprobe.d/blacklist
echo "blacklist ath9k" >> /etc/modprobe.d/blacklist
echo "blacklist ath5k" >> /etc/modprobe.d/blacklistCode:
make && make install
echo ath_pci >> /etc/modules

```

Everything runs fine and when I restarted the Wireless section on the Network Manager Disapear, so only can see Ethernet and VPN tabs there, I restarted again hoping an update but nothing.

This is the iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.


```

---

### Post by BryanMtdt on 2010-12-04
I'm thinking it can be related with the Netbook Remix (Unity), but I'm using with Desktop boot.

I'm considering formating and reinstall with Ubuntu Desktop.

Any idea?

---

### Post by gandaran on 2010-12-05
does the mad-wifi driver show in system » administration » hardware drivers ? I think it should and should after compiling the driver successfully, (I have a netbook and it does have the mad-wifi driver listed there but not activated as wireless is working well) 
I 'm not sure if you did succeed compiling the driver successfully but just for the record one easy way of compiling the driver without any errors in ubuntu (if it's not listed in hardware drivers!) is to install module-assistant, choose the mad-wifi driver from the module-assistant list and start the download and compiling options, module-assistant does everything needed including loading the module.
module-assistant is run from the terminal.

---

### Post by BryanMtdt on 2010-12-05
Hi Gandaran, seems like it didn't installed correctly when I try, I saw some warnings at the building, is good to know that there is a module assistant thnx.

I installed with sudo apt-get and run it.

I found the mad module there, and listed it, get, but when I try to get it fail.

It have a note that says: Ignoring this package, Maybe you need to add contrid or non-free  at the source list.

  I already add those to sources.list so I did sudo apt-get update and try again, but there is the same error.

Maybe is not it but I read the INSTALL file of the MadWifi and they compiled with gcc-3.4.2 and I have gcc-4.4.5

---

### Post by BryanMtdt on 2010-12-16
Hi, I solved the isue with the Wireless but not the way I could like.

I had to format the entire disk, so I started a clean install of Ubuntu Netbook Remix.

With the USB Disk of Ubuntu 10.10 I erase all partitions and configure :
A 17GB Primary Partition NTFS for a W7, this is what I didn't like to do.
And 1 Logic Partition for Ubuntu, 1 swap partition with 1.7GB

With Windows I activated the Wireless device.

Instaled Ubuntu and configured GRUB with the LiveUSB, later I change it for BURG ;)

Wireless worked fine on the Try and the Installed SO.

Other things worked just out of the box.

So I can work peacefully with my ubuntu except I have this partition wasting space, but is just in case I got Wifi deactivated again.

Thanks for the help and this post is SOLVED :D

---

