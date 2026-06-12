---
title: "Installation of Virtual system"
date: 2011-02-05
forum: General Help
---

### Post by marort on 2011-02-05
I would like to run Win XP or 7 under my Ubuntu 10.04 LTS Lucid Lynk. Very likely running Virtual Box. Before I do this I have some questions.
Can I run this on a laptop or does it have to be a server?
Can I use a brand name OS disc (HP, Dell, etc,) or does it have to be the full edition?

---

### Post by dino99 on 2011-02-05
run what you like, that dont matter, only check that you have enough free hdd space and enough ram to run it smootly

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by marort on 2011-02-05
Thank you Dino99

---

### Post by techunit on 2011-02-05
You technically can't use a OEM disk but I don't think it will stop you from trying. I mean you could run in to legal problems.

---

### Post by marort on 2011-02-05
So, techunit, are you saying that if I got a laptop and it came with Win7 originally but later I decided I want to wipe out this OS and install Ubuntu with Vmware (or any other virtual app) running the original OS is illegal? Thank you.

---

### Post by techunit on 2011-02-05
Um technically?? Hum thats an interesting point. It is still on your computer that you bought it with. And you could argue that. So I would go a head with it. Its not like your going to get caught. Really recommend virtualbox

good luck

---

### Post by coldraven on 2011-02-06
My HP laptop had XP preloaded and came with a restore disc, that's the OEM sort which does not have a serial number on it.
The problem you get is that when it installs it looks for some data in the BIOS which generate the activation key.
If you just install in a fresh VirtualBox the activation will fail because VBox presents a fake BIOS to the guest OS.
However, you can get the info from your BIOS and configure VBox to present this instead.
Read this [http://www.virtualbox.org/manual/ch09.html#changedmi](http://www.virtualbox.org/manual/ch09.html#changedmi)
Then with the info you got from dmidecode edit this script 
```
#! /bin/bash
VM_NAME="xp01" # Name of your Virtual Machine
VSETED="VBoxManage setextradata $VM_NAME"
CFG_PATH="VBoxInternal/Devices/pcbios/0/Config"
$VSETED $CFG_PATH/DmiBIOSVendor       "Hewlett-Packard"
$VSETED $CFG_PATH/DmiBIOSVersion      "F.0C"
$VSETED $CFG_PATH/DmiBIOSReleaseDate  "06/05/2008"
$VSETED $CFG_PATH/DmiBIOSReleaseMajor  "15"
$VSETED $CFG_PATH/DmiBIOSReleaseMinor  "12"
$VSETED $CFG_PATH/DmiBIOSFirmwareMajor "113"
$VSETED $CFG_PATH/DmiBIOSFirmwareMinor "45"
$VSETED $CFG_PATH/DmiSystemVendor     "Hewlett-Packard"
$VSETED $CFG_PATH/DmiSystemProduct    "HP Compaq 6715b"
$VSETED $CFG_PATH/DmiSystemVersion    "<RK154AV>"
$VSETED $CFG_PATH/DmiSystemSerial     "XXXXXXXXXX"
$VSETED $CFG_PATH/DmiSystemUuid       "XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX"
$VSETED $CFG_PATH/DmiSystemFamily     "103C_5336AN"
```
Run this script after making your virtual disc but before you install XP. This script was on the VBox forum, I've forgotten the poster's name but thanks anyway
This works for XP, I have no idea about Win7

---

### Post by techunit on 2011-02-06
Actually for most OEM disks you can look at the bottom you your computer for the serial number! LOL

---

### Post by coldraven on 2011-02-07
> **techunit said:**
> Actually for most OEM disks you can look at the bottom you your computer for the serial number! LOL

Not when your laptop was a "downgrade" from Vista to XP you can't!
My sticker says Vista Business Edition, I also extracted two different numbers from the existing XP installation before I deleted it.
None of the three numbers would activate XP!
Believe me, I spent hours on this problem. I only use XP for Sketchup and I don't want to run Wine. Windows is best kept in a box!

---

### Post by techunit on 2011-02-07
> **coldraven said:**
> Not when your laptop was a "downgrade" from Vista to XP you can't!
My sticker says Vista Business Edition, I also extracted two different numbers from the existing XP installation before I deleted it.
None of the three numbers would activate XP!
Believe me, I spent hours on this problem. I only use XP for Sketchup and I don't want to run Wine. Windows is best kept in a box!
Your situation suggests bias so perhaps he will have better luck.

---

### Post by slooksterpsv on 2011-02-07
I've been running VirtualBox for a while. I've used other as well. You can run Virtual Machines on pretty much any system that there's an emulator for.

I used to run Bochs on an AMD Duron 1.1ghz with 384MB RAM, used to allocate 128MB RAM for Linux and that. Course Bochs was a bit more difficult as it was more CLI and not GUI'ed (until the GUIs started rolling out).

Overall, I run VirtualBox on an AMD Athlon II X2 2.4GHz with 4GB of RAM, I allocate like 1024MB (1GB) to a VM, sometimes less sometimes more, and they run great. I have even used my Windows 7 key on the bottom of my PC to activate it in VirtualBox - its a license, it's on the same machine, so what if it's virtualized, they don't like it, they can go fly a kite.

So you can VM on any machine, heck I've even done VMs on a 900MHz (680MHz actual) intel Celeron (the EEE PC's, the first ones).

---

