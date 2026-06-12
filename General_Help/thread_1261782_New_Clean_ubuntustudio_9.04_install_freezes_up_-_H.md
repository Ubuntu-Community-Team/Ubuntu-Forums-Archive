---
title: "New Clean ubuntustudio 9.04 install freezes up - HELP"
date: 2009-09-09
forum: General Help
---

### Post by kandos on 2009-09-09
Hello,

I am a new user of ubuntustudio 9.04, having only yesterday performed a clean install.  Most programs have worked correctly.  However, performing any moving or access of any large files from my backup drives to my main working drive causes a crash.  I am unable to use mouse or keyboard when this happens.

Using the command line, I am able to move small files (under about 2MB), but nothing larger.  Trying to move files AT ALL using the GUI causes a crash.

Can anyone please help?  The audio applications I installed ubuntustudio to take advantage of all work perfectly, but I can't move or access large files on my backup hard drives.

Thank you.
Toby

---

### Post by kandos on 2009-09-10
After testing, I've found some things out about my problem.

It is only occurring when I transfer files over 100MB between my backup SATA drive and my main working SATA drive.  It occurs when using the GUI or the command line to move or copy files.

Can anyone please suggest why Ubuntu freezes when I am performing these file operations?  Please?

---

### Post by P4man on 2009-09-10
can you check your logfiles for errors? System > adminstratin > log file viewer. Perhaps that might shed some more light on it.

Also worth trying: can you copy those files when booting from a livecd?

---

### Post by kandos on 2009-09-24
The 9.04 ubuntu studio disk I have doesn't have an option to boot from the CD.

The logs don't seem to be picking anything unusual up.  The system completely freezes - not even Caps Lock will turn on or off.  There is simply a crash, then a message saying I've restarted.  For example:

Sep 24 18:41:57 kandos -- MARK --
Sep 24 19:01:57 kandos -- MARK --
Sep 24 19:06:53 kandos kernel: [ 5515.400231] kjournald starting.  Commit interval 5 seconds
Sep 24 19:06:53 kandos kernel: [ 5515.400576] EXT3 FS on sdb2, internal journal
Sep 24 19:06:53 kandos kernel: [ 5515.400578] EXT3-fs: recovery complete.
Sep 24 19:06:53 kandos kernel: [ 5515.400798] EXT3-fs: mounted filesystem with ordered data mode.
Sep 24 19:11:46 kandos syslogd 1.5.0#5ubuntu3: restart.

Here, I've mounted the drive I wish to transfer data from into my Home Folder.  Then, I attempt to move the files:

mv -v * /home/Animation

After about three files, or 300Mb worth of data, the verbose output stops and the entire system is frozen, regardless of how long I leave it.

Why would only large file transfers between disks cause this freeze?

Smaller transfers don't seem to have the same problem.

---

### Post by ebenedito on 2009-09-24
Hi There,

Sorry for adding more "crying for help here!", rather than adding any value, but I thought your case may be related to mine.

I love Ubuntu, but I find 9.0.4 quite *unstable*.. I am running the studio version. My first attempt was on an Intel dual core2 and that did not go very well. Freezes and lock ups very frequently (< hours). I then installed it on an old hp compaq box (32bits) and although the system is more usable, I get system hangs every day.  Hangs could come in different flavours, sometimes slow lockups (starts with not being able to open new apps, bash shells getting stuck) but mouse and some menus are responsive to the point I can't even shut down the machine or the mouse pointer freezes - then the only escape is the red button.. 

Here is some info if this can help..
Cheers (and thanks in advance for the help)

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
Sep 24 13:37:39 mars kernel: [13209.932170] Pid: 4521, comm: javac Tainted: G        W  (2.6.28-3-rt #12-Ubuntu) HP Compaq dc7100 SFF(PC924A)
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
Sep 24 13:37:39 mars kernel: [13209.932170] ---[ end trace 5592ad72e87054ef ]---

---

### Post by ebenedito on 2009-09-24
with this last lockup I am still able to do some things..   so here is the situation

- I have an extended partition on /dev/sda5 .. 
- I then mounted it as "sudo mount -t ext3 /dev/sda5 /hosts/RH9" (since it has some RH9 contents)..  
- I was chrooted into this partition  "sudo chroot /hosts/RH9 /bin/bash".. 
- I was doing some work there when it hanged..

Now if I go back to the folder and try to do an ls, it hangs.. It is blocking on the getdents64 syscall..  This is what I get when I strace it.


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
open(".", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 3
fstat64(3, {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
fcntl64(3, F_GETFD)                     = 0x1 (flags FD_CLOEXEC)
getdents64(3, 
.... and it hangs there.. never returned from kernel..

---

### Post by ebenedito on 2009-09-24
Kandos.. Sorry for taking over your thread.. I think my problem is confined and reproducible at will - so I moved my posting to another thread.. Sorry again..
[http://ubuntuforums.org/showthread.php?p=8001205#post8001205](http://ubuntuforums.org/showthread.php?p=8001205#post8001205)
cheers

---

### Post by kandos on 2009-09-26
No problems, ebenedito.  It seems that I need to become more familiar with the processes before I can start hunting down the problem.  I might start with learning what strace is.

Thanks.

---

