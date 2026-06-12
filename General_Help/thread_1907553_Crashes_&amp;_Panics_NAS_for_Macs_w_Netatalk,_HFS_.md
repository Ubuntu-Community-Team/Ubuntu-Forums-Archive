---
title: "Crashes &amp; Panics: NAS for Macs w/ Netatalk, HFS drives, USB wifi dongle."
date: 2012-01-11
forum: General Help
---

### Post by orisdorch on 2012-01-11
Hey Folks! 

I'm fairly new to ubuntu, so please bare with me! Been a bit of an Apple power user, but Linux gets a whole lot more complicated - though I love the amount of control and flexibility it gives!

Here's are my Issues (likely related): Intermittent (~daily) mix of crashes and kernel panics. Kernel Panic log below - not sure how to recover prior boot's crash log.. Kernel Panic screen can be 'exited' with Ctrl-alt-F6 then Ctrl-alt-F7, though the computer doesn't like to shut down after kernel panics -- hangs on 'Kubuntu' shut-down screen.. Beyond the panics, my crashes involve fans spinning and lights being on, but monitor will not turn on to mouse clicks / keystrokes, keyboard lights will not turn on / of (i.e. caps lock), and SSH is unavailable.. Have to do a hard shut-down (hold power button). .

Hardware: IBM Think Centre A50: P4 3.8ghz, 1GB Ram,  40GB HD.
Additional HW: Internal 400GB HFS+ HD (Journaling disabled), Tenda wireless USB dongle, Enternal 2TB HFS+ HD (Journaling disabled, recent addition - problem occurred before), DVDR
Additional SW: Netatalk, HFS utils, Avahi, Open SSH, X11VNC.

Notes: I initially installed Ubuntu 11.10, then added XFCE4, Xubuntu Desktop, and Kubuntu Desktop..  I use Xubuntu Desktop. So far this computer serves as a NAS server for other Apple computers in the house.. Not much else on this machine at this point..

Setup Netatalk and Avahi based on [http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/](http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/)  -- though did not compile netatalk separately, just used the packaged version in ubuntu as apparently it no longer needs to be compiled due to updates to the base config.

Due to crashes and other issues, I've had to force power-off the computer on several occations, and perform umount -l on the 400gb HFS drive, causing corrupt catalogue and incorrect file counts (corrected with fsck_hfsplus).

Added to fstab:
/dev/sdb2 /home/zryan/Timemachine hfsplus rw,exec,auto,nosuid,nodev,user 0 0

Example of a manual mount command:
sudo mount -t hfsplus -o rw,nosuid,nodev /dev/sdb2 /[mountpoint]
Netatalk options used: cnidscheme:dbd options:usedots,tm

Looking over my dmesg, I see a few other concerning lines that may be somehow related.. These are near boot:
[    0.543320] Critical temperature reached (90 C), shutting down.
[    0.543437] thermal LNXTHERM:00: registered as thermal_zone0
[    0.543443] ACPI: Thermal Zone [THM0] (90 C)
...
[    6.463147] scsi 2:0:0:0: Direct-Access     Seagate  External         SG12 PQ: 0 ANSI: 4
[    6.463279] scsi: killing requests for dead queue
[    6.463425] scsi: killing requests for dead queue
[    6.464126] scsi: killing requests for dead queue
[    6.464240] scsi: killing requests for dead queue
[    6.469146] scsi: killing requests for dead queue
[    6.476167] scsi: killing requests for dead queue
[    6.476297] scsi: killing requests for dead queue
[    6.476550] scsi: killing requests for dead queue
...
[   19.738271] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   19.833219] intel_rng: Firmware space is locked read-only. If you can't or
[   19.833224] intel_rng: don't want to disable this in firmware setup, and if
[   19.833226] intel_rng: you are certain that your system has a functional
[   19.833229] intel_rng: RNG, try using the 'no_fwh_detect' option.
...
A WHOLE BUNCH of entries like this, with varying frequencies and reg. rules:
[   20.575943] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   20.575952] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
...
[   31.000773] [drm] capturing error event; look for more information in /debug/dri/0/i915_error_state
[   31.004027] render error detected, EIR: 0x00000010
[   31.004027] [drm:i915_report_and_clear_eir] *ERROR* EIR stuck: 0x00000010, masking
[   31.004027] render error detected, EIR: 0x00000010
[   33.260661] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0


