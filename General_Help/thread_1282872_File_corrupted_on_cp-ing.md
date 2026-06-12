---
title: "File corrupted on cp-ing"
date: 2009-10-04
forum: General Help
---

### Post by RazvanP on 2009-10-04
Hi there,

I have a very odd issue with copying files on Ubuntu 9.04 (tried both Ubuntu and Kubuntu, both are 64 bit). After copying a file, the target file is not identical with the souce one.

Here is the source file:
```

razvan@kub:~$ md5sum /media/disk/home/razvan/kubuntu-9.04-desktop-amd64.iso
798b8789af2f13bb9687b2ce57f25f9c  /media/disk/home/razvan/kubuntu-9.04-desktop-amd64.iso

```Here is how I copy, checksum and compare:
```

razvan@kub:~$ cp /media/disk/home/razvan/kubuntu-9.04-desktop-amd64.iso .
razvan@kub:~$ md5sum kubuntu-9.04-desktop-amd64.iso
0c2098be8871986caf78c07f30f27d42  kubuntu-9.04-desktop-amd64.iso
razvan@kub:~$ cmp -b kubuntu-9.04-desktop-amd64.iso /media/disk/home/razvan/kubuntu-9.04-desktop-amd64.iso
kubuntu-9.04-desktop-amd64.iso /media/disk/home/razvan/kubuntu-9.04-desktop-amd64.iso differ: byte 549001, line 1554 is 111 I 151 i

```Or another attempt:
```

razvan@kub:~$ cp /media/disk/home/razvan/kubuntu-9.04-desktop-amd64.iso .
razvan@kub:~$ md5sum kubuntu-9.04-desktop-amd64.iso
a2cc9e50cfbcc085420aa43346cd15e7  kubuntu-9.04-desktop-amd64.iso
razvan@kub:~$ cmp -b kubuntu-9.04-desktop-amd64.iso /media/disk/home/razvan/kubuntu-9.04-desktop-amd64.iso
kubuntu-9.04-desktop-amd64.iso /media/disk/home/razvan/kubuntu-9.04-desktop-amd64.iso differ: byte 421724297, line 1536634 is 203 M-^C 243 M-#

```I tried to copy from/to NTFS, VFAT and ext4, with the same results. What I find also interesting, although the position within the target of the first different byte is variable, the difference between the target and souce value is always 40!

Does anybody experienced such abnormal behaviour? FIrst I have believed the error occurs because of errors in networking, but the problem got narrowed even on copying on the same file system.

Since the checksums are computed each time the same, I assume the issue is on writing the data.

I hope I don't have to replace the whole motherboard, as an attempt to fix the defective southbridge.

---

### Post by RazvanP on 2009-10-05
A follow up: I tried to copy from/to different hardware (connected on S-ATA and USB). The behavior is the same no matter what storage hardware it is used. The memory test indicated no errors (it ran for an hour); I will try to tweak the parameters of FSB or any other southbridge related parameter.

---

### Post by geirha on 2009-10-05
I suggest tailing some log files while you copy. See if you see any I/O errors during the copying. I don't remember if they'll show up in syslog or not, so maybe check dmesg as well.
```
tail -F /var/log/syslog
dmesg | tail 
```

Also, just to be sure, cp isn't overridden by a function or alias or anything is it?
```
$ type cp
cp is /bin/cp

```

---

### Post by RazvanP on 2009-10-05
Thanks for the reply, geirha.

Regarding the cp, it looks good:

```

razvan@kub:~$ type cp
cp is hashed (/bin/cp)
razvan@kub:~$ ls -al /bin/cp
-rwxr-xr-x 1 root root 84768 2008-06-26 20:31 /bin/cp
razvan@kub:~$

```Regarding the syslog:

