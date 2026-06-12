---
title: "software startup failure afer fglrx installation"
date: 2012-05-26
forum: General Help
---

### Post by zottimoises on 2012-05-26
Hi;
I have ubuntu 11.04 x86 and before fglrx driver installation (amd-driver-installer-12-4-x86.x86_64.run)  all software and packages were running fine; however after fglrx installation the sybylx package failed to startup;

All files are initialised as before but the nothing prompts up;


root@moises-workstation:/tripos/sybylx1.2/sybylx1.2/bin/linux# ./sybyl_launcher.sh
./sybyl_launcher.sh
/tripos/sybylx1.2/sybylx1.2/bin/linux
TA_LICENSE = /tripos/sybylx1.2/AdminTools11.6
 
SYBYL-X 1.2 (linux_os2x), Created Jul 13, 2010 01:59:58 AM
Application Path: "/tripos/sybylx1.2/sybylx1.2/bin/linux" 
Executing: "/tripos/sybylx1.2/sybylx1.2/bin/linux/sybyl.exe" 
root@moises-workstation:/tripos/sybylx1.2/sybylx1.2/bin/linux# 


PS:
root@moises-workstation:/tripos/sybylx1.2/sybylx1.2/bin/linux# lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
root@moises-workstation:/tripos/sybylx1.2/sybylx1.2/bin/linux# 

any suggestion?
moises;

---

### Post by steeldriver on 2012-05-26
uninstall it and revert to the non-proprietary fglrx from the repository?

---

### Post by gamblor01 on 2012-05-26
Maybe check to see if there are errors in the kernel's message buffer.  You could try something like:

```

dmesg | tail -n 100

```


That will show you the last 100 lines of the buffer.  If you're ever stuck on a virtual terminal with no graphics at all then you can use SHIFT+PGUP and SHIFT+PGDN to scroll up and down pages and read the output.

