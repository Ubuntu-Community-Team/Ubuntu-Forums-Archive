---
title: "Unable to compleate kernel compilation"
date: 2010-02-02
forum: General Help
---

### Post by Lockheed on 2010-02-02
Here is what I am getting with any kernel I am attempting to compile these days:
[http://pastebin.com/m4bf1b30e](http://pastebin.com/m4bf1b30e)

I pasted as much as I could salvage from the terminal.
Any clues welcomed.


-------
**EDIT: I solved the problem!**
Details here: [http://ubuntuforums.org/showthread.php?p=8858881#post8858881](http://ubuntuforums.org/showthread.php?p=8858881#post8858881)

---

### Post by Lockheed on 2010-02-03
up

---

### Post by Lockheed on 2010-02-06
Tell me, friends, when did Ubuntu forums abandon helpfulness for disregard?

---

### Post by mushwars on 2010-02-06
Good news, I am probably the only other person here that compiles myown kernel. I will take a look at your log. just a sec.

looks like you need to upgrade this linux-image-2.6.32.7-exhibitiona
dont know what that is or what version you need to get.

---

### Post by Lockheed on 2010-02-06
> **mushwars said:**
> 
looks like you need to upgrade this linux-image-2.6.32.7-exhibitiona
dont know what that is or what version you need to get.

This is custom name for my new kernel. What do you mean by upgrade?

---

### Post by mushwars on 2010-02-06
I am not sure what it means, I dont compile my own kernel in debian, and that error is debian related, I just read the log. >  # The UTS Release version in include/linux/version.h #            "" # does not match current version: #            "2.6.32.7-exhibitiona" # Please correct this.  maybe if you pastebin your include/linux/version.h

---

### Post by Lockheed on 2010-02-14
include/linux/version.h
```
#define LINUX_VERSION_CODE 132640
#define KERNEL_VERSION(a,b,c) (((a) << 16) + ((b) << 8) + (c))

```

---

### Post by sandyd on 2010-02-14
> **Lockheed said:**
> include/linux/version.h
```
#define LINUX_VERSION_CODE 132640
#define KERNEL_VERSION(a,b,c) (((a) << 16) + ((b) << 8) + (c))

```
[http://linux.derkeiler.com/Mailing-Lists/Kernel/2006-07/msg05326.html](http://linux.derkeiler.com/Mailing-Lists/Kernel/2006-07/msg05326.html)
if your still having problems, you might want to check out the link in my sig (while substituting your kernel of course)

---

### Post by Lockheed on 2010-02-15
> **carlee said:**
> [http://linux.derkeiler.com/Mailing-Lists/Kernel/2006-07/msg05326.html](http://linux.derkeiler.com/Mailing-Lists/Kernel/2006-07/msg05326.html)


I am not sure I follow. Should I do this
```
Right after you get the error, modify
debian/ruleset/misc/version_vars.mk
```
after I get an error during compilation? Wouldn't it be little too late?

---

### Post by Lockheed on 2010-02-15
I tried the method from your sig but it resulted in unbootable kernel. Fatal error, something about not finding modules in /lib/....

---

### Post by Lockheed on 2010-02-15
I tried compiling newest rc with Master Kernel guide but it's the same thing as always:
```
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
run-parts: executing /etc/kernel/postinst.d/nvidia-common
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 20
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.33-rc8.postinst line 1186.
dpkg: error processing linux-image-2.6.33-rc8 (--install):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.33-rc8

```

---

### Post by noops on 2010-02-16
With 2.6.33 kernels you will need the kernel-package for lucid installed or your compile will fail near the end.

[http://packages.ubuntu.com/lucid/kernel-package](http://packages.ubuntu.com/lucid/kernel-package)

---

### Post by Lockheed on 2010-02-16
> **noops said:**
> With 2.6.33 kernels you will need the kernel-package for lucid installed or your compile will fail near the end.

[http://packages.ubuntu.com/lucid/kernel-package](http://packages.ubuntu.com/lucid/kernel-package)

I installed it and now installing compiled DEBs go a bit differently but ends the same:
```
/usr/src/linux# cd .. && dpkg -i linux*2.6.33-rc8*.deb
Selecting previously deselected package linux-headers-2.6.33-rc8.
(Reading database ... 156450 files and directories currently installed.)
Unpacking linux-headers-2.6.33-rc8 (from linux-headers-2.6.33-rc8_2.6.33-rc8-10.00.Custom_amd64.deb) ...
Selecting previously deselected package linux-image-2.6.33-rc8.
Unpacking linux-image-2.6.33-rc8 (from linux-image-2.6.33-rc8_2.6.33-rc8-10.00.Custom_amd64.deb) ...
Done.
Setting up linux-headers-2.6.33-rc8 (2.6.33-rc8-10.00.Custom) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.33-rc8           
 *  nvidia (180.44)...                                                          nvidia (180.44): Unable to locate /var/lib/dkms/nvidia/180.44/source/dkms.conf
	DKMS tree must be manually fixed.
                                                                         [fail]
 *  vboxdrv (3.1.4)...                                                          vboxdrv (3.1.4): Installing module.
................
......
                                                                         [ OK ]
 *  vboxnetadp (3.1.4)...                                                       vboxnetadp (3.1.4): Installing module.
........
......
                                                                         [ OK ]
 *  vboxnetflt (3.1.4)...                                                       vboxnetflt (3.1.4): Installing module.
........
......
                                                                         [ OK ]
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common

Setting up linux-image-2.6.33-rc8 (2.6.33-rc8-10.00.Custom) ...
Running depmod.
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
run-parts: executing /etc/kernel/postinst.d/nvidia-common
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 20
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.33-rc8.postinst line 341.
dpkg: error processing linux-image-2.6.33-rc8 (--install):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.33-rc8
```

---

### Post by Satoru-san on 2010-02-16
Wow. seriously, compiling your kernel means making it spacific to your system, here is what is looks like when I compile mine:

```
  LD      vmlinux
  SYSMAP  System.map
  SYSMAP  .tmp_System.map
  CC      arch/x86/boot/a20.o
  CC      arch/x86/boot/cmdline.o
  HOSTCC  arch/x86/boot/mkcpustr
  CPUSTR  arch/x86/boot/cpustr.h
  CC      arch/x86/boot/cpu.o
  CC      arch/x86/boot/cpucheck.o
  CC      arch/x86/boot/edd.o
  VOFFSET arch/x86/boot/voffset.h
  AS      arch/x86/boot/compressed/head_32.o
  CC      arch/x86/boot/compressed/misc.o
  OBJCOPY arch/x86/boot/compressed/vmlinux.bin
  HOSTCC  arch/x86/boot/compressed/relocs
  RELOCS  arch/x86/boot/compressed/vmlinux.relocs
  GZIP    arch/x86/boot/compressed/vmlinux.bin.gz
  HOSTCC  arch/x86/boot/compressed/mkpiggy
arch/x86/boot/compressed/mkpiggy.c: In function ‘main’:
arch/x86/boot/compressed/mkpiggy.c:65: &#35686;&#21578;: ignoring return value of ‘fread’, declared with attribute warn_unused_result
  MKPIGGY arch/x86/boot/compressed/piggy.S
  AS      arch/x86/boot/compressed/piggy.o
  LD      arch/x86/boot/compressed/vmlinux
  ZOFFSET arch/x86/boot/zoffset.h
  AS      arch/x86/boot/header.o
  CC      arch/x86/boot/main.o
  CC      arch/x86/boot/mca.o
  CC      arch/x86/boot/memory.o
  CC      arch/x86/boot/pm.o
  CC      arch/x86/boot/printf.o
  CC      arch/x86/boot/regs.o
  CC      arch/x86/boot/string.o
  CC      arch/x86/boot/tty.o
  CC      arch/x86/boot/video.o
  CC      arch/x86/boot/video-mode.o
  CC      arch/x86/boot/version.o
  CC      arch/x86/boot/video-vga.o
  CC      arch/x86/boot/video-vesa.o
  CC      arch/x86/boot/video-bios.o
  LD      arch/x86/boot/setup.elf
  OBJCOPY arch/x86/boot/setup.bin
  OBJCOPY arch/x86/boot/vmlinux.bin
  HOSTCC  arch/x86/boot/tools/build
  BUILD   arch/x86/boot/bzImage
Root device is (8, 3)
Setup is 12140 bytes (padded to 12288 bytes).
System is 4312 kB
CRC d84fb193
Kernel: arch/x86/boot/bzImage is ready  (#16)
  Building modules, stage 2.
  MODPOST 7 modules
  CC      arch/x86/kernel/test_nx.mod.o
  LD [M]  arch/x86/kernel/test_nx.ko
  CC      drivers/net/wireless/ipw2x00/ipw2200.mod.o
  LD [M]  drivers/net/wireless/ipw2x00/ipw2200.ko
  CC      drivers/net/wireless/ipw2x00/libipw.mod.o
  LD [M]  drivers/net/wireless/ipw2x00/libipw.ko
  CC      drivers/scsi/scsi_wait_scan.mod.o
  LD [M]  drivers/scsi/scsi_wait_scan.ko
  CC      net/wireless/lib80211_crypt_ccmp.mod.o
  LD [M]  net/wireless/lib80211_crypt_ccmp.ko
  CC      net/wireless/lib80211_crypt_tkip.mod.o
  LD [M]  net/wireless/lib80211_crypt_tkip.ko
  CC      net/wireless/lib80211_crypt_wep.mod.o
  LD [M]  net/wireless/lib80211_crypt_wep.ko
  INSTALL arch/x86/kernel/test_nx.ko
  INSTALL drivers/net/wireless/ipw2x00/ipw2200.ko
  INSTALL drivers/net/wireless/ipw2x00/libipw.ko
  INSTALL drivers/scsi/scsi_wait_scan.ko
  INSTALL net/wireless/lib80211_crypt_ccmp.ko
  INSTALL net/wireless/lib80211_crypt_tkip.ko
  INSTALL net/wireless/lib80211_crypt_wep.ko
  DEPMOD  2.6.31-gentoo-r6
```

you have like 600 modules o_O

---

### Post by Lockheed on 2010-02-17
> **Satoru-san said:**
> Wow. seriously, compiling your kernel means making it spacific to your system

you have like 600 modules o_O

Yeah, well I cut as many as I could by guessing since there is no list of what module is necessary for my, say, SATA interface.
Besides, I used this set of modules for 4 kernels between 2.6.29 and 2.6.31 and never had any problems.

---

### Post by Klondikes on 2010-02-17
> Yeah, well I cut as many as I could by guessing since there is no list of what module is necessary for my, say, SATA interface.

easy fix (with time and patience). use lsmod and lspci as follows:

```

sudo lsmod > lsmod_output
sudo lspci -vv > lspci_output
```

lsmod lists modules in use; lspci lists PCI devices among other hardware info. use man or google for more info on these commands.

the output of lsmod and lspci is stored in lsmod_output and lspci_output respectively through the use of ">". (i'm not sure what you already know; for completeness sake) listed below is one of several sections for my SATA driver:

```

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
	Subsystem: Intel Corporation Device 5842
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx+
	Latency: 0
	Interrupt: pin A routed to IRQ 18
	Region 0: I/O ports at 01f0 [size=8]
	Region 1: I/O ports at 03f4 [size=1]
	Region 2: I/O ports at 0170 [size=8]
	Region 3: I/O ports at 0374 [size=1]
	Region 4: I/O ports at 30b0 [size=16]
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix
```

take note of the "Kernel modules" and "Kernel driver in use" lines. these lines should indicate a respective module in the kernel config.

thus for my SATA driver, i ensured AT least CONFIG_ATA_PIIX in my .config was set as "m" for module. of course, other modules may be necessary, so take some time to read the documentation about each module. btw, running

```

make xconfig
```

shows priceless documentation for each item.

---

### Post by Satoru-san on 2010-02-17
> **Klondikes said:**
> 
```

make xconfig
```shows priceless documentation for each item.
XCONFIG?! ?! !!

```
localhost linux # make xconfig
  CHECK   qt
*
* Unable to find the QT3 installation. Please make sure that
* the QT3 development package is correctly installed and
* either install pkg-config or set the QTDIR environment
* variable to the correct location.
*
sed < scripts/kconfig/lkc_proto.h > scripts/kconfig/lkc_defs.h 's/P(\([^,]*\),.*/#define \1 (\*\1_p)/'
  HOSTCC  scripts/kconfig/kconfig_load.o
make[1]: *** `scripts/kconfig/qconf.o' &#12395;&#24517;&#35201;&#12394;&#12479;&#12540;&#12466;&#12483;&#12488; `scripts/kconfig/.tmp_qtcheck' &#12434; make &#12377;&#12427;&#12523;&#12540;&#12523;&#12364;&#12354;&#12426;&#12414;&#12379;&#12435;.  &#20013;&#27490;.
make: *** [xconfig] &#12456;&#12521;&#12540; 2

```

No xconfig for me :<

---

### Post by Klondikes on 2010-02-17
xconfig is bound to be in one of these packages:

```
sudo apt-get install build-essential bin86 kernel-package libqt3-headers libqt3-mt-dev wget libncurses5 libncurses5-dev
```

most probably libqt3-headers and libqt3-mt-dev judging by the package names.

quoted from the Master Kernel Thread:
[http://ubuntuforums.org/showthread.php?t=311158]("http://ubuntuforums.org/showthread.php?t=311158")

---

### Post by Lockheed on 2010-02-18
Ok, thank you for clarifying how to cut down on the modules.

However, this valuable knowledge is useless to me until someone tells me how to fix my problem with kernel compilation!

---

### Post by Lockheed on 2010-02-18
> **Klondikes said:**
> 
lsmod lists modules in use; lspci lists PCI devices among other hardware info. use man or google for more info on these commands.

the output of lsmod and lspci is stored in lsmod_output and lspci_output respectively through the use of ">". (i'm not sure what you already know; for completeness sake) listed below is one of several sections for my SATA driver:

Does it mean I only need to select modules that appear in those output files? For example, in lspci_output there is RAM section but no module is named until few paragraphs lower (Kernel driver in use: pcieport-driver).

---

### Post by Klondikes on 2010-02-18
> **Lockheed said:**
> Does it mean I only need to select modules that appear in those output files? For example, in lspci_output there is RAM section but no module is named until few paragraphs lower (Kernel driver in use: pcieport-driver).

not necessarily. eliminating modules requires some trial and error. you'll have to read the documentation, note correlations between config items and module names, etc., and still you may run into issues.

---

### Post by Lockheed on 2010-02-21
**I solved the problem!**
Details here: [http://ubuntuforums.org/showthread.php?p=8858881#post8858881](http://ubuntuforums.org/showthread.php?p=8858881#post8858881)

---

