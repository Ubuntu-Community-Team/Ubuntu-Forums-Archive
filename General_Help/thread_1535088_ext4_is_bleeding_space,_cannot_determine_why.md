---
title: "ext4 is bleeding space, cannot determine why"
date: 2010-07-20
forum: General Help
---

### Post by astradivina on 2010-07-20
I am running Ubuntu 10.04 amd64. So I have just returned from a week vacation to see that my / is full. When I had left, the ~80G partition was only consuming around 40G of space. I feel like this is a bug and i haven't tried a custom kernel yet to see if it is kernel level. Here is all the good information though to help debug:
```

mount
# mount
/dev/mapper/pdc_cfefedbci3 on / type ext4 (rw,noatime,user_xattr,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/mapper/pdc_cfefedbci1 on /boot type ext3 (rw)
/dev/mapper/pdc_cfefedbci4 on /home type ext4 (rw,noatime,user_xattr,errors=remount-ro,data=journal)
none on /proc/fs/vmblock/mountPoint type vmblock (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

```du
```

# du -ack --exclude=/home/* --exclude=/media/* --exclude=/boot/* / 2> /dev/null | sort -n | tail -10
322780    /var
352180    /lib/modules
399004    /lib
541648    /usr/lib/vmware
654628    /usr/share/doc
2296792    /usr/share
2536520    /usr/lib
5749160    /usr
6558488    /
6558488    total

```df -Th
```

# df -Th
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/mapper/pdc_cfefedbci3
              ext4     74G   74G     0 100% /
none      devtmpfs    2.7G  360K  2.7G   1% /dev
none         tmpfs    2.7G     0  2.7G   0% /dev/shm
none         tmpfs    2.7G  364K  2.7G   1% /var/run
none         tmpfs    2.7G     0  2.7G   0% /var/lock
none         tmpfs    2.7G     0  2.7G   0% /lib/init/rw
/dev/mapper/pdc_cfefedbci1
              ext3    510M   63M  422M  13% /boot
/dev/mapper/pdc_cfefedbci4
              ext4    827G  685G  100G  88% /home

``````

# cat boot.log | tail -30
fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
root: clean, 320814/4923392 files, 19624774/19663560 blocks
boot: clean, 218/33200 files, 18113/132528 blocks (check in 4 mounts)
home: clean, 89335/55050240 files, 182982976/220198938 blocks (check after next mount)
init: ureadahead-other main process (1017) terminated with status 4
 * Starting AppArmor profiles                                                   Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
                                                                         [ OK ]
 * Setting sensors limits                                                [ OK ] 

```lspci
```

lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 RAID bus controller: ATI Technologies Inc SB700/SB800 SATA Controller [RAID5 mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3300 Graphics
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
02:00.0 VGA compatible controller: ATI Technologies Inc RV770 LE [Radeon HD 4800 Series]
02:00.1 Audio device: ATI Technologies Inc HD48x0 audio
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
04:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

```uname
```

Linux paulphenom 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 08:03:28 UTC 2010 x86_64 GNU/Linux

```I really have no idea what the problem is at this point. I am using a fakeraid with dm-raid on a raid0 for my /dev/mapper discs. I just wonder if anyone else is getting this error or if it is a problem with ext4. Thank You

---

### Post by Slim Odds on 2010-07-20
Sound like you have a backup application that is out of control.

---

### Post by ankspo71 on 2010-07-20
+1 Or a log file out of control.

Check your .xsession-errors file's size. It is a hidden file in your home folder. I have seen that file rapidly grow out of control (practically overnight) on people more than once. 

Here is a command I found that can help locate all files larger than 10mb.
```
cd /
sudo find . -type f -size +10000k -exec ls -lh {} \; | awk '{ print $8 ": " $5 }'
```

It will simply produce results like this:
/home/james/.googleearth/Cache/dbCache.dat: 300M
/usr/lib/jvm/java-6-openjdk/jre/lib/rt.jar: 59M
/media/sdb1/storage/Applications/Games/nexuiz-252.zip: 889M
/media/sdb2/iso/ubuntu-10.04-desktop-i386.iso: 700M

Hope this helps.

---

### Post by astradivina on 2010-07-20
> **Slim Odds said:**
> Sound like you have a backup application that is out of control.
Yes, I think that maybe it; where can I find the files it is creating on /?

---

### Post by astradivina on 2010-07-20
Yeah I am using simple backup, but that must have gone haywire. I am going to look into and clean it up. If you need my mount options, /home is on a different partition than /.

---

### Post by astradivina on 2010-07-20
OK, I figured it out. Simplebackup was backing up to / instead of a seperate partition, like it should. I will look into it further to see what is up. Thank you for your help!

---

