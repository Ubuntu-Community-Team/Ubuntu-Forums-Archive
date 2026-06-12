---
title: "Trying to install ATI Driver (9.04)"
date: 2009-08-30
forum: General Help
---

### Post by Russell_S on 2009-08-30
Hi, I'm running Ubuntu 9.04 and am trying to install the proprietary ATI drivers as documented here "[https://help.ubuntu.com/community/BinaryDriverHowto/ATI"]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")  in the Ubuntu documentation.

I am trying to enable the accelerated ATI graphics driver in the 'Hardware Drivers' (System->Hardware drivers) as shown but have the following problems when entering the following commands in a terminal window.

> sudo dpkg-reconfigure -phigh linux-restricted-modules-`uname -r`
sudo insmod /lib/modules/`uname -r`/volatile/fglrx.kowhich returns the following:

> russell@ubuntu-desktop:~$ sudo dpkg-reconfigure -phigh linux-restricted-modules-`uname -r`
[sudo] password for russell: 
update-initramfs: Generating /boot/initrd.img-2.6.28-15-generic
russell@ubuntu-desktop:~$ sudo insmod /lib/modules/`uname -r`/volatile/fglrx.ko
insmod: can't read '/lib/modules/2.6.28-15-generic/volatile/fglrx.ko': No such file or directory
So I don't know where to go from here. I have the folder "/lib/modules/2.6.28-15-generic/volatile" present but there is no "fglrx.ko" file in that folder.

Does anyone have any suggestions as to how to overcome this please.


Many thanks

Russell

---

### Post by P4man on 2009-08-30
are you sure your card is supported? What card do you have?
If in doubt, type:

```
lspci
```

in a terminal and paste the result here.

---

### Post by sanorj on 2009-08-30
I'm with this same problem...

```
sudo insmod /lib/modules/`uname -r`/volatile/fglrx.ko
insmod: can't read '/lib/modules/2.6.28-15-generic/volatile/fglrx.ko': No such file or directory
```

My lspci

```
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]
```

PS: I'm doing this because i'm trying to run a unix game and getting this error:

```
X Error of failed request:  BadDrawable (invalid Pixmap or Window parameter)
  Major opcode of failed request:  136 (XFree86-DRI)
  Minor opcode of failed request:  7 ()
  Resource id in failed request:  0x4000008
  Serial number of failed request:  66
  Current serial number in output stream:  66

```

If not I didnt need this installation because i'm watching videos and browsing my ubuntu very Ok.

Thanks,
Leonardo

---

### Post by DougieFresh4U on 2009-08-30
Maybe have a read through 
[http://ubuntuforums.org/showthread.php?t=1114168](http://ubuntuforums.org/showthread.php?t=1114168)

---

### Post by P4man on 2009-08-30
> **sanorj said:**
> I'm with this same problem...

My lspci

```
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]
```

[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.25&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.25&lang=English)

Your videocard is no longer supported by the recent ATI drivers, and you need those to support X.org version in jaunty.

You basically have the choice between being stuck with ubuntu 8.10,  using the opensource ati drivers, or upgrading your videocard. A forth option is downgrading your xorg,  its not recommended, though it could work.

---

### Post by Russell_S on 2009-08-30
Hi & thanks for the replies.

Here is the output of lspci

> russell@ubuntu-desktop:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
01:07.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
01:07.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
02:00.0 VGA compatible controller: ATI Technologies Inc RV570 [Radeon X1950 Pro] (rev 9a)
02:00.1 Display controller: ATI Technologies Inc RV570 [Radeon X1950 Pro] (secondary) (rev 9a)
russell@ubuntu-desktop:~$ 
I can't find any release notes for the latest 9.8 ATI drivers to see if my card is supported. As shown it is a X1950Pro.


Regards

Russell

---

### Post by P4man on 2009-08-31
You're in the same boat as the other poster Im afraid. Your card is on the list of cards no longer supported (see my link above).

---

### Post by Russell_S on 2009-08-31
Thanks very much for the reply.

I realize where I was going wrong now. I was searching on the ATI site for the latest drivers, entering the relevant info (OS & graphics card) and it was just showing the 9.3 drivers and couldn't understand why it wasn't showing anything later like the 9.8 ones. I didn't even consider that my card wouldn't be supported in the later drivers. When I entered a later graphics card into the list it then came up with the 9.8 drivers so I could then access the release notes and see the supported cards list.

As it happens, I'm currently waiting for a ATI HD3870X2 graphics card to be delivered that I bought of eBay, so I will try again when that card is in and running.

I obviously wasn't thinking straight at the time and I'm sorry to have wasted your time.


Best regards

Russell

---