```

razvan@kub:~$ tail -F /var/log/syslog
Oct  5 09:32:00 kub kernel: [   74.631112] EXT4-fs: mounted filesystem with ordered data mode.
Oct  5 09:33:09 kub kernel: [  143.136487] /dev/vmmon[5442]: PTSC: initialized at 2399907000 Hz using TSC
Oct  5 09:33:33 kub kernel: [  167.152211] /dev/vmnet: open called by PID 5445 (vmware-vmx)
Oct  5 09:33:33 kub kernel: [  167.152227] /dev/vmnet: port on hub 1 successfully opened
Oct  5 09:36:50 kub kernel: [  363.724026] vmmon: Had to deallocate locked 36561 pages from vm driver ffff88006aca8c00
Oct  5 09:36:50 kub kernel: [  363.725505] vmmon: Had to deallocate AWE 3345 pages from vm driver ffff88006aca8c00
Oct  5 09:40:01 kub /USR/SBIN/CRON[5473]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Oct  5 09:50:01 kub /USR/SBIN/CRON[5661]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Oct  5 10:00:01 kub /USR/SBIN/CRON[6173]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Oct  5 10:00:01 kub /USR/SBIN/CRON[6175]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
^C
razvan@kub:~$ dmesg | tail
[   74.626648] EXT4 FS on sda1, internal journal on sda1:8
[   74.626649] EXT4-fs: delayed allocation enabled
[   74.626651] EXT4-fs: file extents enabled
[   74.631109] EXT4-fs: mballoc enabled
[   74.631112] EXT4-fs: mounted filesystem with ordered data mode.
[  143.136487] /dev/vmmon[5442]: PTSC: initialized at 2399907000 Hz using TSC
[  167.152211] /dev/vmnet: open called by PID 5445 (vmware-vmx)
[  167.152227] /dev/vmnet: port on hub 1 successfully opened
[  363.724026] vmmon: Had to deallocate locked 36561 pages from vm driver ffff88006aca8c00
[  363.725505] vmmon: Had to deallocate AWE 3345 pages from vm driver ffff88006aca8c00


```So there are no I/O error; even if an IO error would occur, cp won't finish successfully.
Also, the issue does not occur on cp only, even if the file gets copied with Dolphin or downloaded with Firefox, both report a successful operation but the MD5 sum is usually wrong.


I tried the same experiment multiple times, here is what I got:
```

/media/disk-1/home/razvan/kubuntu-9.04-desktop-amd64.iso kubuntu-9.04-desktop-amd64.iso differ: byte 379301961, line 1392539 is 277 M-? 237 M-^_                                                                    
razvan@kub:~$ cp /media/disk-1/home/razvan/kubuntu-9.04-desktop-amd64.iso . ; md5sum kubuntu-9.04-desktop-amd64.iso; cmp -b /media/disk-1/home/razvan/kubuntu-9.04-desktop-amd64.iso kubuntu-9.04-desktop-amd64.iso 
14aadcc7f09e4c0c394c40284dfcaed0  kubuntu-9.04-desktop-amd64.iso                                                                                                                                                    
/media/disk-1/home/razvan/kubuntu-9.04-desktop-amd64.iso kubuntu-9.04-desktop-amd64.iso differ: byte 115560521, line 435874 is 264 M-4 224 M-^T                                                                     
razvan@kub:~$ cp /media/disk-1/home/razvan/kubuntu-9.04-desktop-amd64.iso . ; md5sum kubuntu-9.04-desktop-amd64.iso; cmp -b /media/disk-1/home/razvan/kubuntu-9.04-desktop-amd64.iso kubuntu-9.04-desktop-amd64.iso 
04261a307dd85e34256693568f57df94  kubuntu-9.04-desktop-amd64.iso                                                                                                                                                    
/media/disk-1/home/razvan/kubuntu-9.04-desktop-amd64.iso kubuntu-9.04-desktop-amd64.iso differ: byte 41840713, line 161096 is  74 <  34 ^\                                                                          
razvan@kub:~$ cp /media/disk-1/home/razvan/kubuntu-9.04-desktop-amd64.iso . ; md5sum kubuntu-9.04-desktop-amd64.iso; cmp -b /media/disk-1/home/razvan/kubuntu-9.04-desktop-amd64.iso kubuntu-9.04-desktop-amd64.iso 
030ec8297326ec716f911d720fe7fda0  kubuntu-9.04-desktop-amd64.iso                                                                                                                                                    
/media/disk-1/home/razvan/kubuntu-9.04-desktop-amd64.iso kubuntu-9.04-desktop-amd64.iso differ: byte 111226953, line 419450 is 265 M-5 225 M-^U                                                                     
razvan@kub:~$ cp /media/disk-1/home/razvan/kubuntu-9.04-desktop-amd64.iso . ; md5sum kubuntu-9.04-desktop-amd64.iso; cmp -b /media/disk-1/home/razvan/kubuntu-9.04-desktop-amd64.iso kubuntu-9.04-desktop-amd64.iso 
c2b077f4eb014e2d01ab07fad01439b4  kubuntu-9.04-desktop-amd64.iso                                                                                                                                                    
/media/disk-1/home/razvan/kubuntu-9.04-desktop-amd64.iso kubuntu-9.04-desktop-amd64.iso differ: byte 46284937, line 178148 is 142 b 102 B                                                                           
razvan@kub:~$ cp /media/disk-1/home/razvan/kubuntu-9.04-desktop-amd64.iso . ; md5sum kubuntu-9.04-desktop-amd64.iso; cmp -b /media/disk-1/home/razvan/kubuntu-9.04-desktop-amd64.iso kubuntu-9.04-desktop-amd64.iso 
98f8817294e4b529ae4f271ef73e4b06  kubuntu-9.04-desktop-amd64.iso                                                                                                                                                    
/media/disk-1/home/razvan/kubuntu-9.04-desktop-amd64.iso kubuntu-9.04-desktop-amd64.iso differ: byte 710717577, line 2537428 is 155 m 115 M                                                                         
razvan@kub:~$ cp /media/disk-1/home/razvan/kubuntu-9.04-desktop-amd64.iso . ; md5sum kubuntu-9.04-desktop-amd64.iso; cmp -b /media/disk-1/home/razvan/kubuntu-9.04-desktop-amd64.iso kubuntu-9.04-desktop-amd64.iso 
5b6c3ed01270419813bea176162188fb  kubuntu-9.04-desktop-amd64.iso                                                                                                                                                    
/media/disk-1/home/razvan/kubuntu-9.04-desktop-amd64.iso kubuntu-9.04-desktop-amd64.iso differ: byte 225607753, line 844767 is  42 "   2 ^B 
```

