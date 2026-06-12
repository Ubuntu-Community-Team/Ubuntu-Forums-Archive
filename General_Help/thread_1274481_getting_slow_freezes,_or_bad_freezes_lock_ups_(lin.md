---
title: "getting slow freezes, or bad freezes/ lock ups (linux-rt-2.6.28/kernel/exit.c:1009)"
date: 2009-09-24
forum: General Help
---

### Post by ebenedito on 2009-09-24
Hi There,

I love Ubuntu, but I find 9.0.4 quite *unstable*.. I am running the studio version. My first attempt was on an Intel dual core2 64 bits machine and that did not go very well. Freezes and lock ups very frequently (< hours). I have seen some bug reports for 64 bits so I then installed it on an old hp compaq box (32bits) and although the system is more usable, I get system hangs every day. Hangs could come in different flavors, sometimes slow lockups (starts with not being able to open new apps, bash shells getting stuck) but mouse and some menus are responsive to the point I can't even shut down the machine or the mouse pointer freezes - then the only escape is the red button.. 

I was able to narrow down the last episode and I can reproduce it at will.. This one is not a complete lock up.

Maybe my setup is not common, but hey.. this is what I have:

- main partition (ubuntu)
- extended partition with RH9 contents (/dev/sda5)
- I then mount the RH9 partition  as "sudo mount -t ext3 /dev/sda5 /hosts/RH9" 
- I also mount my home folder on top of that RH9 partition/mount point "sudo mount -t nfs nas-01:/vol/vol1/home /hosts/RH9/rh9/home1"
- I then *chroot* into this partition  "sudo chroot /hosts/RH9/rh9 /bin/bash".. 
- I do my compile work there

what I noticed is that it seems the kernel  crashes when I run the java compiler (javac)

Below  is some info if this can be of any help..
Cheers (and thanks in advance for the help)

--------------------------------
ebenedito@mars:~$ uname -a
Linux mars 2.6.28-3-rt #12-Ubuntu SMP PREEMPT RT Fri Apr 17 10:09:11 UTC 2009 i686 GNU/Linux

ebenedito@mars:~$ lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation 82915G Integrated Graphics Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
40:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
ebenedito@mars:~$ 

--------------------------------
... <messages>

Sep 24 11:38:50 mars -- MARK --
Sep 24 11:58:50 mars -- MARK --
Sep 24 12:18:50 mars -- MARK --
Sep 24 12:38:50 mars -- MARK --
Sep 24 12:58:50 mars -- MARK --
Sep 24 13:18:50 mars -- MARK --
Sep 24 13:28:15 mars kernel: [12646.302504] kjournald starting.  Commit interval 5 seconds
Sep 24 13:28:15 mars kernel: [12646.302700] EXT3 FS on sda5, internal journal
Sep 24 13:28:15 mars kernel: [12646.302706] EXT3-fs: recovery complete.
Sep 24 13:28:15 mars kernel: [12646.302899] EXT3-fs: mounted filesystem with ordered data mode.
Sep 24 13:37:39 mars kernel: [13209.932170] Dumping ftrace buffer:
Sep 24 13:37:39 mars kernel: [13209.932170]    (ftrace buffer empty)
Sep 24 13:37:39 mars kernel: [13209.932170] Modules linked in: nfs lockd nfs_acl sunrpc i915 drm bridge stp bnep video output input_polldev lp snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss ppdev snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device psmouse iTCO_wdt iTCO_vendor_support serio_raw pcspkr snd soundcore snd_page_alloc joydev parport_pc parport intel_agp agpgart usbhid tg3 floppy fbcon tileblit font bitblit softcursor
Sep 24 13:37:39 mars kernel: [13209.932170] 
Sep 24 13:37:39 mars kernel: [13209.932170] Pid: 4521, comm: javac Tainted: G W (2.6.28-3-rt #12-Ubuntu) HP Compaq dc7100 SFF(PC924A)
Sep 24 13:37:39 mars kernel: [13209.932170] EIP: 0060:[<c01e3f61>] EFLAGS: 00210046 CPU: 0
Sep 24 13:37:39 mars kernel: [13209.932170] EIP is at __find_get_block+0x21/0x1a0
Sep 24 13:37:39 mars kernel: [13209.932170] EAX: 00200086 EBX: 000a0016 ECX: 00000000 EDX: 000a0016
Sep 24 13:37:39 mars kernel: [13209.932170] ESI: 00000000 EDI: f6baa800 EBP: d0d43cb8 ESP: d0d43c78
Sep 24 13:37:39 mars kernel: [13209.932170]  DS: 007b ES: 007b FS: 00d8 GS: 0000 SS: 0068 preempt:00000000
Sep 24 13:37:39 mars kernel: [13209.932170]  00000000 000a0016 f6baa800 00000001 f0a9afa0 d0d43ca4 00200046 00200046
Sep 24 13:37:39 mars kernel: [13209.932170] ---[ end trace 5592ad72e87054ef ]---
Sep 24 13:37:39 mars kernel: [13209.932170] ------------[ cut here ]------------
Sep 24 13:37:39 mars kernel: [13209.932170] WARNING: at /build/buildd/linux-rt-2.6.28/kernel/exit.c:1009 do_exit+0x3d1/0x3e0()
Sep 24 13:37:39 mars kernel: [13209.932170] Modules linked in: nfs lockd nfs_acl sunrpc i915 drm bridge stp bnep video output input_polldev lp snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss ppdev snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device psmouse iTCO_wdt iTCO_vendor_support serio_raw pcspkr snd soundcore snd_page_alloc joydev parport_pc parport intel_agp agpgart usbhid tg3 floppy fbcon tileblit font bitblit softcursor
Sep 24 13:37:39 mars kernel: [13209.932170] Pid: 4521, comm: javac Tainted: G      D W  2.6.28-3-rt #12-Ubuntu
Sep 24 13:37:39 mars kernel: [13209.932170] Call Trace:
Sep 24 13:37:39 mars kernel: [13209.932170]  [<c050f991>] ? printk+0x18/0x1f
Sep 24 13:37:39 mars kernel: [13209.932170]  [<c013be54>] warn_on_slowpath+0x54/0x80
Sep 24 13:37:39 mars kernel: [13209.932170]  [<c02d4418>] ? vsnprintf+0x378/0x5c0
Sep 24 13:37:39 mars kernel: [13209.932170]  [<c0123e68>] ? default_spin_lock_flags+0x8/0x10
Sep 24 13:37:39 mars kernel: [13209.932170]  [<c013c6c9>] ? release_console_sem+0x199/0x1e0
Sep 24 13:37:39 mars kernel: [13209.932170]  [<c0156eda>] ? blocking_notifier_call_chain+0x1a/0x20
Sep 24 13:37:39 mars kernel: [13209.932170]  [<c013fab1>] do_exit+0x3d1/0x3e0
Sep 24 13:37:39 mars kernel: [13209.932170]  [<c013bd7a>] ? print_oops_end_marker+0x2a/0x30
Sep 24 13:37:39 mars kernel: [13209.932170]  [<c0512b81>] oops_end+0xb1/0xc0
Sep 24 13:37:39 mars kernel: [13209.932170]  [<c0107051>] die+0x51/0x70
Sep 24 13:37:39 mars kernel: [13209.932170]  [<c05129d1>] do_trap+0x91/0xf0
Sep 24 13:37:39 mars kernel: [13209.932170]  [<c0106020>] ? do_invalid_op+0x0/0xa0
Sep 24 13:37:39 mars kernel: [13209.932170]  [<c01060a6>] do_invalid_op+0x86/0xa0
Sep 24 13:37:39 mars kernel: [13209.932170]  [<c01e3f61>] ? __find_get_block+0x21/0x1a0
Sep 24 13:37:39 mars kernel: [13209.932170]  [<c04300da>] ? sock_sendmsg+0xea/0x110
Sep 24 13:37:39 mars kernel: [13209.932170]  [<c0151a40>] ? autoremove_wake_function+0x0/0x50
Sep 24 13:37:39 mars kernel: [13209.932170]  [<c05120b2>] error_code+0x72/0x80
Sep 24 13:37:39 mars kernel: [13209.932170]  [<c01e3f61>] ? __find_get_block+0x21/0x1a0
Sep 24 13:37:39 mars kernel: [13209.932170]  [<c0194bd1>] ? find_get_pages+0x101/0x110
Sep 24 13:37:39 mars kernel: [13209.932170]  [<c01e45d2>] __getblk+0x22/0x50
Sep 24 13:37:39 mars kernel: [13209.932170]  [<c02190e7>] __ext3_get_inode_loc+0xd7/0x310
Sep 24 13:37:39 mars kernel: [13209.932170]  [<c019d922>] ? pagevec_lookup+0x22/0x30
Sep 24 13:37:39 mars kernel: [13209.932170]  [<c0511b38>] ? rt_spin_lock+0x8/0x10
Sep 24 13:37:39 mars kernel: [13209.932170]  [<c0250a44>] ? start_this_handle+0x2f4/0x380
Sep 24 13:37:39 mars kernel: [13209.932170]  [<c0219714>] ext3_get_inode_loc+0x14/0x20
Sep 24 13:37:39 mars kernel: [13209.932170]  [<c0219746>] ext3_reserve_inode_write+0x26/0x80
Sep 24 13:37:39 mars kernel: [13209.932170]  [<c021ca21>] ext3_orphan_del+0x81/0x180
Sep 24 13:37:39 mars kernel: [13209.932170]  [<c02228b9>] ? ext3_journal_start_sb+0x29/0x50
Sep 24 13:37:39 mars kernel: [13209.932170]  [<c021b700>] ? ext3_delete_inode+0x0/0xe0
Sep 24 13:37:39 mars kernel: [13209.932170]  [<c021b760>] ext3_delete_inode+0x60/0xe0
Sep 24 13:37:39 mars kernel: [13209.932170]  [<c021b700>] ? ext3_delete_inode+0x0/0xe0
Sep 24 13:37:39 mars kernel: [13209.932170]  [<c01d6458>] generic_delete_inode+0x98/0x160
Sep 24 13:37:39 mars kernel: [13209.932170]  [<c01d6545>] generic_drop_inode+0x25/0x30
Sep 24 13:37:39 mars kernel: [13209.932170]  [<c01d52d1>] iput+0x41/0x60
Sep 24 13:37:39 mars kernel: [13209.932170]  [<c01d27bf>] dentry_iput+0x6f/0xc0
Sep 24 13:37:39 mars kernel: [13209.932170]  [<c01d28d6>] d_kill+0x36/0x60
Sep 24 13:37:39 mars kernel: [13209.932170]  [<c01d3050>] dput+0x70/0x120
Sep 24 13:37:39 mars kernel: [13209.932170]  [<c01c4143>] __fput+0x123/0x1b0
Sep 24 13:37:39 mars kernel: [13209.932170]  [<c01c41ef>] fput+0x1f/0x30
Sep 24 13:37:39 mars kernel: [13209.932170]  [<c01aac8d>] remove_vma+0x2d/0x60
Sep 24 13:37:39 mars kernel: [13209.932170]  [<c01aae77>] exit_mmap+0x1b7/0x280
Sep 24 13:37:39 mars kernel: [13209.932170]  [<c0139f86>] mmput+0x26/0xa0
Sep 24 13:37:39 mars kernel: [13209.932170]  [<c013f594>] exit_mm+0x114/0x160
Sep 24 13:37:39 mars kernel: [13209.932170]  [<c013f80a>] do_exit+0x12a/0x3e0
Sep 24 13:37:39 mars kernel: [13209.932170]  [<c0510117>] ? schedule+0x457/0x760
Sep 24 13:37:39 mars kernel: [13209.932170]  [<c013faf0>] do_group_exit+0x30/0x90
Sep 24 13:37:39 mars kernel: [13209.932170]  [<c014a348>] get_signal_to_deliver+0x238/0x3a0
Sep 24 13:37:39 mars kernel: [13209.932170]  [<c0123e68>] ? default_spin_lock_flags+0x8/0x10
Sep 24 13:37:39 mars kernel: [13209.932170]  [<c0103db0>] do_signal+0x70/0x180
Sep 24 13:37:39 mars kernel: [13209.932170]  [<c051106b>] ? rt_mutex_slowunlock+0x3b/0x70
Sep 24 13:37:39 mars kernel: [13209.932170]  [<c01629ae>] ? rt_up_read+0x2e/0x50
Sep 24 13:37:39 mars kernel: [13209.932170]  [<c01607e7>] ? futex_wake+0xd7/0xf0
Sep 24 13:37:39 mars kernel: [13209.932170]  [<c01618d6>] ? do_futex+0x56/0x160
Sep 24 13:37:39 mars kernel: [13209.932170]  [<c0161a74>] ? sys_futex+0x94/0x110
Sep 24 13:37:39 mars kernel: [13209.932170]  [<c0103efd>] do_notify_resume+0x3d/0x40
Sep 24 13:37:39 mars kernel: [13209.932170]  [<c0104200>] work_notifysig+0x13/0x23
Sep 24 13:37:39 mars kernel: [13209.932170] ---[ end trace 5592ad72e87054ef

------------------------------
...<can't umount>
ebenedito@mars:~$ sudo umount /hosts/RH9
[sudo] password for ebenedito: 
umount: /hosts/RH9: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))

-------------------------
...<javac seems to be defunct>
ebenedito@mars:~$ ps -ef |grep java
2077     14124 14123  0 14:39 ?        00:00:02 [javac]
2077     14569 14550  0 14:46 pts/3    00:00:00 grep java
ebenedito@mars:~$ kill -9 14124
ebenedito@mars:~$ ps -ef |grep java
2077     14124 14123  0 14:39 ?        00:00:02 [javac]
2077     14571 14550  0 14:46 pts/3    00:00:00 grep java
ebenedito@mars:~$ kill -9 14123
ebenedito@mars:~$ ps -ef |grep java
2077     14124     1  0 14:39 ?        00:00:02 [javac]
2077     14573 14550  0 14:46 pts/3    00:00:00 grep java
ebenedito@mars:~$ kill -9 14124
ebenedito@mars:~$ ps -ef |grep java
2077     14124     1  0 14:39 ?        00:00:02 [javac]
2077     14575 14550  0 14:46 pts/3    00:00:00 grep java

-----
ebenedito@mars:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-3-rt/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/ebenedito/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ebenedito)
/dev/sda5 on /hosts/RH9 type ext3 (rw)
nas-01:/vol/vol1/home on /hosts/RH9/rh9/home1 type nfs (rw,addr=10.0.0.9)
nas-01:/vol/vol1/home on /home1 type nfs (rw,addr=10.0.0.9)
proc on /hosts/RH9/rh9/proc type proc (rw)
nas-01:/vol/vol2/tools on /hosts/RH9/rh9/opt type nfs (rw,addr=10.0.0.9)
ebenedito@mars:~$ 

