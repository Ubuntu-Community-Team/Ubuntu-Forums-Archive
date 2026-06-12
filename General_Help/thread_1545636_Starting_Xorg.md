---
title: "Starting Xorg"
date: 2010-08-04
forum: General Help
---

### Post by sideaway on 2010-08-04
I've been having issues logging on;

So I reset the X server... I now get the following upon trying to /etc/init.d/gdm start;

Ubuntu is running in low graphics mode

The following error was encountered. You may need to update your configuration to solve this.

(EE) GLX error: Can not get required symbols.
(EE) Microsoft Microsoft (R) SideWinderTM x6 Keyboard: failed to initialise for relative axes.

---

### Post by dragos240 on 2010-08-04
Hi, could you give us your video specs? Ex. Open up a terminal (ctrl + alt + f1) login, and type lspci.

Look for the VGA controller line. We may be able to help you there. It looks like your keyboard is causing you some trouble, in the meantime, look for a more bland PS/2 keyboard or simple USB keyboard.

---

### Post by sideaway on 2010-08-04
ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Device 6898
01:00.1 Audio device: ATI Technologies Inc Cypress HDMI Audio [Radeon HD 5800 Series]
03:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 02)
03:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 02)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)


That was taken from a live environment.

I have an HD5870.

---

### Post by sideaway on 2010-08-04
I'm on the verge of doing a windows and reinstalling - I've got a serparate home partition and am desperate to get to my e-mails asap.

---

### Post by Sylos on 2010-08-04
Hi there.
Im by no means an expert but have you tried reconfiguring the xserver from where you are? It could just be a messed up Xorg file.

```
sudo dpkg-reconfigure xserver-xorg


```

That might lead you somewhere.

---

### Post by sideaway on 2010-08-04
Thank you for the suggestion, but yes I have tried that :)

Was one of the first things I tried.

---

### Post by Sylos on 2010-08-04
Have you tried fully purging/removing then reinstalling the xserver as well?

---

### Post by sideaway on 2010-08-04
No I have not!

---

### Post by Sylos on 2010-08-04
If you dont mind the risk you could try the following:


```
sudo apt-get remove --purge xserver-xorg
```

then..

```
sudo apt-get install xserver-xorg
```

then...

```
sudo dpkg-reconfigure xserver-xorg
```

I suppose if your xserver is not running anyway you arent really risking anything.

Sorry if im pitching below your level and you know all this already.

---

