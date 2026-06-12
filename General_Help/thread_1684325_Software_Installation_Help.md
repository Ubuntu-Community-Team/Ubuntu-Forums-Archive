---
title: "Software Installation Help?"
date: 2011-02-08
forum: General Help
---

### Post by codysblackbox on 2011-02-08
Hey. I'm new to Ubuntu and recently installed it on a Dell desktop. I'm trying to get my Tenda Wireless PCI Adapter to work with it, and was pleased to see that they have software for Linux (a tar.bz2 file). The trouble is, I don't know how to install it. Is there a program which can do this for me easily? Is there a step-by-step guide that would help me to know how to do this? Keep in mind, I am brand-spanking new to Ubuntu and even Linux.

---

### Post by P4man on 2011-02-09
Before we scare the bejuses out of you by explaining how to unpack that tarball and compile the drivers, lets see if we really need to do that.

First of all, which version of ubuntu are you using?

Secondly, can you (temporarily) connect the machine to the internet with a cable?

Lastly, hoping you can connect wired, can you open a terminal (applications > accessories > terminal) and copy paste the output of following commands:

```
lspci

```

```
iwconfig
```

---

### Post by codysblackbox on 2011-02-09
> **P4man said:**
> Before we scare the bejuses out of you by explaining how to unpack that tarball and compile the drivers, lets see if we really need to do that.

First of all, which version of ubuntu are you using?

Secondly, can you (temporarily) connect the machine to the internet with a cable?

Lastly, hoping you can connect wired, can you open a terminal (applications > accessories > terminal) and copy paste the output of following commands:

```
lspci

```

```
iwconfig
```



I can connect to the internet using my laptop's wireless via ethernet cable. I am running Ubuntu 10.10 netbook as a desktop.

Here is what I got from inputting the commands:


cody@Hal-Dimension-2400:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:04.0 Network controller: RaLink Device 3062
01:06.0 PCI bridge: Texas Instruments PCI2050 PCI-to-PCI Bridge (rev 01)
01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
02:06.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01)
cody@Hal-Dimension-2400:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off



Thanks!

---

