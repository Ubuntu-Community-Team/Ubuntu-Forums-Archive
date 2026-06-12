---
title: "Need Help Setting Up RAID 5"
date: 2010-10-02
forum: General Help
---

### Post by Jimcando on 2010-10-02
I recently got a little box running Ubuntu Server 10.04. It has a Jetway JNC92-330 motherboard with a [4x SATA daughterboard]("http://www.jetway.com.tw/jw/ipcboard_view.asp?productid=625") attached.

Ubuntu is installed and running fine on a separate hard drive connected to a SATA port on the motherboard, and I've tried plugging 4 2TB hard drives in through the daughterboard.

When the computer turns on, before Ubuntu boots, it gives me the option to create a RAID array, which I have done and it says it's active, but Ubuntu can't see it.

From what I gather, I might either need to install some drivers for the daughterboard (of which I can't find any) or set it up using fakeraid (which I'm not sure how to go about)

Any help in which direction to go, and how to go about it would be greatly appreciated, thanks :D

---

### Post by SeijiSensei on 2010-10-02
When you say you set up RAID, I presume you mean you used the hardware RAID controller on the daughterboard?

Try turning off hardware RAID and see whether Ubuntu recognizes the individual drives themselves.  If so, you can use the software RAID code that comes in the Linux kernel to build the array yourself.  You can find more details at [https://raid.wiki.kernel.org/index.php/Linux_Raid](https://raid.wiki.kernel.org/index.php/Linux_Raid).

---

### Post by Jimcando on 2010-10-02
Yeh, I was thinking about doing that.

Can't do it now though, so I'll try again later :D

---

### Post by Jimcando on 2010-10-02
I have deleted the RAID array and tried booting with all the drives still attached through the daughterboard. Ubuntu still can't see them. 

I don't know whether it's any use, but in the BIOS, it metions the hard drives currently connected. It lists all 4 drives as SCSI (when set in an array, it just lists it as one SCSI drive)

---

### Post by SeijiSensei on 2010-10-02
Type "sudo dmesg" in Alt-F2 or a Terminal.  Look for lines like these in the result:

```
[    1.841896] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.841954] sd 0:0:0:0: [sda] Write Protect is off
[    1.841956] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.841958] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.841980] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA

```

You should see entries for sdb, sdc, etc., if Linux is recognizing all the drives.  If they don't appear, the problem could be in a number of places -- the computer's main BIOS, the BIOS on the daughterboard, or the absence of an appropriate driver in Linux.  Usually the last of these isn't the problem as long as the drive controller presents a standard interface to the operating system.

This is actually a SATA drive, but Linux nowadays handles all types of drives as if they were SCSI devices.  This happened with the arrival of SATA devices.

---

### Post by Jimcando on 2010-10-03
I have tried that and there does seem to be a problem. No other drives such as sdb, sdc etc are showing.

Since I've no idea what to do, I did a little playing around to try get you some more information.

I tried plugging just my boot drive in through the daughterboard, and it managed to start booting. It got through GRUB, but then gave me this error message:

> 
Gave up waiting for root device. Common problems:
- Boot args (ct /proc/cmdline)
  - Check rootdelay= (did the system wait long enough?)
  - check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/mapper/server-root does not exist. Dropping to a shell!


Then I put the boot drive back into the motherboard, and tried running it without anything plugged into the daughterboard. When I run dmesg I notice this:
> 
[    1.376623] pata_marvell 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.376724] pata_marvell 0000:03:00.0: setting latency timer to 64
[    1.378998] scsi2 : pata_marvell
[    1.379456] scsi3 : pata_marvell
which doesn't appear if the daughterboard isn't plugged in, so I guess it can at least see the board.

Then as soon as I plug in another hard drive through the daughterboard, I start getting these error messages:
> 
[*randomnumber*] ata4: SRST failed (errno=-16)


Thanks for helping me out here, and I'm sorry if I've missed anything important :D

---

### Post by SeijiSensei on 2010-10-03
Did a little searching around the Jetway site and found a Linux driver for the daughterboard here: [http://www.jetwaycomputer.com/Daughter_Board.html](http://www.jetwaycomputer.com/Daughter_Board.html)

I'm assuming it's the ADPE4S since that's the one Jetway says is related to your motherboard.

---

### Post by Jimcando on 2010-10-03
Ahhhh, fantastic!

I thought I'd looked on the website for a driver, but I clearly failed, thank you so much.

One, hopefully, last question (since I'm already clearly in need of the help), is it just a simple 'sudo make install' to get these to work, or is it more complex to install drivers?

**EDIT:** just tried using 'make' and I get this error:
> 
make ARCH=x86_64 CC=cc LD=ld CROSS_COMPILE= V= -C /lib/modules/2.6.32-25-generic/build M=`pwd` modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-25-generic'
make[1]: *** No rule to make target `code'. Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-25-generic'
make: *** [all] Error 2


**EDIT 2:** Trying to make sense of the Readme file, I ran this code:
"sudo make KERNEL_SRC=/usr/src/linux-headers-2.6.32-25-generic"
but this gives a similar error:
> 
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
make[1]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'. Stop.
make: *** [prepare0] Error 2


---

### Post by SeijiSensei on 2010-10-03
Looks like you might need to install the entire kernel source tree. Perhaps this is relevant: [http://ubuntuforums.org/showthread.php?t=1047374](http://ubuntuforums.org/showthread.php?t=1047374)

Just installing kernel-headers-[your kernel version] doesn't seem sufficient.  The driver apparently needs access to the entire source tree.

I've used "locate" to find bounds.c on both some CentOS 5.5 machines I maintain and my Ubuntu machines without much luck.  If the bug reports don't help, maybe Jetway can.  Tell the support staff you want to install the driver on Ubuntu (looks like they only support Red Hat/SuSE directly).  Maybe they can help.

---

### Post by Jimcando on 2010-10-04
I know you said to contact Jetway, and I have, but I thought I'd just put this here as well.

I installed the source but now I get this error
> make ARCH=x86_64 CC=cc LD=ld CROSS_COMPILE= V= -C /usr/src/linux-source-2.6.32 M=`pwd` modules
make[1]: Entering directory `/usr/src/linux-source-2.6.32'

  ERROR: Kernel configuration is invalid.
         include/linux/autoconf.h or include/config/auto.conf are missing.
         Run 'make oldconfig && make prepare' on kernel src to fix it.

make[1]: *** No rule to make target `code'. Stop.
make[1]: Leaving directory `/usr/src/linux-source-2.6.32'
make: *** [all] Error 2


I tried using 'make oldconfig && make prepare', but that didn't help

I also tried copying the autoconf.h and auto.conf from the headers folder, but it just gave the previous "*** No rule to make target `code'. Stop." error

---

### Post by Jimcando on 2010-10-04
*EDIT: Nevermind*

How does one normally install a driver such as this for Ubuntu? I've never done it before and would like to actually know what is supposed to happen.

(Also, Jetway still haven't replied :()

Update:
I've been talking to someone else on another forum, and he pointed me to [http://kmuto.jp/debian/hcl/](http://kmuto.jp/debian/hcl/) . It implies that the drivers are already installed. If this is true, then I guess it puts me right back at the start where Ubuntu can't see the hard drives.

---

### Post by Jimcando on 2010-10-05
ARGH.

I've managed to get Ubuntu to see the drives through the daugtherboard. But only sometimes.
Sometimes it will appear, but other times it won't be there after a reboot.

I'm getting increasingly angry with this. I have no idea why it might work one minute, then not the next.

---