Unfortunately I have had nothing but problem with ATI cards.  I was given a laptop at work with an ATI card and I finally gave up trying to get the proprietary drivers to work.  I eventually got it to boot and work, but then I could never get it to handle the dual monitors appropriately when the laptop was docked.  So annoying...but the non-proprietary drivers have worked fine for me.  They handle everything I need them to do (I'm not gaming on the laptop).  If you plan to game then you'll need 3D acceleration and you'll want the proprietary drivers.  :|

Let's check what dmesg says.  Maybe something useful will show up there?  Or maybe look in /var/log/messages...I don't know if either one with show anything but it's worth a shot.

---

### Post by zottimoises on 2012-05-26
> **gamblor01 said:**
> Maybe check to see if there are errors in the kernel's message buffer.  You could try something like:

```

dmesg | tail -n 100

```
That will show you the last 100 lines of the buffer.  If you're ever stuck on a virtual terminal with no graphics at all then you can use SHIFT+PGUP and SHIFT+PGDN to scroll up and down pages and read the output.

Unfortunately I have had nothing but problem with ATI cards.  I was given a laptop at work with an ATI card and I finally gave up trying to get the proprietary drivers to work.  I eventually got it to boot and work, but then I could never get it to handle the dual monitors appropriately when the laptop was docked.  So annoying...but the non-proprietary drivers have worked fine for me.  They handle everything I need them to do (I'm not gaming on the laptop).  If you plan to game then you'll need 3D acceleration and you'll want the proprietary drivers.  :|

Let's check what dmesg says.  Maybe something useful will show up there?  Or maybe look in /var/log/messages...I don't know if either one with show anything but it's worth a shot.


Hello [gamblor01]("http://ubuntuforums.org/member.php?u=826773");

Thanks four your attention:
see below the output:
 I can not see anything wrong;:confused:


root@moises-workstation:/tripos/sybylx1.2/sybylx1.2/bin/linux# ./sybyl_launcher.sh
./sybyl_launcher.sh
/tripos/sybylx1.2/sybylx1.2/bin/linux
TA_LICENSE = /tripos/sybylx1.2/AdminTools11.6
 
SYBYL-X 1.2 (linux_os2x), Created Jul 13, 2010 01:59:58 AM
Application Path: "/tripos/sybylx1.2/sybylx1.2/bin/linux" 
Executing: "/tripos/sybylx1.2/sybylx1.2/bin/linux/sybyl.exe" 
root@moises-workstation:/tripos/sybylx1.2/sybylx1.2/bin/linux# dmesg | tail -n 100
[    8.518916] type=1400 audit(1338031726.875:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=611 comm="apparmor_parser"
[    8.518935] type=1400 audit(1338031726.875:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=451 comm="apparmor_parser"
[    8.519481] type=1400 audit(1338031726.875:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=611 comm="apparmor_parser"
[    8.519522] type=1400 audit(1338031726.875:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=451 comm="apparmor_parser"
[    8.520397] type=1400 audit(1338031726.879:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=452 comm="apparmor_parser"
[    8.521278] type=1400 audit(1338031726.879:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=452 comm="apparmor_parser"
[    8.521847] type=1400 audit(1338031726.879:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=452 comm="apparmor_parser"
[    8.740027] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    8.740088] HDA Intel 0000:00:1b.0: irq 48 for MSI/MSI-X
[    8.740117] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    9.286681] hda_codec: ALC262: SKU not ready 0x411111f0
[    9.293060] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[    9.293141] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[    9.293298] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    9.293367] HDA Intel 0000:01:00.1: irq 49 for MSI/MSI-X
[    9.293393] HDA Intel 0000:01:00.1: setting latency timer to 64
[    9.308214] hda-intel: Enable sync_write for AMD chipset
[   10.243585] vesafb: framebuffer at 0xc0000000, mapped to 0xf9a80000, using 5824k, total 5824k
[   10.243590] vesafb: mode is 1400x1050x32, linelength=5632, pages=0
[   10.243592] vesafb: scrolling: redraw
[   10.243594] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[   10.243670] fbcon: VESA VGA (fb0) is primary device
[   10.243778] Console: switching to colour frame buffer device 175x65
[   10.243817] fb0: VESA VGA frame buffer device
[   11.197484] EXT3-fs (sda1): using internal journal
[   11.505639] EXT3-fs: barriers not enabled
[   11.505821] kjournald starting.  Commit interval 5 seconds
[   11.505977] EXT3-fs (sda9): using internal journal
[   11.505983] EXT3-fs (sda9): mounted filesystem with ordered data mode
[   12.132324] EXT3-fs: barriers not enabled
[   12.178325] kjournald starting.  Commit interval 5 seconds
[   12.180475] EXT3-fs (sda10): using internal journal
[   12.180479] EXT3-fs (sda10): mounted filesystem with ordered data mode
[   12.719928] EXT3-fs: barriers not enabled
[   12.720111] kjournald starting.  Commit interval 5 seconds
[   12.720250] EXT3-fs (sda5): using internal journal
[   12.720254] EXT3-fs (sda5): mounted filesystem with ordered data mode
[   12.938958] EXT3-fs: barriers not enabled
[   12.939138] kjournald starting.  Commit interval 5 seconds
[   12.939371] EXT3-fs (sda6): using internal journal
[   12.939376] EXT3-fs (sda6): mounted filesystem with ordered data mode
[   13.324353] EXT3-fs: barriers not enabled
[   13.333255] kjournald starting.  Commit interval 5 seconds
[   13.340965] EXT3-fs (sda11): using internal journal
[   13.340968] EXT3-fs (sda11): mounted filesystem with ordered data mode
[   13.771226] EXT3-fs: barriers not enabled
[   13.771419] kjournald starting.  Commit interval 5 seconds
[   13.771587] EXT3-fs (sda7): using internal journal
[   13.771592] EXT3-fs (sda7): mounted filesystem with ordered data mode
[   14.820134] EXT3-fs: barriers not enabled
[   14.820324] kjournald starting.  Commit interval 5 seconds
[   14.820459] EXT3-fs (sda8): using internal journal
[   14.820463] EXT3-fs (sda8): mounted filesystem with ordered data mode
[   14.926806] EXT3-fs: barriers not enabled
[   14.926994] kjournald starting.  Commit interval 5 seconds
[   14.927177] EXT3-fs (sda12): using internal journal
[   14.927180] EXT3-fs (sda12): mounted filesystem with ordered data mode
[   17.414573] ppdev: user-space parallel port driver
[   17.995967] type=1400 audit(1338031736.356:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=838 comm="apparmor_parser"
[   17.997012] type=1400 audit(1338031736.356:12): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=838 comm="apparmor_parser"
[   18.374745] type=1400 audit(1338031736.732:13): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=848 comm="apparmor_parser"
[   18.375637] type=1400 audit(1338031736.732:14): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=848 comm="apparmor_parser"
[   18.376321] type=1400 audit(1338031736.736:15): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=848 comm="apparmor_parser"
[   18.540420] type=1400 audit(1338031736.900:16): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=847 comm="apparmor_parser"
[   18.545122] type=1400 audit(1338031736.904:17): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=853 comm="apparmor_parser"
[   18.546155] type=1400 audit(1338031736.904:18): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=853 comm="apparmor_parser"
[   18.584166] type=1400 audit(1338031736.944:19): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=854 comm="apparmor_parser"
[   19.204287] type=1400 audit(1338031737.564:20): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=849 comm="apparmor_parser"
[   22.095656] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.109053] sky2 0000:08:00.0: eth0: enabling interface
[   22.109262] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.774171] sky2 0000:08:00.0: eth0: Link is up at 100 Mbps, full duplex, flow control both
[   23.774330] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   26.472597] Bluetooth: L2CAP ver 2.15
[   26.472600] Bluetooth: L2CAP socket layer initialized
[   26.539107] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   26.539110] Bluetooth: BNEP filters: protocol multicast
[   26.936553] Bluetooth: SCO (Voice Link) ver 0.6
[   26.936556] Bluetooth: SCO socket layer initialized
[   27.594347] Bluetooth: RFCOMM TTY layer initialized
[   27.594353] Bluetooth: RFCOMM socket layer initialized
[   27.594355] Bluetooth: RFCOMM ver 1.11
[   29.242531] fglrx_pci 0000:01:00.0: irq 50 for MSI/MSI-X
[   29.243313] [fglrx] Firegl kernel thread PID: 1195
[   29.243391] [fglrx] Firegl kernel thread PID: 1196
[   29.243461] [fglrx] Firegl kernel thread PID: 1197
[   29.243644] [fglrx] IRQ 50 Enabled
[   30.013358] [fglrx] Gart USWC size:1248 M.
[   30.013361] [fglrx] Gart cacheable size:494 M.
[   30.013367] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   30.013369] [fglrx] Reserved FB block: Unshared offset:fc17000, size:3e9000 
[   30.013372] [fglrx] Reserved FB block: Unshared offset:1fffb000, size:5000 
[   34.544041] eth0: no IPv6 routers present
[   41.097134] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   65.326733] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[  136.270081] input: Targus Optical BT Laptop Mouse as /devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1:1.0/bluetooth/hci0/hci0:11/input11
[  136.270226] generic-bluetooth 0005:3938:1001.0001: input,hidraw0: BLUETOOTH HID v1.02 Mouse [Targus Optical BT Laptop Mouse] on 00:26:43:AC:CD:0E
[  151.138438] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[ 2025.582969] cfg80211: Found new beacon on frequency: 5180 MHz (Ch 36) on phy0
[ 2025.582981] cfg80211: Pending regulatory request, waiting for it to be processed...
root@moises-workstation:/tripos/sybylx1.2/sybylx1.2/bin/linux#

---

### Post by zottimoises on 2012-05-26
> **gamblor01 said:**
> Maybe check to see if there are errors in the kernel's message buffer.  You could try something like:

```

dmesg | tail -n 100

```
That will show you the last 100 lines of the buffer.  If you're ever stuck on a virtual terminal with no graphics at all then you can use SHIFT+PGUP and SHIFT+PGDN to scroll up and down pages and read the output.

Unfortunately I have had nothing but problem with ATI cards.  I was given a laptop at work with an ATI card and I finally gave up trying to get the proprietary drivers to work.  I eventually got it to boot and work, but then I could never get it to handle the dual monitors appropriately when the laptop was docked.  So annoying...but the non-proprietary drivers have worked fine for me.  They handle everything I need them to do (I'm not gaming on the laptop).  If you plan to game then you'll need 3D acceleration and you'll want the proprietary drivers.  :|

Let's check what dmesg says.  Maybe something useful will show up there?  Or maybe look in /var/log/messages...I don't know if either one with show anything but it's worth a shot.



Hello [gamblor01]("http://ubuntuforums.org/member.php?u=826773");

/var/log/messages:


May 25 14:52:32 moises-workstation kernel: [  393.154812] show_signal_msg: 6 callbacks suppressed
May 25 14:52:32 moises-workstation kernel: [  393.154817] sybyl.exe[18497]: segfault at 42c ip b22ab836 sp bf918bec error 4 in libGL.so.1.2[b22a9000+5000]
May 25 14:52:44 moises-workstation kernel: Kernel logging (proc) stopped.



May 25 17:53:13 moises-workstation kernel: [  485.471007] show_signal_msg: 6 callbacks suppressed
May 25 17:53:13 moises-workstation kernel: [  485.471013] sybyl.exe[24981]: segfault at 42c ip b22a4836 sp bfdb986c error 4 in libGL.so.1.2[b22a2000+5000]
May 25 17:55:04 moises-workstation kernel: [  597.010631] sybyl.exe[30467]: segfault at 42c ip b2180836 sp bff24aec error 4 in libGL.so.1.2[b217e000+5000]

---

### Post by gamblor01 on 2012-05-27
> **zottimoises said:**
> Hello [gamblor01]("http://ubuntuforums.org/member.php?u=826773");

/var/log/messages:


May 25 14:52:32 moises-workstation kernel: [  393.154812] show_signal_msg: 6 callbacks suppressed
May 25 14:52:32 moises-workstation kernel: [  393.154817] sybyl.exe[18497]: segfault at 42c ip b22ab836 sp bf918bec error 4 in libGL.so.1.2[b22a9000+5000]
May 25 14:52:44 moises-workstation kernel: Kernel logging (proc) stopped.



May 25 17:53:13 moises-workstation kernel: [  485.471007] show_signal_msg: 6 callbacks suppressed
May 25 17:53:13 moises-workstation kernel: [  485.471013] sybyl.exe[24981]: segfault at 42c ip b22a4836 sp bfdb986c error 4 in libGL.so.1.2[b22a2000+5000]
May 25 17:55:04 moises-workstation kernel: [  597.010631] sybyl.exe[30467]: segfault at 42c ip b2180836 sp bff24aec error 4 in libGL.so.1.2[b217e000+5000]


The segfault there is the problem.  It means that the program did something wrong and is now trying to access a portion of memory that it does not have access to or does not exist.  You can see more information here:

[http://en.wikipedia.org/wiki/Segmentation_fault](http://en.wikipedia.org/wiki/Segmentation_fault)



You should check your ulimit values, specifically the -c option which is for core dumps.  However, if you wish to list them all at the same time, then you can just run:

```
ulimit -a
```


Unfortunately this is something that a developer for Tripos, or possibly the ATI drivers will have to look into.  One thing I find odd however -- are you running this under Wine?  It shows sybyl.exe in the output there, but you were launching it from a shell script so I guess they just name their Linux executables with a .exe on the end?  Very odd.

Your best course of action here is really to try this:

1. Set your core file size to ulimited:

```
ulimit -c unlimited
```

2. Launch the program and let it segfault:

```
./sybyl_launcher.sh
```

3. Find the core file that was generated.  Typically it will be named something like "core" but you can locate it as the most recently updated file in your current directory.  It should be the last line shown in the following command:

```
ls -lrt
```



Then report a bug to Tripos and attach that core file to it.  They may wind up saying it's a bug with the ATI drivers though -- I don't know.  If you really want to be extra helpful in the bug report then you can use gdb to obtain a stack trace showing which functions were called before it ultimately crashed.  You would have to do something like this:

```

$ sudo apt-get install gdb
$ gdb ./sybyl_launcher.sh core
> bt
> quit

```


The "bt" command in gdb should produce a backtrace which will show the flow of execution.  Without debugging symbols you usually cannot do much else, but if they have the core file then their developers should be able to debug it.

If I were you, I would uninstall those ATI drivers and just go with what you had previously.  It may take a long time to get an answer.  Good luck.

---

