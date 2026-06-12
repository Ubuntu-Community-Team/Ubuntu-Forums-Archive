---
title: "CodeWarrior Startup crash"
date: 2010-08-05
forum: General Help
---

### Post by AlexBR on 2010-08-05
I am a Ubuntu 10.4 Linux User (32 bits)! I installed the CodeWarrior Development Studio v10. The installation was OK. However, I am getting an error when I run cwide (see below). The problem seems to be in the library libpemicro_jloaderh.so.
 
Can someone help me?
 
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb17fb230, pid=2450, tid=2999868272
#
# JRE version: 6.0_20-b02
# Java VM: Java HotSpot(TM) Client VM (16.3-b01 mixed mode, sharing linux-x86 )
# Problematic frame:
# C  [libpemicro_jloaderh.so+0x137230]
#
# An error report file with more information is saved as:
# /home/alex/hs_err_pid2450.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#

---

### Post by lengau on 2010-10-06
I'm not sure if you're still interested, but I ran into this problem recently.

If you're not using PEMicro's BDM (or any of their other hardware, you can delete (or move) the shared objects. Here's what I did:

```
lengau@Atlantis:/usr/local/Freescale/CodeWarrior_MCU_10.0/eclipse/plugins$ sudo mkdir ../../backup
lengau@Atlantis:/usr/local/Freescale/CodeWarrior_MCU_10.0/eclipse/plugins$ sudo mv com.pemicro.* ../../backup
lengau@Atlantis:/usr/local/Freescale/CodeWarrior_MCU_10.0/eclipse/plugins$ cd ..
lengau@Atlantis:/usr/local/Freescale/CodeWarrior_MCU_10.0/eclipse$ ./cwide
```

It seems to be working for the moment.

Best of luck!

---

### Post by skywatcher on 2010-10-13
Hi 

I don't think my problem is directly related to the subject of this thread, but I hope that someone might help.

I recently installed the CodeWarrior Development Studio v10 on my computer (Ubuntu 9.10). It seems OK - I can set up a new project and the compiler works etc., except for one major problem: it doesn't see the PEMicro Multilink BDM, which means I cannot program and debug.

When I run the dmesg command, I can see that the system detected the BDM, besides the fact that the blue LED is on:

```
[ 2865.912057] usb 5-1: new full speed USB device using uhci_hcd and address 3
[ 2866.125252] usb 5-1: configuration #1 chosen from 1 choice
```

I know that the BDM works, because I tested it on a Windows installation. Looking under /usr/local/Freescale and /usr/local/PEMicrocomputerSystems it would appear that all the necessary drivers have been installed.

Can anyone shed light on this problem?

---

### Post by jcottier on 2011-03-08
I installed CW 10.0 SE on Ubuntu 10.04 (32 bit), and it would crash every time it tried to run. There was a java error related to PEmicro. I have since installed CW 10.1 SE and that runs fine, except that is could not find the USB multilink. I found that running the driver builder/installer "sudo /usr/local/Freescale/CodeWarrior_MCU_10.1/Drivers/pemicro/setup.sh" as root made it work. This also updated its firmware so that functionality is also in Linux. But it would not survive a reboot. The modules windriver6 and windriver6_usb always appear to be loaded, but the device /dev/windriver6 does not appear until you run the script "sudo /usr/local/Freescale/CodeWarrior_MCU_10.1/Drivers/pemicro/windriver/redist//wdreg windrvr6 auto", and then you have to change its permissions EG sudo chmod 666 /dev/windrvr6. Its a cludge but it works on my machine.

---

