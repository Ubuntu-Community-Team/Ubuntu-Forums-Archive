---
title: "Ubuntu isn't booting anymore - is this output of any help to someone?"
date: 2010-12-03
forum: General Help
---

### Post by DJTurboToJo on 2010-12-03
Hi Community,

I'm got a problem with my computer. I had Ubuntu running for a long time and then I didn't use it now for quite some time as it didn't want to boot anymore.

If there are any other details you need know to somehow point me in the right direction because right now I have absolutely now clue what to look for please tell me

So in Grub I have the following choices:
Ubuntu 9.10, kernel 2.6.31-14-generic
2.6.28-16
2.6.27-15
2.6.24-25
all versions with recovery mode - but none is working!!!

I think the problems started with an upgrade and I think it was to version higher than 9.10. This was this year in let's say August or September. What possible upgrade could that be?

EDIT: I think it must have been Ubuntu 10.04 LTS (Lucid Lynx)

Anyhow, when I boot up my system it shows me this output and I don't know where to start to fix this problem. Maybe someone can decipher this for me...:

in the usual graphic mode (ALT+CTRL+F7) while booting:
###
udev[2813]: SYSFS{}=will be removed in a future udev version, please ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/65-libmtp.rule:83
udev[2813]: SYSFS{}=will be removed in a future udev version, please ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/65-libmtp.rule:85
udev[2813]: SYSFS{}=will be removed in a future udev version, please ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/65-libmtp.rule:87
udev[2813]: SYSFS{}=will be removed in a future udev version, please ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/65-libmtp.rule:89

dosfck 3.0.7, 24 Dec 2009, FAT32, LFN
/dev/sdb6: clean, 270561/2256576 files, 1855607/4510240 blocks
/dev/sdb5: recovering journal
init: ureadahead-other main process (3207) terminated with status 4
/dev/sdb5: clean, 3507/2818048 files, 2428508/5632782 blocks
init: ureadahead-other main process (3215) terminated with status 4
/dev/sdb2: 29001 files, 1941711/2686561 clusters
init: ureadahead-other main process (3227) terminated with status 4 
####

then the booting stops and when I go to the console (ALT+CTRL+F1) it displays:
###
Begin: Mounting root file system... ...
Begin: Running /Scripts/local-top ...
[    2.625243] forcedeth 0000:00:04.0: ifame eth1, PHY OUI 0x732 @ 1, addr 00:00c:6e:0a:c2:0b
[    2.625355] forcedeth 0000:00:04:0: timirq lnktim desc-v1
[    2.626278] ACPI: PCI INterrrupt Link [APCM] enabled at IRQ 20
[    2.626368] ohci1394 0000:00:0d.0: PCI INT A -> Link[APCM] -> GSI 20 (level, high) -> IRQ 20
[    2.682191] ohci1394: fw-host0: OHCI-1394 1.1 (OCI): IRQ=[20] MMID=[ef084000-ef0847ff]  Max PAcket=[2048]  IR/IT contexts=[4/4]
Done.
Begin: Running /scripts/local-premount ...
Done.
[   3.025822] EXT3-fs: INFO: recovery required on readonly filesystem.
[   3.025914] EXT3-fs: write access will be enabled during recovery.
[   3.065344] kjournal starting. COmmit interval 5 seconds
[   3.065447] EXT3-fs: recovery complete.
[   3.065798] EXT-fs: mounted filesystem with writeback data mode.
Begin: Runing /scripts/local-bottom ...
Done.
Done.
Begin. Running /scripts/init-bottom ...
Done.
init: ureadahead main process (308) terminated with status 5
###

When I start the system the pid are sometimes different though.

Any suggestions are welcome and also comments how to start investigating the booting problem. I unplugged all USB devices and this is a computer no laptop. I also don't have a memory card somewhere as I read these can be troublesome sometimes...

EDIT 1: I also installed a new hard drive and disconnected an other hard disk this year but as far as I remember it was working with this one before trying to upgrade.

EDIT 2: I just tried to start 2.6.24-25 in recovery mode and got these messages:
###
init: ureadahead main process(2777) terminated with status 5
libudev: udev_monitor_new_from_netlink: error getting socket: Invalid argument
mountall:mountall.c:3206: Assertion failed in main: udev_monitor = udev_monitor_new_from_netlink (udev, "udev")
init: mountall main process (2780) killed by ABRT signal
General error mounting filesystems.
A maintenance shell will now be started.
CONTROL-C will terminate this shell and reboot the system.
###
At least I have a shell now... too bad that I don't know what to do...

EDIT 3: I tried to start with the Super Grup Disk and first looked at my partitions, here's the output:
sda (hd0) 419 GB
hd(0,0) HPFS/NTFS 186 GB Windows
hd(0,4) HPFS/NTFS 232 GB WIndows
sdb (hd1) 149 GB
hd(1,0) HPFS/NTFS 68 GB Windows
hd(1,1) fat 41 GB Windows
hd(1,4) ext2fs 21 GB
hd(1,5) ext2fs 17 GB Ubuntu 10.04.1 LTS \n \l
hd(1,6) SWAP 1GB

So I really have 10.04 on my computer installed but grub won't show me this???

EDIT 4: I remember that I had some problems updating first. I had some broken packages, tried to updated them several times and then maybe I skipped them (I can't remember) and just did the upgrade. Is there any hope to fix this problem or would it be easier to simply install from scratch?

EDIT 5: I renamed ureadahead and ureadahead-other but it wouldnt boot neither


Any comment is appreciated!!
DJTJ

---

### Post by DJTurboToJo on 2010-12-05
In case someone might be interested. I got help in this thread: [http://ubuntuforums.org/showthread.php?p=10201916](http://ubuntuforums.org/showthread.php?p=10201916)

---

