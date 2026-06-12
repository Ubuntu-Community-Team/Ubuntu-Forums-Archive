---
title: "Unresponsiveness in 9.10: ext4, jbd2?"
date: 2009-12-26
forum: General Help
---

### Post by jvroutak on 2009-12-26
Hi all

I couldn't find anyone other with exactly the same symptoms as my system has.

I have a 9.10 Ubuntu installation, upgraded from 9.04, quite typical desktop PC setup. Root file system is ext4, graphics card is nvidia with 180 driver. See end of post for specs.

Problem is that some desktop applications sometimes go unresponsive. Firefox (karmic 3.5.6, tested with a fresh profile & ran from xterm session so shouldn't be from corrupt user setup) seems to have the largest tendency to this, but other applications seem to freeze in the middle of displaying a menu etc. When some application has gone unresponsive, other tasks usually go unresponsive as well (for example, can't log in a virtual terminal, or even execute simple commands, man for example). The unresponsive behaviour doesn't seem to be easily reproducible, it just happens sometimes (of course usually when you wouldn't exactly need a coffee break :). 

The desktop doesn't freeze totally, the desktop minimize/maximize etc works fine, though the frozen app is obviously frozen (not updated). The app will *always* become responsive after a while (can take ten secs to a couple of minutes). Otherwise the system seems to be quite stable, no data loss or crashes so far. I wouldn't suspect HW problems.

The unresponsive process seems to be waiting for IO. The Gnome System Monitor *always* shows the app in question to be waiting for

```
blkdev_issue_flush
jbd2_log_wait_commit

```which would seem to indicate the problem is related to ext4 or jbd2 access, which I think differs from accessing ext3. Perhaps a timeout or a race condition of some kind? Unfortunately, Ubuntu kernels are compiled without support for debugging jbd2, so I don't have debug data. A recompile would be needed and I wouldn't like to go to that road unless it's the only way. 

ext4 can't be converted to ext3 (afaik), but one thing that might be worth the try would be copy -> reformat to ext3 -> copy back. Also that is quite a task so wouldn't like to do that unless necessary.

Any ideas? Have you have similar problems?

-Juho

***EDIT**: It seems that the reason for the unresponsiveness is that Firefox uses fsync() calls which will force the cached data to be synced to disk, which can take a long time. Probably Firefox has also reserved some other resource that is unavailable to others until the fsync() has finished. A partial solution is proposed here: [http://ubuntuforums.org/showthread.php?t=1120475](http://ubuntuforums.org/showthread.php?t=1120475), and this even seems to work but is far from a good solution. It can lead to data loss and is a mess to maintain in a system with multiple users. A proper solution would be fixing Firefox and possibly **ext4/jbd2** code. In any case, a problem in one application should not make the whole system unresponsive.*

```

[juho@norppa:~]$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 10)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9400 GT] (rev a1)
02:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller (rev b0)


[juho@norppa:~]$ uname -a
Linux norppa 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686 GNU/Linux


[juho@norppa:~]$ mount
/dev/sdc5 on / type ext4 (rw,noatime,data=writeback,errors=remount-ro,debug,commit=10)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sdc1 on /boot type ext3 (rw,relatime)
none on /proc/fs/vmblock/mountPoint type vmblock (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/juho/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=juho)


[juho@norppa:~]$ lsmod
Module                  Size  Used by
binfmt_misc             8356  1
vmnet                  40252  13
vmblock                12576  1
vmci                   49684  0
vmmon                  70416  0
snd_hda_codec_via      28988  1
snd_hda_intel          26920  6
snd_hda_codec          75708  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0
snd_mixer_oss          16028  1 snd_pcm_oss
nvidia               9586440  36
snd_pcm                75296  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
lp                      8964  0
snd_seq_dummy           2656  0
psmouse                56500  0
snd_seq_oss            28576  0
serio_raw               5280  0
snd_seq_midi            6432  0
ppdev                   6688  0
asus_atk0110            8252  0
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
usblp                  12636  0
parport_pc             31940  1
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iptable_filter          3100  0
parport                35340  3 lp,ppdev,parport_pc
snd_timer              22276  3 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  21 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
usbhid                 38208  0
usb_storage            52576  0
atl1e                  31824  0
intel_agp              27484  0
agpgart                34988  2 nvidia,intel_agp

```

---

