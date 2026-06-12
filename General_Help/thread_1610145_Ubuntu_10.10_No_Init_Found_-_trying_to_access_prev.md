---
title: "Ubuntu 10.10 No Init Found - trying to access previous ubuntu encrypted install"
date: 2010-10-31
forum: General Help
---

### Post by star3am on 2010-10-31
Hallo all, 

I ran Ubuntu 9.10 on encrypted disc dual boot with vista
I updated Ubuntu to 10.10 about a week ago, all was well, then another update, and now I cannot boot in to any kernel :/

No init found

I have subsequently reinstalled Ubuntu 10.10 on another disc, but am now trying to get my old files 

Ubuntu 10.10 seems to have a bug, if I plug in my usb drive which contains my b0rk3d Ubuntu install, I cannot install anything using apt, it hangs with unpacking replacement package.

I have to reboot and do apt-get --configure -a to fix (if my usb drive is unplugged I can install apps, once I plug it in, I cannot, and I have to reboot)

reading the forums, I gather that I should do fsck 

```
[   86.949160] usb 1-3: new high speed USB device using ehci_hcd and address 5
[   87.169434] Initializing USB Mass Storage driver...
[   87.169596] scsi2 : usb-storage 1-3:1.0
[   87.169952] usbcore: registered new interface driver usb-storage
[   87.169955] USB Mass Storage support registered.
[   88.169421] scsi 2:0:0:0: Direct-Access     TOSHIBA  MK2555GSX             PQ: 0 ANSI: 2 CCS
[   88.170958] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   88.171783] sd 2:0:0:0: [sdb] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[   88.172838] sd 2:0:0:0: [sdb] Write Protect is off
[   88.172848] sd 2:0:0:0: [sdb] Mode Sense: 00 38 00 00
[   88.172855] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   88.175576] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   88.175590]  sdb: sdb1 sdb2 sdb3 < sdb5 sdb6 >
[   88.249179] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   88.249192] sd 2:0:0:0: [sdb] Attached SCSI disk
[   88.977886] EXT4-fs warning (device sdb5): ext4_clear_journal_err: Filesystem error recorded from previous mount: IO failure
[   88.977902] EXT4-fs warning (device sdb5): ext4_clear_journal_err: Marking fs in need of filesystem check.
[   88.977938] BUG: unable to handle kernel paging request at 02b45000
[   88.977950] IP: [<c03622aa>] __percpu_counter_sum+0x2a/0x70
[   88.977969] *pde = 00000000 
[   88.977977] Oops: 0000 [#1] SMP 
[   88.977985] last sysfs file: /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-3/speed
[   88.977993] Modules linked in: usb_storage aes_i586 aes_generic binfmt_misc rfcomm sco bnep l2cap parport_pc ppdev dm_crypt snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi arc4 joydev snd_seq_midi_event snd_seq tifm_sd snd_timer snd_seq_device iwlagn iwlcore psmouse pcmcia mac80211 tifm_7xx1 snd soundcore snd_page_alloc uvcvideo videodev v4l1_compat serio_raw yenta_socket tifm_core toshiba_bluetooth lp btusb bluetooth pcmcia_rsrc pcmcia_core parport cfg80211 usbhid hid nouveau ttm drm_kms_helper sdhci_pci firewire_ohci drm sdhci video intel_agp r8169 firewire_core crc_itu_t led_class output mii i2c_algo_bit agpgart
[   88.978143] 
[   88.978152] Pid: 1854, comm: mount Not tainted 2.6.35-22-generic #35-Ubuntu ISKAE/Satellite A200
[   88.978162] EIP: 0060:[<c03622aa>] EFLAGS: 00010293 CPU: 1
[   88.978171] EIP is at __percpu_counter_sum+0x2a/0x70
[   88.978178] EAX: 00000000 EBX: 00000000 ECX: 02b45000 EDX: 00000000
[   88.978186] ESI: 00000000 EDI: f4a0e494 EBP: f48abd6c ESP: f48abd60
[   88.978193]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
[   88.978202] Process mount (pid: 1854, ti=f48aa000 task=f2ecf230 task.ti=f48aa000)
[   88.978207] Stack:
[   88.978212]  f4aa4c00 16712750 00000000 f48abda0 c02ad8b6 f1d9b400 f48abd88 c05c64d0
[   88.978231] <0> 00000001 f1d9b400 1671274c 00000000 f2136818 f4aa4c00 f5582800 f1d9b400
[   88.978252] <0> f48abdd8 c02ada83 f4aa4c00 c05e91b5 c0730ca8 c073dd92 f5582800 f48abdd8
[   88.978275] Call Trace:
[   88.978289]  [<c02ad8b6>] ? ext4_commit_super+0xd6/0x1d0
[   88.978301]  [<c05c64d0>] ? printk+0x2d/0x35
[   88.978312]  [<c02ada83>] ? ext4_clear_journal_err+0xa3/0xd0
[   88.978324]  [<c02d7ffc>] ? jbd2_journal_load+0x6c/0xd0
[   88.978335]  [<c02b0cff>] ? ext4_load_journal+0x14f/0x2e0
[   88.978347]  [<c02b219d>] ? ext4_fill_super+0x11fd/0x1a40
[   88.978358]  [<c0151519>] ? irq_exit+0x39/0x70
[   88.978368]  [<c05cf79b>] ? smp_apic_timer_interrupt+0x5b/0x8a
[   88.978381]  [<c021b552>] ? get_sb_bdev+0x162/0x1a0
[   88.978391]  [<c02b0fa0>] ? ext4_fill_super+0x0/0x1a40
[   88.978402]  [<c02ac1d6>] ? ext4_get_sb+0x26/0x30
[   88.978412]  [<c02b0fa0>] ? ext4_fill_super+0x0/0x1a40
[   88.978422]  [<c021aee4>] ? vfs_kern_mount+0x74/0x1c0
[   88.978433]  [<c022f493>] ? get_fs_type+0x33/0xb0
[   88.978442]  [<c021b08e>] ? do_kern_mount+0x3e/0xe0
[   88.978452]  [<c023260c>] ? do_mount+0x1dc/0x220
[   88.978461]  [<c02326bb>] ? sys_mount+0x6b/0xa0
[   88.978471]  [<c05c9114>] ? syscall_call+0x7/0xb
[   88.978477] Code: 00 55 89 e5 57 89 c7 56 53 e8 43 69 26 00 8b 5f 04 b8 ff ff ff ff 8b 77 08 eb 1c 8d b6 00 00 00 00 8b 0c 85 80 56 81 c0 8b 57 14 <8b> 14 0a 89 d1 c1 f9 1f 01 d3 11 ce 8d 48 01 a1 6c 93 5d c0 ba 
[   88.978594] EIP: [<c03622aa>] __percpu_counter_sum+0x2a/0x70 SS:ESP 0068:f48abd60
[   88.978608] CR2: 0000000002b45000
[   88.978616] ---[ end trace 7b1c1f2e072124a8 ]---
root@star-ubuntu:~# fsck /dev/sdb5 
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext4: Device or resource busy while trying to open /dev/sdb5
Filesystem mounted or opened exclusively by another program?
```

