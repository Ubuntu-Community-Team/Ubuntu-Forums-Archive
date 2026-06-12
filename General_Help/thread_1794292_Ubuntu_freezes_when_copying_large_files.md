---
title: "Ubuntu freezes when copying large files"
date: 2011-06-30
forum: General Help
---

### Post by paracaidista18 on 2011-06-30
System keeps freezing when I try to copy files over 1gb, copy and paste in Nautilus or using cp produce the same affect. After a while the system becomes unresponsive, I've left it in this state for and hour but it never came back. After restart, I can see that it never copy more than 1gb.

Please help, this is the first time I use Linux and love it but this issue is very annoying, I have restated the system dozens of times.

System is a Vaio YB15 with Ubuntu Natty x64, file system is EXT4, please tell me if you need more data or logs files.


Thanks in advance and excuse my english.


**Update:**

I tracked down the problem to virtualbox: problem gone after ubuntu reinstall but reappeared as before after installing VirtualBox. I haven't found a solution yet.

---

### Post by sandman887 on 2011-07-01
Without being there to run memtest86, or other memory diagnostic tools, my preliminary suspicion is that you may have some corrupt RAM. However, I cannot be sure that's what it is. I'd suggest running a few diagnostic tools like testing memory and your hard drive.

---

### Post by paracaidista18 on 2011-07-01
hi sandman,

I forgot to mention, but I have run memtest86 and found no problems. Also, I booted with a live CD and ran fsck-f, all partitions passed the five check phases without problems. Is there any more test that I can run?

I do not know what to do, everyday tasks such as internet works fine, but just copying a file of a couple of gigabytes freezes the system.

---

### Post by paracaidista18 on 2011-07-01
I booted with a liveCD and was able to copy files without problems. There must be some incompatibility with installed applications, but how I can figure out which one is causing this problem? Can I get this from system logs?

---

### Post by zitch on 2011-07-01
Are you trying to copy a file to/from a network drive (Via NFS, SSHFS, or SMB) or is this a local hd-to-hd copy?

If you were trying to copy a file from a network and it's going over a Realtek NIC, you might be hitting [this bug](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/746914) if your system is getting hard-locked (no mouse or keyboard response at all, only thing you can do is hold down the power button for a hard-shutdown or pull the power plug). I've been hitting this issue with the exact card in the title (Realtek RTL8111/8168B Gigabit), the work-arounds I have to to use is to either use wireless, or force the card to work at 100 Mbps speeds (by using a switch).  This seemed to be a recent change for me, so it might have been introduced in a kernel update at some point; I distinctly remember transferring files at gigabit speeds to be stable several weeks ago.  I'm running Ubuntu 10.04 64-bit. 

If it's a local hd-to-hd copy, is it copying to-from the same physical drive, or a different drive?

---

### Post by paracaidista18 on 2011-07-01
System freezes when I try to copy to-from the same physical drive. First the hd led turns off and system becomes unresponsive, then I lose mouse and keyboard.

---

### Post by zitch on 2011-07-01
Well, let's start with what kind of controller your system has and your kernel version.  Run the following commands and paste the results here:

uname -a

lspci


Especially look for any lines that specify IDE or SATA.  For example, here's what mine looks like:

```

nick@kanae:~$ uname -a
Linux kanae 2.6.32-32-generic #62-Ubuntu SMP Wed Apr 20 21:52:38 UTC 2011 x86_64 GNU/Linux
nick@kanae:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
**00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)**
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GT200 [GeForce GTX 260M] (rev a2)
06:00.0 Network controller: Intel Corporation PRO/Wireless 5300 AGN [Shiloh] Network Connection
07:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
07:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
07:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
07:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
nick@kanae:~$
```

Also, the next time your system locks up, note the time, reboot, and look in /var/log/syslog around the time it locked up to see if there's any clues.

---

### Post by paracaidista18 on 2011-07-01
```
vg@vg-VPCYB15AL:~/Documents/log$ uname -a
Linux vg-VPCYB15AL 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

vg@vg-VPCYB15AL:~/Documents/log$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] Pavilion DM1Z-3000 Host bridge
00:01.0 VGA compatible controller: ATI Technologies Inc Device 9802
00:01.1 Audio device: ATI Technologies Inc Device 1314
00:04.0 PCI bridge: Advanced Micro Devices [AMD] Device 1512
00:06.0 PCI bridge: Advanced Micro Devices [AMD] Device 1514
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (rev 40)
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
01:00.0 Ethernet controller: Atheros Communications AR8131 Gigabit Ethernet (rev c0)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

```There is nothing in syslog, the last record was prior to the time I started the file copy