---

### Post by RazvanP on 2009-10-05
Also I have tried to reduce the FSB frequency, in multiple steps, i have tried fail-safe bios settings, I have replaced the video card (just testing) but the issue is still here. I will try today another OS, although I am pretty sure this is a hardware issue now.

---

### Post by CatKiller on 2009-10-05
It probably wouldn't hurt to run memtest, just in case.

---

### Post by RazvanP on 2009-10-05
i have memtested, also I have replaced the video card, tried to check different BIOS settings, changed the harddrive and performed the same test on USB hard drive and memory stick.

---

### Post by RazvanP on 2009-10-09
A follow up of the issue:
- I have tried a few live cds (Ubuntu 9.04 64 bit) and sysrescuecd, this is a 32 bit distribution. The issue was encountered in both cases. Further I have installed Windows XP (a very old version i have, i think with no service pack) and the motherboard drivers (for performance reasons). The files are now properly copied, even if I run Linux in a Virtual Box.
I am pretty frustrated to run everything from the virtual machine, but this seems the only viable way for now.

---

### Post by geirha on 2009-10-09
Then it sounds very much like a problem with linux's driver for your (s)ata controller. A bug report at [https://bugs.launchpad.net/ubuntu/+source/linux](https://bugs.launchpad.net/ubuntu/+source/linux) sounds like the way to go to get it fixed.

---

### Post by RazvanP on 2009-10-10
Hi Geirha and thanks for your answer. The issue could be also reproduced on USB storage devices, both external hard drive and memory drive.

What should I include in the bug report? Is there a tool to read the hardware configuration, or a simple lspci would be enough? 

The fact that the issue occurs already with the default live CD removes the chance of a software misconfiguration or an unsupported kernel driver (I have used ndiswrapper on the hard drive installation).

---

### Post by geirha on 2009-10-11
According to this, [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs), you can report the bug with ubuntu-bug. I'm guessing «ubuntu-bug linux-image» would be the right command to use. I have never used that command myself, but I suspect it may gather some necessary information automatically. If not, lspci and dmesg output will probably be a good start.

BTW. Have you tried to reproduce the problem with an older Ubuntu version, like with Ubuntu 8.04 LTS live cd? If it works correctly in an older version, that would be useful information in tracking down the bug.

---