mount.ecryptfs is not much help either, i know the password of this drive, but nothing seems to work, should i try 9.10 ? 

thanks, any help will be much appreciated !

---

### Post by star3am on 2010-11-01
It took me all day, but I have my data back. 

What fixed it for me was FSCK but I could not do this with the current drive, it was always in use by the system, so i installed Ubuntu on another HDD and booted from that, then plugged my drive into USB. 

Once Ubuntu was booted up, I did not login to my desktop, I pressed Alt Ctrl F1 and logged in there, then did fsck and it worked. 

So happy, already backed up my data now, it was a close call :)

Happy Monday all, and yes, I still think Ubuntu Rocks !:guitar:

---

### Post by m1kael on 2010-11-01
Hello, I think I'm having a similar problem.  I put a fresh install of Ubuntu 10.10 on my laptop this weekend, and today it failed to boot up!

```

Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootrag

```

I tried booting with a livecd, but I cannot touch the /dev/sda5 partition that I have ubuntu on.  I keep getting an error:

```

fsck.ext4: Device or resource busy while trying to open /dev/sda5
Filesystem mounted or opened exclusively by another program?

```

I haven't found a solution for this yet, but your post seems more similar than others.  Any advice?  Ideally I would like to just fix the boot problems without needing another harddrive.. is this possible?  Thanks.

---

### Post by frederik.nnaji on 2010-11-02
> fsck.ext4: Device or resource busy while trying to open /dev/sda5
Filesystem mounted or opened exclusively by another program?

yeah that's what i get too.
essentially, i didn't do anything to the drive.
i just booted the computer off a usb-pendrive.
after shutting down, i couldn't boot from the harddisk again.

none of the old kernels made any difference to this..

i have a seperate /home partition, but that won't help me now, since my homefolder is encrypted. i need to fix the unmountable system partition, no way around it i guess.

i tried swapoff, but that didn't help..

what program is accessing the device?
is this error message perhaps a bug?
how can the device be busy, if its neither mounted, nor being accessed by any app that i started..!?

---

### Post by patse on 2010-11-16
hello, I am experiencing the exact same problem as m1kael. This actually already happened to me sometime in October but I ended up just reinstalling Ubuntu.

Today, Ubuntu 10.10 booted into BusyBox on startup, resulting in the same error:

```
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootrag
```

So I decided to boot up my netbook (Samsung n510) on a live usb system (also ubuntu 10.10). I tried to run a file system check with fsck, but it keeps on telling me that the Device or resource is busy and ask if the Filesystem is mounted or opened exclusively by another program. I tried using lsof to see if the device is used by any program, but no result.

Also, mounting the root partition, sda5 in my case, doesn't work. I passed --verbose to the mount command, but this didn't give me any error message. When typing:

```
sudo mount /dev/sda5 /mnt
```

it dosn't do anything and I am not able to use crtl+c to cancel either!?


Is there any other possibility to check the file system? I've never ran into a situation where fsck or even mounting a partition from a live system doesn't work.

---