Thanks for your help

---

### Post by zitch on 2011-07-01
Unfortunately, searching for your SATA controller model doesn't reveal anything. The closest I could find was [this bug report](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/583539) for Lucid and transferring between two different local hard-drives, but supposedly the Maverick kernel fixed it. And you're not having problems when you boot from a LiveCD, which seems to possibly point to a kernel upgrade causing the problem.  

As one at least one last attempt, get the kernel version off of the LiveCD (boot the cd and run *uname -a* there), and try a few more copy attempts there to confirm that the lockup doesn't manifest from the LiveCD.

Hopefully, someone much smarter than I can figure it out; I'd suggest doing more searches on [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu), then [submit a bug](https://help.ubuntu.com/community/ReportingBugs) if you don't find anything specifically matching your issue and hardware.

Sorry I'm not much help here.

---

### Post by paracaidista18 on 2011-07-01
I assumed that the SATA controller was not the cause of the error as it is the same used on the LiveCD. By now the only thing I found that freezes the system is copying files and I'm pretty sure that doesn't happen with the livecd.

I think I'll be reinstalling ubuntu and installing the programs one by one to see if I find the culprit. Thanks again.

---

### Post by linuxuser12345 on 2011-07-01
Maybe it is just because the file is so large, it causes the program watching the progress of it stop responding, as it is using more system resources for actually getting the job done.
It sounds crazy, but that has happened to me.

---

### Post by paracaidista18 on 2011-07-01
No, I left it an hour to copy a 1.5GB file and never responded, but booting with LiveCD it can handle files over 20gb without issues.

---

### Post by linuxuser12345 on 2011-07-01
Omg, nevermind! lol
Have you tried running a different version of your distro?

---

### Post by soulcat on 2011-07-01
hi

i ave a similar problem copy & paste from hd to a memory stick or pen drive mainly say a divx film where it will reach say a 99% then freeze so i normaly use windows to do this job.


ubuntu 10.10

---

### Post by dcstar on 2011-07-04
> **paracaidista18 said:**
> System keeps freezing when I try to copy files over 1gb, copy and paste in Nautilus or using cp produce the same affect. After a while the system becomes unresponsive, I've left it in this state for and hour but it never came back. After restart, I can see that it never copy more than 1gb.

Please help, this is the first time I use Linux and love it but this issue is very annoying, I have restated the system dozens of times.

System is a Vaio YB15 with Ubuntu Natty x64, file system is EXT4, please tell me if you need more data or logs files.


Thanks in advance and excuse my english.

You can try the Ubuntu instructions in this post:

[http://www.webupd8.org/2010/11/alternative-to-200-lines-kernel-patch.html](http://www.webupd8.org/2010/11/alternative-to-200-lines-kernel-patch.html)

---

### Post by woodcab on 2011-07-04
I want to copy a large file (4.3 gigs) to a flash drive (8 gigs). Every time I try to copy it says the disk is full even though the file is smaller than the room on the drive. I have windows XP. I am able to copy the file to other parts of my HD drive

Regards,
[wooden file cabinets](http://www.woodenfilecabinets.net)

---

### Post by paracaidista18 on 2011-07-04
OK, I believe I tracked down the problem to virtualbox: problem completly gone after ubuntu reinstall but reappeared as before after installing VirtualBox. Tried virtualbox and virtualbox OSE, both have the same effect.

Is there anything I can do? I really need virtualbox installed on this pc.

---

### Post by dcstar on 2011-07-05
> **woodcab said:**
> I want to copy a large file (4.3 gigs) to a flash drive (8 gigs). Every time I try to copy it says the disk is full even though the file is smaller than the room on the drive. I have windows XP. I am able to copy the file to other parts of my HD drive


Let me guess, the 4.3GB file is been copied to a FAT32 filesystem with a 4GB maximum file size limit?

---

### Post by paracaidista18 on 2011-07-05
> **dcstar said:**
> You can try the Ubuntu instructions in this post:

[http://www.webupd8.org/2010/11/alternative-to-200-lines-kernel-patch.html](http://www.webupd8.org/2010/11/alternative-to-200-lines-kernel-patch.html)


Hi dcstar, appreciate your help. I installed the patch you recomend, but it didn't solve the problem. Any idea of what may be the problem?

---