Latest Kernel Panic occurred ~1hr after boot a little after accessing ubuntu's drives using Netatalk:
[ 1433.229355] BUG: unable to handle kernel NULL pointer dereference at   (null)
[ 1433.229447] IP: [<c102b8e0>] kmap+0x10/0x60
[ 1433.229498] *pde = 1b6e3067 *pte = 00000000 
[ 1433.229533] Oops: 0000 [#1] SMP 
[ 1433.229564] Modules linked in: dm_crypt ppdev appletalk snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_seq_midi snd_rawmidi arc4 snd_seq_midi_event rt2800usb rt2800lib crc_ccitt rt2x00usb rt2x00lib mac80211 snd_seq cfg80211 snd_timer snd_seq_device snd psmouse soundcore snd_page_alloc serio_raw binfmt_misc shpchp nls_utf8 parport_pc hfsplus lp parport usbhid hid usb_storage uas i915 e1000 drm_kms_helper drm i2c_algo_bit video floppy
[ 1433.229985] 
[ 1433.230000] Pid: 1981, comm: duplicity Not tainted 3.0.0-14-generic #23-Ubuntu IBM 8183WR4/IBM
[ 1433.230069] EIP: 0060:[<c102b8e0>] EFLAGS: 00010246 CPU: 0
[ 1433.230108] EIP is at kmap+0x10/0x60
[ 1433.230133] EAX: 00000000 EBX: 00000000 ECX: 0000e8b1 EDX: d6984000
[ 1433.230175] ESI: 00000002 EDI: 000008b1 EBP: d6985b94 ESP: d6985b90
[ 1433.230217]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
[ 1433.230255] Process duplicity (pid: 1981, ti=d6984000 task=debeb300 task.ti=d6984000)
[ 1433.230310] Stack:
[ 1433.230327]  dea756c0 d6985bb0 e00bafd0 0000001a d6985bbe dea756c0 00002000 00001b73
[ 1433.230402]  d6985bc0 e00bb05c 00000002 b1e85c28 d6985bd8 e00bc7e5 e00bc760 00000004
[ 1433.230479]  dea756c0 d6985c28 d6985bfc e00bd32a 00000000 d6985e58 de532000 e8b10004
[ 1433.230554] Call Trace:
[ 1433.230581]  [<e00bafd0>] hfsplus_bnode_read+0x40/0xb0 [hfsplus]
[ 1433.230626]  [<e00bb05c>] hfsplus_bnode_read_u16+0x1c/0x30 [hfsplus]
[ 1433.230673]  [<e00bc7e5>] hfsplus_brec_keylen+0x65/0x90 [hfsplus]
[ 1433.230718]  [<e00bc760>] ? hfsplus_brec_lenoff+0x30/0x50 [hfsplus]
[ 1433.230763]  [<e00bd32a>] hfsplus_brec_goto+0x8a/0x140 [hfsplus]
[ 1433.230810]  [<e00b99d5>] hfsplus_readdir+0x195/0x530 [hfsplus]
[ 1433.230858]  [<c1138f00>] ? sys_ioctl+0x80/0x80
[ 1433.230895]  [<c1001c24>] ? __switch_to+0x94/0x1a0
[ 1433.230933]  [<c1037f60>] ? finish_task_switch+0x40/0xc0
[ 1433.230974]  [<c152baf1>] ? __schedule+0x2f1/0x620
[ 1433.231011]  [<c107114b>] ? ktime_get_ts+0xeb/0x120
[ 1433.231045]  [<c1026208>] ? default_spin_lock_flags+0x8/0x10
[ 1433.231087]  [<c152dd0d>] ? _raw_spin_lock_irqsave+0x2d/0x40
[ 1433.231129]  [<c10b12e6>] ? delayacct_end+0x96/0xb0
[ 1433.231163]  [<c1026208>] ? default_spin_lock_flags+0x8/0x10
[ 1433.231205]  [<c152dd0d>] ? _raw_spin_lock_irqsave+0x2d/0x40
[ 1433.231253]  [<c11246f7>] ? swap_cgroup_record+0x67/0x80
[ 1433.231296]  [<c1124077>] ? mem_cgroup_uncharge_swap+0x27/0x60
[ 1433.231338]  [<c110c648>] ? swap_entry_free+0x108/0x170
[ 1433.231376]  [<c10fddba>] ? do_swap_page+0x36a/0x580
[ 1433.231414]  [<c1136483>] ? path_openat+0xc3/0x350
[ 1433.231449]  [<c10ff6ea>] ? handle_pte_fault+0x19a/0x220
[ 1433.231486]  [<c10ff878>] ? handle_mm_fault+0x108/0x210
[ 1433.231525]  [<c1223960>] ? security_file_permission+0x90/0xb0
[ 1433.231567]  [<c1139226>] vfs_readdir+0xa6/0xd0
[ 1433.231599]  [<c1138f00>] ? sys_ioctl+0x80/0x80
[ 1433.231632]  [<c11393d8>] sys_getdents64+0x68/0xc0
[ 1433.231669]  [<c152def4>] syscall_call+0x7/0xb
[ 1433.231706]  [<c1520000>] ? ext3_load_journal+0x1ea/0x246
[ 1433.231741] Code: 74 26 00 8b 15 c8 05 88 c1 e8 ed fe ff ff 5d c3 8d 74 26 00 8d bc 27 00 00 00 00 55 89 e5 53 3e 8d 74 26 00 89 c3 e8 90 05 50 00 <8b> 03 c1 e8 1e 69 c0 40 03 00 00 05 00 34 7b c1 2b 80 0c 03 00 
[ 1433.233274] EIP: [<c102b8e0>] kmap+0x10/0x60 SS:ESP 0068:d6985b90
[ 1433.233274] CR2: 0000000000000000
[ 1433.278165] ---[ end trace a1cf1c3de0f65c8a ]---

---

### Post by orisdorch on 2012-01-12
No tips, suggestions, or even guidance on which log files I should be checking?

---

### Post by orisdorch on 2012-01-13
Alright.. Formatted and trying again from a clean install...

---

### Post by orisdorch on 2012-01-14
Okay, so a clean install actually did it.. NAS is running smoothly now. must have run into corruption of some sort.

**UPDATE - Crashes cropped up again.. Gave up on this part of the forum and moved thread here:
[http://ubuntuforums.org/showthread.php?p=11644593&posted=1#post11644593](http://ubuntuforums.org/showthread.php?p=11644593&posted=1#post11644593)

---

