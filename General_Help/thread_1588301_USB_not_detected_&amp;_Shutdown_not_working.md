---
title: "USB not detected &amp; Shutdown not working"
date: 2010-10-04
forum: General Help
---

### Post by Cpierce on 2010-10-04
I am listing both problems on one post because what I have read, they may be related. I am working on a Compaq Presario SR1603WM. I have installed 10.04 three times thinking I may have gotten a poor install. The computer has two issues and everything else appears to be working properly. The main problem is that the USB's aren't detected. There are 4 on the back and three on the front. They have power, but the computer doesn't detect when a drive is inserted. The card reader does not work either. The second problem is that when you shutdown the computer, it hangs on the "purple Ubuntu" screen until you press and hold the power button. Restart works just fine. Here are the things I have tried so far:

*Enable & disable USB legecy support in BIOS
*disable auto-login
*Make sure OpenOffice quickstarter is not running
*Change /etc/default/grub with the acpi=force
*In system>admin>Hardware there are no drivers activated
*I went to /etc/X11/xorg.conf to delete the "driver vesa" line, but xorg.conf was empty. 
*all of the shutdown commands - shutdown-p, sudo init0, sudo poweroff shut down the computer, but it still hangs on the "purple Ubuntu" screen. 
* lsusb shows no usb devices. 

If anyone has any ideas, PLEASE let me know. I will gladly post any command lines that will help

---

### Post by oregonbob on 2010-10-04
Did you try lsusb command?

---

### Post by r+9 on 2010-10-04
I've actually been wondering how I might force Ubuntu/Linux to reconsider my USB devices.

I've recently discovered an odd thing.  My laptop uses but does not identify my mouse (lsub has a blank descriptor) and when I plug in my usb headset it won't register until I've unplugged my mouse.

I can then re-plug in my mouse to have the use of both.

Not sure how to address that one.

I haven't run into a shutdown problem before, but it could be related, There should be (I don't know it) a way to get all the shutdown spam that shows things shutting down properly, perhaps someone else knows.

---

### Post by Cpierce on 2010-10-04
OregonBob, Are you talking about a different lsusb command other than what I talked about in my original post ? If I just type lsusb in terminal, nothing is listed. If I need to do something different, please let me know.

---

### Post by andrewthomas on 2010-10-04
That is weird that lsusb shows no devices.  

What about
```

sudo lshw -short
```

---

### Post by Cpierce on 2010-10-04
Andrew, i will run that tomorrow when I am back on it. It is weird. With all of my google reading, it looks like an issue with older HP/Compaq with 9.10 and 10.04. 9.04 is supposed to work, and I plan on installing it just to see. I really want 10.04 to work. Someone among the great people of the forum will know the answer.

---

### Post by andrewthomas on 2010-10-04
How old is the BIOS?

---

### Post by jfed on 2010-10-04
You could try shutting down in the cli using the following command.
```
sudo shutdown -h now
```

Did you try mounting the USB? To do so use this code:
```
sudo mount /dev/sdb1 ~/usb
```

---

### Post by Cpierce on 2010-10-04
Andrew, I will check the BIOS version tomorrow as well. the computer is from 2005, so not really old.

Jfed, I did try the "sudo shutdown -h now". It did shut down, until it got to the purple ubuntu screen, then it hangs. I will try that USB command. If I could get the USB's working, I could live with the shutdown problem.

---

### Post by Cpierce on 2010-10-05
Andrew, 
The BIOS is Phoenix 3.08, 9/13/2005

The lshw -short command:

H/W path           Device      Class          Description
=========================================================
                               system         ED861AA-ABA SR1603WM NA540
/0                             bus            Amberine M
/0/0                           memory         128KiB BIOS
/0/4                           processor      AMD Sempron(tm) Processor 3200+
/0/4/b                         memory         128KiB L1 cache
/0/4/d                         memory         256KiB L2 cache
/0/5                           processor      CPU
/0/5/0                         memory         128KiB L1 cache
/0/5/1                         memory         256KiB L2 cache
/0/2000                        memory         1MiB BIOS
/0/28                          memory         1280MiB System Memory
/0/28/0                        memory         256MiB DIMM DDR 400 MHz (2.5 ns)
/0/28/1                        memory         1GiB DIMM DDR 400 MHz (2.5 ns)
/0/28/2                        memory         DIMM [empty]
/0/28/3                        memory         DIMM [empty]
/0/100                         bridge         RS480 Host Bridge
/0/100/1                       bridge         RS480 PCI Bridge
/0/100/1/5                     display        RS480 [Radeon Xpress 200G Series]
/0/100/12                      storage        IXP SB400 Serial ATA Controller
/0/100/13                      bus            IXP SB400 USB Host Controller
/0/100/13.1                    bus            IXP SB400 USB Host Controller
/0/100/13.2                    bus            IXP SB400 USB2 Host Controller
/0/100/14                      bus            IXP SB400 SMBus Controller
/0/100/14.1        scsi0       storage        IXP SB400 IDE Controller
/0/100/14.1/0      /dev/sda    disk           80GB HDS728080PLAT20
/0/100/14.1/0/1    /dev/sda1   volume         71GiB EXT4 volume
/0/100/14.1/0/2    /dev/sda2   volume         3152MiB Extended partition
/0/100/14.1/0/2/5  /dev/sda5   volume         3152MiB Linux swap / Solaris parti
/0/100/14.1/1      /dev/cdrom  disk           COMBO SOHC-4836K
/0/100/14.3                    bridge         IXP SB400 PCI-ISA Bridge
/0/100/14.4                    bridge         IXP SB400 PCI-PCI Bridge
/0/100/14.4/5                  bus            VT6306/7/8 [Fire II(M)] IEEE 1394 
/0/100/14.4/9                  communication  HSF 56k Data/Fax Modem
/0/100/14.4/a      eth0        network        Gigabit Network Adapter
/0/100/14.5                    multimedia     IXP SB400 AC'97 Audio Controller
/0/101                         bridge         K8 [Athlon64/Opteron] HyperTranspo
/0/102                         bridge         K8 [Athlon64/Opteron] Address Map
/0/103                         bridge         K8 [Athlon64/Opteron] DRAM Control
/0/104                         bridge         K8 [Athlon64/Opteron] Miscellaneou


Hope this provides some clues !

Jfed, when I run 
sudo mount /dev/sdb1 ~/usb

it says mount point doesn't exist.

---

### Post by jfed on 2010-10-05
> **Cpierce said:**
> 
Jfed, when I run 
sudo mount /dev/sdb1 ~/usb

it says mount point doesn't exist.

Wow, thats intriguing. Now I'm no elitist, but what that seems like to me is...that either those USB ports are just rubbish all together, or Ubuntu isn't recognizing the ports whatsoever...

Sorry mate that terminal command was about all I was worth, hope you fix it sooner or later.:)

---

### Post by Cpierce on 2010-10-05
I installed 9.04 just to check. Some of the reading said this issue was on 10.04 and 9.10 only, but 9.04 had the same issues. So I slapped on win7 just to try, and the USB's and shutdown worked just fine. 

HOWEVER, I don't want to run windows, so I am counting on someone knowing how to fix this.

---

