---
title: "NVIDIA driver installation problem"
date: 2012-08-08
forum: General Help
---

### Post by community on 2012-08-08
Hi
   I recently installed nvidia drivers using *nvidia-current*. But after rebooting the nvidia x server settings doesn't recognize my graphics card. It showed an error displaying "type *nvidia-xconfig*" as root in terminal. After executing the command and restarting, the screen resolution changed to 640x...What is the reason? I somehow managed to reset by removing /etc/X11/xorg.cnf. Please tell me how to configure the graphics card successfully.

---

### Post by community on 2012-08-15
Anybody help please???

---

### Post by Scozzar on 2012-08-15
What are your computer specs?  Normal laptop resolution?

---

### Post by community on 2012-08-15
Samsung laptop.
Intel i5 2nd Gen processor.
4 GB RAM.
750 GB HDD.
1 GB NVIDIA OPtimus Graphics card.

Normal resolution is 1366x768.

---

### Post by Scozzar on 2012-08-15
What kind of Nvidia graphics though?  I have a 540m and this is how I fixed it...

Open up Terminal and type in:
```
sudo gedit /etc/X11/xorg.conf
```

And scroll down to the part where you see

vertical refresh 
Horizontal sync

Tell us what the numbers are for those

---

### Post by community on 2012-08-15
NVIDIA GeForce 520mx on Ubuntu 12.04. Presently drivers are not installed.


I removed xorg.conf as I said and now I got the resolution back. On running *gedit /etc/X11/xorg.conf* it opens a new file.

---

### Post by davidryderuk on 2012-08-15
Your post said you have Nvidia Optimus, which implies you have two graphics cards, an integrated Intel Graphics Card, and a descrete Nvidia Graphics Card. You can check which graphics cards you have by running:

```
lspci -nnk | grep iA3 VGA
```

In any case see these links for more information on Nvidia Optimus, and how you might be able to get the descrete Graphics Card to work in Linux.

[http://en.wikipedia.org/wiki/Nvidia_Optimus#GNU.2FLinux_support](http://en.wikipedia.org/wiki/Nvidia_Optimus#GNU.2FLinux_support)
[https://github.com/Bumblebee-Project/Bumblebee/wiki/FAQ](https://github.com/Bumblebee-Project/Bumblebee/wiki/FAQ)
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by bogan on 2012-08-15
Hi!.**All**,

The lspci command Posted above should read: 
```
lspci -nnk | grep -iA3 VGA
```With a '-' hyphen in front of the 'iA3'.

The original typo was mine.

Chao!,** bogan**.

---

### Post by davidryderuk on 2012-08-15
Sorry for the lack of credit. Thanks for the help in the other thread.

---

### Post by community on 2012-08-16
This is the output of 
*lspci -nnk | grep -iA3 VGA*



00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0126] (rev 09)
	Subsystem: Samsung Electronics Co Ltd Device [144d:c606]
	Kernel driver in use: i915
	Kernel modules: i915

---

### Post by bogan on 2012-08-16
Hi!, **Community**,

Well, Your system is not recognizing any nvidia Graphics card, or lspci would have listed it. Are you sure there is one?

If so, is it turned off in the Bios or by hardware?

Do you have Windows installed? If so, what does Device Manager show for a Display adapter??

See separate Post about Hybrid Graphics & Nvidia.

Chao!, **bogan**.

---

### Post by bogan on 2012-08-16
Hi!, **All,**

[COLOR=Blue]There is a new nvidia driver full released version 304.37, no longer a 'Beta', available [/COLOR]from nvidia downloads. It supports GeForce 6xxx series cards, and later.

If you have Optimus, Hybrid, with Integrated Graphics as well as a Nvidia card, see the note below.

 This Link is for the 32 bit version, check you get the correct one:
[http://www.nvidia.co.uk/object/linux-display-ia32-304.37-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-ia32-304.37-driver-uk.html)

If you already have a nvidia driver installed - not one of the  nvidia-current versions - it is now accessible using: ```
sudo  nvidia-installer --latest 
```  which now returns: v304.37 and the currently installed version, without altering anything.

So you can now install it with, from a TTY Terminal:  ```
sudo  nvidia-installer -f 
```Which will download it, un-install the  previous version and install the new, creating a new Xorg.conf file.
Or you can download it and run the .run file with 'sh'.

In either case you need to close the Xserver session first, using:  ```
sudo service lightdm stop
```I downloaded and installed it in  an updated version of 12.04 LTS  3.2.0-29-generic - not the pae version -  and it installed and ran  correctly with no problems on a GT 7650 card.

**[COLOR=Blue]For those with Integrated Graphics[/COLOR]**:  Extract from Nvidia's "Supported Products" notes:".... in particular,  notebook and all-in-one desktop designs with switchable  (hybrid) or  Optimus graphics will not work if means to disable the  integrated  graphics in hardware are not available. ...".

Chao!,** bogan.**

---

### Post by community on 2012-08-19
OK. Let me try that one.

---

### Post by community on 2012-08-19
This is the result of *lspci*


00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
01:00.0 3D controller:** NVIDIA Corporation GF119 [GeForce GT 520MX] (rev a1)**
02:00.0 Network controller: Intel Corporation Centrino Wireless-N 130 (rev 34)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)


So it recognized the card.Now what should I do? None of the drivers are installed presently.From where to start? Installing *nvidia-current* or something else?

---

### Post by bogan on 2012-08-19
Hi!, **community**,

Right, I see the nvidia card is not identified as a VGA controller, that's why the lspci cmd did not find it.

I am no expert on Hybrid graphics, and you will have seen the Nvidia note in my earlier Post.

However, you will need BumbleBee to keep a reasonable Battery life, and my understanding is that Bumblebee prefers to install the nvidia driver itself.

Perhaps someone who knows more about BumbleBee can advise you better; There are also the Links in **davidryderuk'**s Post.

Chao!,** bogan**.

---