### Post by 3rdalbum on 2011-02-09
I think we might have to scare the bejesus out of you and tell you how to unpack that tarball :-(  Doesn't look like Linux recognises your device.

First, get an internet connection by plugging your computer directly into your router via Ethernet cable.

Go to System > Administration > Synaptic Package Manager. Go to Settings > Repositories and make sure that the first four checkboxes are ticked. Close this window. Click the Reload button in Synaptic. Find the "build-essential" and "linux-headers-generic" packages and install them. These are BIG packages, but they are necessary.

Double-click on the drivers .tar.gz archive and extract it to your desktop.

Go to Applications > Accessories > Terminal and type 'cd ' (without the quotes, with a space at the end) and then drag the new folder on your desktop to the terminal. This brings the terminal to the background - click on it again and press Enter. This navigates the terminal to the directory of the source code, so you can work on it.

Type:

```
./configure
```

If you get an error message about "configure not found" then don't worry, just continue.

```
make
sudo make install
```

The last command will ask you for your password - type it in and press Enter. Note that it will not even show you any * symbols as you're typing.

Finally, reboot. If all has gone well you should be able to get wireless now.

EDIT: Important to note: You'll need to run the "./configure, make, sudo make install" again whenever you get a new Linux kernel through the Update Manager.

---

### Post by codysblackbox on 2011-02-09
> **3rdalbum said:**
> I think we might have to scare the bejesus out of you and tell you how to unpack that tarball :-(  Doesn't look like Linux recognises your device.

First, get an internet connection by plugging your computer directly into your router via Ethernet cable.

Go to System > Administration > Synaptic Package Manager. Go to Settings > Repositories and make sure that the first four checkboxes are ticked. Close this window. Click the Reload button in Synaptic. Find the "build-essential" and "linux-headers" packages and install them. These are BIG packages, but they are necessary.

Double-click on the drivers .tar.gz archive and extract it to your desktop.

Go to Applications > Accessories > Terminal and type 'cd ' (without the quotes, with a space at the end) and then drag the new folder on your desktop to the terminal. This brings the terminal to the background - click on it again and press Enter. This navigates the terminal to the directory of the source code, so you can work on it.

Type:

```
./configure
```

If you get an error message about "configure not found" then don't worry, just continue.

```
make
sudo make install
```

The last command will ask you for your password - type it in and press Enter. Note that it will not even show you any * symbols as you're typing.

Finally, reboot. If all has gone well you should be able to get wireless now.

Do I need to download all of the linux-headers files? There are a lot listed here and some of them have already been downloaded. Thank you for your help!

---

### Post by wojox on 2011-02-09
Open a terminal and run:

```
sudo apt-get install linux-headers-$(uname -r) 
```

---

### Post by 3rdalbum on 2011-02-09
Sorry for the lack of clarity, you just need "linux-headers-generic". If you've already got some of the linux-headers packages, then you've probably already got this one anyway.

EDIT: Or do what wojox suggested - but mine has the advantage of always downloading the headers for any new kernels that get pushed out via updates later.

---

### Post by codysblackbox on 2011-02-09
Okay. When I try to apply the marked installations I am told to use the Ubuntu Netbook CD-ROM, which I put in and continue to get the error message. I do already have linux-header-generic, but I don't yet have build-essential.

I also tried to download build-essential in the terminal and was asked again to put in the install CD.

---

### Post by 3rdalbum on 2011-02-09
> **codysblackbox said:**
> Okay. When I try to apply the marked installations I am told to use the Ubuntu Netbook CD-ROM, which I put in and continue to get the error message. I do already have linux-header-generic, but I don't yet have build-essential.

I also tried to download build-essential in the terminal and was asked again to put in the install CD.

What error message is this?

If you want to you can go to Settings > Repositories and uncheck the "CD-ROM with Ubuntu 10.10" (it's in the bit that says "Installable from CD-ROM/DVD"). This will now prevent it from asking for the CD.

Also, you need to have an internet connection at this point... just in case that's the error message.

---

### Post by codysblackbox on 2011-02-09
Cool! That worked. I was able to install build-essential without the CD-ROM error message.

Now when I type the commands into the terminal, I get this error after "make":
"make: *** no targets specified and no makefile found. stop."

And this after "sudo make install":
"make: *** no rule to make target 'install'. stop."

---

### Post by codysblackbox on 2011-02-10
Here is what I found in the readme. Some of this makes sense to me, but not all of it:

1> $tar -xvzf RT3562_Linux_STA_x.x.x.x.tgz
    go to "./RT3562_Linux_STA_x.x.x.x" directory.
    
2> In Makefile
     set the "MODE = STA" in Makefile and chose the TARGET to Linux by set "TARGET = LINUX"
     define the linux kernel source include file path LINUX_SRC
     modify to meet your need.

3> In os/linux/config.mk 
    define the GCC and LD of the target machine
    define the compiler flags CFLAGS
    modify to meet your need.
    ** Build for being controlled by NetworkManager or wpa_supplicant wext functions
       Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
       => #>cd wpa_supplicant-x.x
       => #>./wpa_supplicant -Dwext -ira0 -c wpa_supplicant.conf -d
    ** Build for being controlled by WpaSupplicant with Ralink Driver
       Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n'.
       => #>cd wpa_supplicant-0.5.7
       => #>./wpa_supplicant -Dralink -ira0 -c wpa_supplicant.conf -d

4> $make            
    # compile driver source code
    # To fix "error: too few arguments to function ¡¥iwe_stream_add_event"
      => $patch -i os/linux/sta_ioctl.c.patch os/linux/sta_ioctl.c

5> $cp RT2860STA.dat  /etc/Wireless/RT2860STA/RT2860STA.dat       
    
6> load driver, go to "os/linux/" directory.
    #[kernel 2.4]
    #    $/sbin/insmod rt3562sta.o
    #    $/sbin/ifconfig ra0 inet YOUR_IP up
        
    #[kernel 2.6]
    #    $/sbin/insmod rt3562sta.ko
    #    $/sbin/ifconfig ra0 inet YOUR_IP up

7> unload driver    
    $/sbin/ifconfig ra0 down
    $/sbin/rmmod rt3562sta

---

### Post by P4man on 2011-02-11
HAve a look here:
[http://ubuntuforums.org/showthread.php?t=1674202&page=2](http://ubuntuforums.org/showthread.php?t=1674202&page=2)

Post 12 explains it nicely.

---

### Post by codysblackbox on 2011-02-11
That worked perfectly! Thank you so much! For some reason when I tried that with the drivers that came with the install disc, it wouldn't read the make file.

---

