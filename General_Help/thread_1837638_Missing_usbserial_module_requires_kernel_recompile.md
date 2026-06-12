---
title: "Missing usbserial module requires kernel recompile?"
date: 2011-09-02
forum: General Help
---

### Post by HarriU11-04 on 2011-09-02
Hello

If this is the wrong forum category my apologies, but I do not know where else to put it.

Basic problem: Cannot connect to Internet

System: Ubuntu Server 11.04 running Linux 2.6.38-8-virtual (F4 from install screen->Install a minimal virtual machine). I chose Basic Server Setup for the type of server install.

I want to use Vodafone(UK) 3G modem to connect (rebranded Huawei). I know this works perfectly fine for a Desktop install with GUI/NetworkManager/etc. But "Ubuntu Server" = no GUI and no NetworkManager. 

The usb modem is detected as a CD-ROM/usb storage, but doesn't 'switch over' to a modem, module usbserial is not loaded on boot. Running "modprobe usbserial" tells me the module is missing, and usbserial is not listed if I do "lsmod".

Do I need to recompile the kernel??? If I do, it sounds like a daunting task, and I would probably go back to a Desktop edition.

---

### Post by gandaran on 2011-09-02
> The usb modem is detected as a CD-ROM/usb storage, but doesn't 'switch over' to a modem
install usb-modeswitch and usb-modeswitch-data
and install wvdial too to setup the 3g connection if you don't want the network manager or any gui install.

---

### Post by HarriU11-04 on 2011-09-02
> **gandaran said:**
> install usb-modeswitch and usb-modeswitch-data
and install wvdial too to setup the 3g connection if you don't want the network manager or any gui install.
Thank you for responding.
usb-modeswitch and usb-modeswitch-data are already installed. wvdial will not work because /dev/ttyUSB* do not exist because usbserial is not there. I -think- this is the reason modeswitch does not work either, because /dev/ttyUSB is missing.

I've resolved this now by creating a different Server install, still minimal but not the virtual machine option. lsmod is showing usbserial and I have ttyUSB0 and ttyUSB1 now :) And I have connectivity from the virtual machine while the host machine does not (how bizarre!)

Obviously there's a difference between the two images, but whether its down to packages or the kernel is beyond my limited knowledge.

---

### Post by gandaran on 2011-09-02
> Obviously there's a difference between the two images, but whether its down to packages or the kernel is beyond my limited knowledge.
that is the virtual machine problem not the ubuntu server, usb devices usually don't work on virtual machines unless the virtual machine has some options/settings that can make them work.

---