---
...<can't get the contents of the folder>
ebenedito@mars:~$ cd /hosts/RH9/rh9/build
ebenedito@mars:/hosts/RH9/rh9/build$ ls ../../..
RH9
ebenedito@mars:/hosts/RH9/rh9/build$ ls
    (it hangs here)
-----

... < a close inspection with strace reveals it is stuck in the getdents64 system call..>
close(3)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_NUMERIC", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_NUMERIC", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=54, ...}) = 0
mmap2(NULL, 54, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7d71000
close(3)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_CTYPE", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_CTYPE", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=256316, ...}) = 0
mmap2(NULL, 256316, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7d32000
close(3)                                = 0
ioctl(1, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 opost isig icanon echo ...}) = 0
ioctl(1, TIOCGWINSZ, {ws_row=24, ws_col=102, ws_xpixel=0, ws_ypixel=0}) = 0
open(".", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOE  XEC) = 3
fstat64(3, {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
fcntl64(3, F_GETFD)                     = 0x1 (flags FD_CLOEXEC)
getdents64(3, 
.... and it hangs there.. never returned from kernel..

---

### Post by drew_austin on 2009-09-26
I had a similar problem last weekend when I did a clean install of Ubuntu Studio on my AMD64 dual core system. When I tried to update the system with the update manager or Synaptic package manager, the system would halt and I had to do a hard reset. Even just leaving it up and running without doing anything would cause it to halt usually within 10 minutes or so. Disabling IOAPIC in the BIOS did the trick, and it's been stable for a week (no crashes, no halts). I'm not sure why this worked, but it did the trick.

---

### Post by pveurshout on 2009-09-27
> **drew_austin said:**
> I had a similar problem last weekend when I did a clean install of Ubuntu Studio on my AMD64 dual core system. When I tried to update the system with the update manager or Synaptic package manager, the system would halt and I had to do a hard reset. Even just leaving it up and running without doing anything would cause it to halt usually within 10 minutes or so. Disabling IOAPIC in the BIOS did the trick, and it's been stable for a week (no crashes, no halts). I'm not sure why this worked, but it did the trick.

I'm having similar problems as the OP. Screen just went blank and a similar message as they were having (posted below) was in the logs. I don't want to hijack this thread so I won't go into detail about that, but I was wondering whether there were any downsides to disabling IOAPIC in the BIOS? I mean, it's there for a reason I suppose. (Though mainly I'm worried about doing damage to the system in any way) Does booting with the parameters 'noapic nolapic' (read about that on Wikipedia [here]("http://en.wikipedia.org/wiki/Intel_APIC_Architecture")) do the same thing, by the way?

```

[ 3447.316338] Dumping ftrace buffer:
[ 3447.316343]    (ftrace buffer empty)
[ 3447.316347] CPU 0 
[ 3447.316350] Modules linked in: binfmt_misc bridge stp bnep input_polldev lp pata_pcmcia snd_hda_intel arc4 ecb snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss iwlagn snd_seq_midi snd_rawmidi iwlcore snd_seq_midi_event snd_seq pcmcia snd_timer uvcvideo mac80211 ppdev snd_seq_device leds_hp_disk led_class psmouse yenta_socket rsrc_nonstatic compat_ioctl32 videodev sdhci_pci tpm_infineon tpm parport_pc video snd joydev serio_raw pcspkr pcmcia_core usbhid ricoh_mmc sdhci v4l1_compat cfg80211 tpm_bios iTCO_wdt iTCO_vendor_support parport output intel_agp btusb soundcore lis3lv02d nvidia(P) snd_page_alloc ohci1394 ieee1394 e1000e fbcon tileblit font bitblit softcursor
[ 3447.316454] Pid: 3774, comm: multiload-apple Tainted: P           2.6.28-15-generic #49-Ubuntu
[ 3447.316459] RIP: 0010:[<ffffffff802e269c>]  [<ffffffff802e269c>] kmem_cache_alloc+0x5c/0xc0
[ 3447.316474] RSP: 0018:ffff8801059a1c98  EFLAGS: 00010006
[ 3447.316478] RAX: 0000000000000000 RBX: 101a50a02290217e RCX: 0000000000000000
[ 3447.316483] RDX: ffff88002802cce0 RSI: 00000000000000d0 RDI: 0000000000000020
[ 3447.316487] RBP: ffff8801059a1cc8 R08: 0000000000000000 R09: 0000000000000000
[ 3447.316492] R10: ffff880068c34500 R11: ffffffff8080a956 R12: 0000000000000282
[ 3447.316496] R13: ffffffff809ac288 R14: ffffffff803047bc R15: 00000000000000d0
[ 3447.316502] FS:  00007fd42fc267d0(0000) GS:ffffffff80a9a000(0000) knlGS:0000000000000000
[ 3447.316507] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[ 3447.316511] CR2: 00000000f6786000 CR3: 00000001059cb000 CR4: 00000000000006a0
[ 3447.316516] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[ 3447.316520] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[ 3447.316526] Process multiload-apple (pid: 3774, threadinfo ffff8801059a0000, task ffff88010bdb5980)
[ 3447.316533]  0000002000100100 ffff88013d216b40 00000000fffffff4 ffffffff8033eab0
[ 3447.316767]  RSP <ffff8801059a1c98>
[ 3447.316772] ---[ end trace f2b4059172a3eff9 ]---
```
(note: this time it happened while I was trying to make Skype work after it showed an error message 'Problem with Audio Playback'. Similar scary messages have been popping up in all kinds of situations before)

---

### Post by georgelenzer on 2009-10-23
I'm new to Ubuntu Studio 64-bit, but I've specifically been getting lock ups when doing data transfers over eth0.  If I use rsync, ssh or NFS for network data transfers, the system locks up after about 100 bytes of transfer.  I thought it was a completely hard lock up because I couldn't ping the system, Ctrl-Alt-F1-F6 to a VT, or move the mouse pointer.  But yesterday while getting ready to try and boot into a live CD, I didn't turn the laptop off like I usually do and... I got kernel errors on the console.

The kernel errors referred to ata1:00 and a kernel soft lockup on CPU#0.  This was with linux-image-2.6.28-3-rt (the default for Jaunty).  I then booted with the intallation DVD, went into rescue mode and chrooted to the installed root file system.  ssh and rsync transfers then worked without any problem.  That kernel was linux-image-2.6.28-11-generic.  So I installed that to the installed system and booted into it.  The problem was gone.  However, there appears to be a bug regarding massive data loss on Ubuntu 9.04 on 64-bit systems with linux-2.6.28-11-generic.  So I'm going to be moving to Ubuntu Studio 8.04 64-bit and see if things are better there...

---

### Post by P4man on 2009-10-23
> **pveurshout said:**
> I'm having similar problems as the OP. Screen just went blank and a similar message as they were having (posted below) was in the logs. I don't want to hijack this thread so I won't go into detail about that, but I was wondering whether there were any downsides to disabling IOAPIC in the BIOS? I mean, it's there for a reason I suppose. (Though mainly I'm worried about doing damage to the system in any way) Does booting with the parameters 'noapic nolapic' (read about that on Wikipedia [here]("http://en.wikipedia.org/wiki/Intel_APIC_Architecture")) do the same thing, by the way?


Kind of late response but,
Settong noapic and/or nolapic as boot option  will do the same thing basically as setting them in the bios. Downsides are minimal, Theoretically there is a potential loss of performance on heavily threaded tasks, but its not likely noticeable. Either way, physical damage is not going to occur because of this. Worst case scenerio is that it wont boot and you have to change it again.

A general remark is that the RT kernel is still very experimental afaik. Im not sure if ubuntu is doing a good enough job warning studio users of this fact.

---

### Post by P4man on 2009-10-23
> **georgelenzer said:**
>   However, there appears to be a bug regarding massive data loss on Ubuntu 9.04 on 64-bit systems with linux-2.6.28-11-generic.  

You have a link for that? Even if its true, just upgrade to a newer kernel then. Just avoid the RT kernels except perhaps with the noapic/nolapic option.
```

So I'm going to be moving to Ubuntu Studio 8.04 64-bit and see if things are better there...

```

If it uses the realtime kernel, its likely as bad as 9.04

---

### Post by georgelenzer on 2009-10-26
Here is the link for the bug in question:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691)

Sadly I need the RT kernels for JACK to give me low latency audio.  I'll give the noapic option a try... after I am done restoring/resizing Windows Vista 64 to allow for dual boot.  I am also going to try karmic since it's now RC.  I was told via #ubuntustudio on IRC that as long as I keep up with updates via apt-get, I should wind up with the same thing I will get on the official release day.  We'll see if it's any better.  Otherwise I might be going back to Gentoo for this machine.  :confused:

> **P4man said:**
> You have a link for that? Even if its true, just upgrade to a newer kernel then. Just avoid the RT kernels except perhaps with the noapic/nolapic option.
```

So I'm going to be moving to Ubuntu Studio 8.04 64-bit and see if things are better there...

```If it uses the realtime kernel, its likely as bad as 9.04

---

### Post by georgelenzer on 2009-10-27
So far, so good with Karmic.  The network data transfer and lock up problems are gone and more of the HP HDX16's hardware is working.  Of course... this is the RC version and Karmic is very new, so I expect I'll run into other things...  Such is life with an OS that is always in development, but I wouldn't have it any other way.  :)

> **P4man said:**
> You have a link for that? Even if its true, just upgrade to a newer kernel then. Just avoid the RT kernels except perhaps with the noapic/nolapic option.
```

So I'm going to be moving to Ubuntu Studio 8.04 64-bit and see if things are better there...

```If it uses the realtime kernel, its likely as bad as 9.04

---