### Post by NetworkCowgirl on 2010-12-03
Boot from a live cd, run gparted and remove the mount point from the drive you are trying to check. FSCK should then work for you.

---

### Post by TheBigT on 2011-03-26
> **NetworkCowgirl said:**
> Boot from a live cd, run gparted and remove the mount point from the drive you are trying to check. FSCK should then work for you.

I've had the same problem and unmounting with gparted just simply doesn't work. In fact, the partition is NOT mounted, yet it cannot be fsck'd. And it gets worse, just as the previous poster mentioned... Trying to mount the partition causes the mount command to hang (possibly in the kernel, as the hang cannot be interrupted by ctrl-c).

Just as in the case of the original submitter, the only solution that worked for me was to connect the hard drive in question to a USB dongle which I only connected to the PC after the Live CD boot was complete. At this point I was finally allowed to fsck (which, in turn, restored the bootability of the HDD). I didn't need any pre-login console magic, a normal Live CD boot followed by gparted worked just fine.

This is by far the nastiest thing that I've seen in Ubuntu. It's not every day that you need specialized hardware to do a simple file system check.

---

### Post by rahul255 on 2011-04-09
I had the same set of errors listed above on Ubuntu 10.10,
[INDENT][/INDENT]though I didn't have encryption enabled anywhere.
  
The issue seemed to be happening when the scripts in the linux initial ramdisk start running,
[INDENT][/INDENT]either from the live CD or directly from the hard disk
  
Since I was running ubuntu on a MacBook internal drive,
[INDENT]I did not want to remove the hard disk,
or install one more linux on another partition.
[/INDENT]
For my MacBook, I did the following to recover from this issue
[INDENT]Boot from Ubuntu 10.10 Live CD to the syslinux screen
Press F6, Escape.
Remove the "boot=casper" from the command line
Press Enter to boot
[/INDENT]  
When you reach the (initramfs) prompt ( Replace sr0 and sda4 appropriately below )
[INDENT]ls -l /dev/disk/by-path
modprobe isofs
mkdir /tmp/sr0
mount -r /dev/sr0 /tmp/sr0
mkdir /tmp/fs
mount -t squashfs -r /tmp/sr0/casper/filesystem.squashfs /tmp/fs
/tmp/fs/sbin/e2fsck /dev/sda4
reboot[/INDENT]

---

### Post by zaf.ansari on 2011-09-16
Thanks a lot rahul255. U saved my life buddy. Was stuck with this since 8 hours. God bless, bro.

---

### Post by polarise on 2011-10-04
> **rahul255 said:**
> I had the same set of errors listed above on Ubuntu 10.10,
[INDENT][/INDENT]though I didn't have encryption enabled anywhere.
  
The issue seemed to be happening when the scripts in the linux initial ramdisk start running,
[INDENT][/INDENT]either from the live CD or directly from the hard disk
  
Since I was running ubuntu on a MacBook internal drive,
[INDENT]I did not want to remove the hard disk,
or install one more linux on another partition.
[/INDENT]
For my MacBook, I did the following to recover from this issue
[INDENT]Boot from Ubuntu 10.10 Live CD to the syslinux screen
Press F6, Escape.
Remove the "boot=casper" from the command line
Press Enter to boot
[/INDENT]  
When you reach the (initramfs) prompt ( Replace sr0 and sda4 appropriately below )
[INDENT]ls -l /dev/disk/by-path
modprobe isofs
mkdir /tmp/sr0
mount -r /dev/sr0 /tmp/sr0
mkdir /tmp/fs
mount -t squashfs -r /tmp/sr0/casper/filesystem.squashfs /tmp/fs
/tmp/fs/sbin/e2fsck /dev/sda4
reboot[/INDENT]

Rahul,
You're my hero!
Thanks,
PK

---

### Post by jcoffland on 2012-01-13
I had the same problem on my boot disk.  The issue that makes it hard to fix is that when the OS tries to access the disk it causes a crash in the disk driver.  Once this happens you cannot access the disk again until you reboot.  The solution above works because it gets to the disk very early.

The drive with the problem was built in to a laptop and I didn't want to have to disassemble it and I had a copy of Parted Magic and a USB CD/DVD drive handy. The following worked for me:

 - Boot to the Parted Magic CD or DVD.
 - At the first prompt hit <TAB>
 - Type 'nofstabdaemon<ENTER>'
 - Once the OS boots run: 'fsck /dev/sda1', replacing /dev/sda1 with the correct path to the corrupt disk.
 - Tell fsck 'y' to repair any errors.
 - Remove Parted Magic disk.
 - Reboot.

After this all was well.  With out the 'nofstabdaemon' boot option Parted Magic tries to access the disk and encounters the same problem.

Ultimately, there is a bug in the ext2 kernel driver.  Regardless of what data is on the disk or the state of the hardware the kernel driver should not crash.  I'm not sure how to fix this or if it has been fixed, but once the disk has been properly fsck'ed the problem goes away.

---

### Post by manishm on 2012-01-16
Hi rahul I tried same procedure as given by you but struck at last step when I try to mount squashfs file system.

I get error " mount: mounting /dev/loop0 on /tmp/fs failed : No such device

---

