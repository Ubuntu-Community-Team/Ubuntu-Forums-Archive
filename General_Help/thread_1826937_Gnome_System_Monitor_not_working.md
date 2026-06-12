---
title: "Gnome System Monitor not working"
date: 2011-08-17
forum: General Help
---

### Post by evaliauka on 2011-08-17
I'm using ubuntu 10.04.
After update to 2.6.32-34 kernel gnome-system-monitor craches(sometimes freezes) when switching to processes tab.

kernel.log :
```

Aug 17 15:14:26 evaliauka kernel: [11308.858611] BUG: unable to handle kernel paging request at fffffff3
Aug 17 15:14:26 evaliauka kernel: [11308.858617] IP: [<c024d582>] vma_stop+0x12/0x30
Aug 17 15:14:26 evaliauka kernel: [11308.858623] *pde = 00855067 *pte = 00000000 
Aug 17 15:14:26 evaliauka kernel: [11308.858626] Oops: 0000 [#3] SMP 
Aug 17 15:14:26 evaliauka kernel: [11308.858629] last sysfs file: /sys/devices/virtual/net/tun0/statistics/collisions
Aug 17 15:14:26 evaliauka kernel: [11308.858633] Modules linked in: binfmt_misc ppdev nls_iso8859_1 nls_cp437 vfat fat snd_hda_codec_realtek snd_hda_codec_intelhdmi fbcon tileblit font bitblit softcursor vga16fb vgastate usbhid hid snd_usb_audio snd_pcm_oss snd_mixer_oss snd_hda_intel snd_hda_codec snd_pcm i915 drm_kms_helper drm snd_seq_dummy snd_usb_lib snd_seq_oss snd_seq_midi snd_seq_midi_event snd_seq snd_timer snd_rawmidi snd_seq_device snd_hwdep intel_agp snd i2c_algo_bit video output agpgart soundcore snd_page_alloc lp parport ohci1394 ieee1394 r8169 mii
Aug 17 15:14:26 evaliauka kernel: [11308.858674] 
Aug 17 15:14:26 evaliauka kernel: [11308.858677] Pid: 20031, comm: gnome-system-mo Tainted: G      D    (2.6.32-34-generic #73-Ubuntu) EG41MF-US2H
Aug 17 15:14:26 evaliauka kernel: [11308.858680] EIP: 0060:[<c024d582>] EFLAGS: 00010213 CPU: 0
Aug 17 15:14:26 evaliauka kernel: [11308.858683] EIP is at vma_stop+0x12/0x30
Aug 17 15:14:26 evaliauka kernel: [11308.858685] EAX: eec4a150 EBX: eec4a150 ECX: c05a2828 EDX: fffffff3
Aug 17 15:14:26 evaliauka kernel: [11308.858688] ESI: eef9fe40 EDI: fffffff3 EBP: eec23f10 ESP: eec23f0c
Aug 17 15:14:26 evaliauka kernel: [11308.858690]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Aug 17 15:14:26 evaliauka kernel: [11308.858693] Process gnome-system-mo (pid: 20031, ti=eec22000 task=f06bb300 task.ti=eec22000)
Aug 17 15:14:26 evaliauka kernel: [11308.858695] Stack:
Aug 17 15:14:26 evaliauka kernel: [11308.858696]  eec4a150 eec23f1c c024d8a3 efe34000 eec23f64 c02253ed 00001000 000000d0
Aug 17 15:14:26 evaliauka kernel: [11308.858703] <0> 00000000 fffffff3 b6664000 eef9fe68 00000400 00000000 e1192280 00000000
Aug 17 15:14:26 evaliauka kernel: [11308.858710] <0> e11ec000 00000000 00000000 e1192280 00000400 b6664000 eec23f8c c020a80f
Aug 17 15:14:26 evaliauka kernel: [11308.858718] Call Trace:
Aug 17 15:14:26 evaliauka kernel: [11308.858721]  [<c024d8a3>] ? m_stop+0x13/0x30
Aug 17 15:14:26 evaliauka kernel: [11308.858725]  [<c02253ed>] ? seq_read+0x16d/0x3a0
Aug 17 15:14:26 evaliauka kernel: [11308.858729]  [<c020a80f>] ? vfs_read+0x9f/0x1a0
Aug 17 15:14:26 evaliauka kernel: [11308.858732]  [<c0225280>] ? seq_read+0x0/0x3a0
Aug 17 15:14:26 evaliauka kernel: [11308.858735]  [<c020a9c2>] ? sys_read+0x42/0x70
Aug 17 15:14:26 evaliauka kernel: [11308.858739]  [<c01033ec>] ? syscall_call+0x7/0xb
Aug 17 15:14:26 evaliauka kernel: [11308.858744]  [<c0590000>] ? kprobes_module_callback+0x30/0x100
Aug 17 15:14:26 evaliauka kernel: [11308.858746] Code: 8b 5d 08 2b 48 6c 89 0b 8b 48 58 03 0a 8b 55 0c 89 0a 8b 40 64 5b 5e 5d c3 55 89 e5 53 0f 1f 44 00 00 85 d2 74 16 39 50 08 74 11 <8b> 1a 8d 43 38 e8 64 f8 f1 ff 89 d8 e8 fd de ef ff 5b 5d c3 8d 
Aug 17 15:14:26 evaliauka kernel: [11308.858785] EIP: [<c024d582>] vma_stop+0x12/0x30 SS:ESP 0068:eec23f0c
Aug 17 15:14:26 evaliauka kernel: [11308.858790] CR2: 00000000fffffff3
Aug 17 15:14:26 evaliauka kernel: [11308.858793] ---[ end trace 974b4620516ab243 ]---


```[B]

BUT[/B]:
```

sudo gnome-system-monitor

```works fine and shows all processes (owned by root and by my user evaliauka)

---

### Post by evaliauka on 2011-08-17
Seems like ssh-agent is causing the issue.

strace output of gnome-system-monitor without sudo ends with:
```

17:13:16.159210 munmap(0xb637e000, 4096) = 0
17:13:16.159255 stat64("/proc/1472", {st_mode=S_IFDIR|0555, st_size=0, ...}) = 0
17:13:16.159539 open("/proc/1472/stat", O_RDONLY) = 18
17:13:16.159580 read(18, "1472 (ssh-agent) S 1438 1472 147"..., 8191) = 155
17:13:16.159633 read(18, "", 8036)      = 0
17:13:16.159660 close(18)               = 0
17:13:16.159690 open("/proc/1472/stat", O_RDONLY) = 18
17:13:16.159727 read(18, "1472 (ssh-agent) S 1438 1472 147"..., 8191) = 155
17:13:16.159773 read(18, "", 8036)      = 0
17:13:16.159799 close(18)               = 0
17:13:16.159979 open("/proc/1472/cpu", O_RDONLY) = -1 ENOENT (No such file or directory)
17:13:16.160036 open("/proc/1472/cmdline", O_RDONLY|O_LARGEFILE) = 18
17:13:16.160085 fstat64(18, {st_mode=S_IFREG|0444, st_size=0, ...}) = 0
17:13:16.160155 fcntl64(18, F_GETFL)    = 0x8000 (flags O_RDONLY|O_LARGEFILE)
17:13:16.160193 fstat64(18, {st_mode=S_IFREG|0444, st_size=0, ...}) = 0
17:13:16.160264 mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb637e000
17:13:16.160307 _llseek(18, 0, [0], SEEK_CUR) = 0
17:13:16.160352 read(18, "/usr/bin/ssh-agent\0/usr/bin/dbus"..., 4096) = 74
17:13:16.160412 read(18, "", 3072)      = 0
17:13:16.160452 close(18)               = 0
17:13:16.160489 munmap(0xb637e000, 4096) = 0
17:13:16.160543 open("/proc/1472/attr/current", O_RDONLY|O_LARGEFILE) = 18
17:13:16.160595 read(18, "unconfined\n", 4095) = 11
17:13:16.160636 close(18)               = 0
17:13:16.160677 open("/proc/1472/stat", O_RDONLY) = 18
17:13:16.160721 read(18, "1472 (ssh-agent) S 1438 1472 147"..., 8191) = 155
17:13:16.160776 read(18, "", 8036)      = 0
17:13:16.160811 close(18)               = 0
17:13:16.160849 open("/proc/1472/wchan", O_RDONLY) = 18
17:13:16.160894 read(18, "poll_schedule_timeout", 39) = 21
17:13:16.160941 read(18, "", 18)        = 0
17:13:16.160977 close(18)               = 0
17:13:16.161013 stat64("/proc/1472", {st_mode=S_IFDIR|0555, st_size=0, ...}) = 0
17:13:16.161100 open("/proc/1472/stat", O_RDONLY) = 18
17:13:16.161144 read(18, "1472 (ssh-agent) S 1438 1472 147"..., 8191) = 155
17:13:16.161198 read(18, "", 8036)      = 0
17:13:16.161233 close(18)               = 0
17:13:16.161270 open("/proc/1472/status", O_RDONLY) = 18
17:13:16.161314 read(18, "Name:\tssh-agent\nState:\tS (sleepi"..., 8191) = 780
17:13:16.161386 read(18, "", 7411)      = 0
17:13:16.161420 close(18)               = 0
17:13:16.161458 open("/proc/1472/stat", O_RDONLY) = 18
17:13:16.161501 read(18, "1472 (ssh-agent) S 1438 1472 147"..., 8191) = 155
17:13:16.161553 read(18, "", 8036)      = 0
17:13:16.161589 close(18)               = 0
17:13:16.161626 open("/proc/1472/stat", O_RDONLY) = 18
17:13:16.161668 read(18, "1472 (ssh-agent) S 1438 1472 147"..., 8191) = 155
17:13:16.161721 read(18, "", 8036)      = 0
17:13:16.161756 close(18)               = 0
17:13:16.161793 open("/proc/1472/cpu", O_RDONLY) = -1 ENOENT (No such file or directory)
17:13:16.161854 open("/proc/1472/statm", O_RDONLY) = 18
17:13:16.161899 read(18, "821 89 37 19 0 69 0\n", 8191) = 20
17:13:16.161942 read(18, "", 8171)      = 0
17:13:16.161975 close(18)               = 0
17:13:16.162015 open("/proc/1472/smaps", O_RDONLY) = 18
17:13:16.162060 fstat64(18, {st_mode=S_IFREG|0444, st_size=0, ...}) = 0
17:13:16.162129 mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb637e000
17:13:16.162167 read(18,  <unfinished ...>
17:13:16.163676 +++ killed by SIGKILL +++

```strace output of gnome-system-monitor with sudo contains the following lines:

```

17:02:51.281318 munmap(0xb788e000, 4096) = 0
17:02:51.281378 munmap(0xb6647000, 135168) = 0
17:02:51.281441 stat64("/proc/1461", {st_mode=S_IFDIR|0555, st_size=0, ...}) = 0
17:02:51.281552 open("/proc/1461/stat", O_RDONLY) = 16
17:02:51.281610 read(16, "1461 (ssh-agent) S 1427 1461 146"..., 8191) = 192
17:02:51.281676 read(16, "", 7999)      = 0
17:02:51.281713 close(16)               = 0
17:02:51.282001 open("/proc/1461/stat", O_RDONLY) = 16
17:02:51.282053 read(16, "1461 (ssh-agent) S 1427 1461 146"..., 8191) = 192
17:02:51.282121 read(16, "", 7999)      = 0
17:02:51.282159 close(16)               = 0
17:02:51.282205 open("/proc/1461/cpu", O_RDONLY) = -1 ENOENT (No such file or directory)
17:02:51.282270 open("/proc/1461/cmdline", O_RDONLY|O_LARGEFILE) = 16
17:02:51.282323 fstat64(16, {st_mode=S_IFREG|0444, st_size=0, ...}) = 0
17:02:51.282416 fcntl64(16, F_GETFL)    = 0x8000 (flags O_RDONLY|O_LARGEFILE)
17:02:51.282460 fstat64(16, {st_mode=S_IFREG|0444, st_size=0, ...}) = 0
17:02:51.282553 mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb788e000
17:02:51.282603 _llseek(16, 0, [0], SEEK_CUR) = 0
17:02:51.282651 read(16, "/usr/bin/ssh-agent\0/usr/bin/dbus"..., 4096) = 74
17:02:51.282716 read(16, "", 3072)      = 0
17:02:51.282762 close(16)               = 0
17:02:51.282801 munmap(0xb788e000, 4096) = 0
17:02:51.283044 open("/proc/1461/attr/current", O_RDONLY|O_LARGEFILE) = 16
17:02:51.283103 read(16, "unconfined\n", 4095) = 11
17:02:51.283150 close(16)               = 0
17:02:51.283198 open("/proc/1461/stat", O_RDONLY) = 16
17:02:51.283252 read(16, "1461 (ssh-agent) S 1427 1461 146"..., 8191) = 192
17:02:51.283321 read(16, "", 7999)      = 0
17:02:51.283360 close(16)               = 0
17:02:51.283404 open("/proc/1461/wchan", O_RDONLY) = 16
17:02:51.283457 read(16, "poll_schedule_timeout", 39) = 21
17:02:51.283517 read(16, "", 18)        = 0
17:02:51.283560 close(16)               = 0
17:02:51.283603 stat64("/proc/1461", {st_mode=S_IFDIR|0555, st_size=0, ...}) = 0
17:02:51.283699 open("/proc/1461/stat", O_RDONLY) = 16
17:02:51.283895 read(16, "1461 (ssh-agent) S 1427 1461 146"..., 8191) = 192
17:02:51.284170 read(16, "", 7999)      = 0
17:02:51.284215 close(16)               = 0
17:02:51.284262 open("/proc/1461/status", O_RDONLY) = 16
17:02:51.284316 read(16, "Name:\tssh-agent\nState:\tS (sleepi"..., 8191) = 782
17:02:51.284411 read(16, "", 7409)      = 0
17:02:51.284454 close(16)               = 0
17:02:51.284501 open("/proc/1461/stat", O_RDONLY) = 16
17:02:51.284554 read(16, "1461 (ssh-agent) S 1427 1461 146"..., 8191) = 192
17:02:51.284619 read(16, "", 7999)      = 0
17:02:51.284658 close(16)               = 0
17:02:51.284702 open("/proc/1461/stat", O_RDONLY) = 16
17:02:51.284755 read(16, "1461 (ssh-agent) S 1427 1461 146"..., 8191) = 192
17:02:51.284823 read(16, "", 7999)      = 0
17:02:51.284860 close(16)               = 0
17:02:51.284904 open("/proc/1461/cpu", O_RDONLY) = -1 ENOENT (No such file or directory)
17:02:51.284973 open("/proc/1461/statm", O_RDONLY) = 16
17:02:51.285026 read(16, "821 90 37 19 0 69 0\n", 8191) = 20
17:02:51.285282 read(16, "", 8171)      = 0
17:02:51.285400 close(16)               = 0
17:02:51.285449 open("/proc/1461/smaps", O_RDONLY) = 16
17:02:51.285505 fstat64(16, {st_mode=S_IFREG|0444, st_size=0, ...}) = 0
17:02:51.285603 mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb788e000
17:02:51.285650 read(16, "00269000-0026a000 r-xp 00000000 "..., 1024) = 1024
17:02:51.285759 read(16, "     0 kB\nReferenced:           "..., 1024) = 1024
17:02:51.285850 read(16, "2 kB\nShared_Clean:          0 kB"..., 1024) = 1024
17:02:51.285937 read(16, "    /lib/ld-2.11.1.so\nSize:     "..., 1024) = 1024
17:02:51.286019 read(16, " 0 kB\nSwap:                  0 k"..., 1024) = 1024
17:02:51.286111 read(16, "          32 kB\nShared_Clean:   "..., 1024) = 1024
17:02:51.286390 read(16, "     /usr/bin/ssh-agent\nSize:   "..., 1024) = 1024
17:02:51.286480 read(16, " kB\nKernelPageSize:        4 kB\n"..., 1024) = 1024
17:02:51.286569 read(16, "\nPrivate_Dirty:         4 kB\nRef"..., 1024) = 1024
17:02:51.286655 read(16, "       0 kB\nShared_Dirty:       "..., 1024) = 922
17:02:51.286737 read(16, "", 1024)      = 0
17:02:51.286778 close(16)               = 0


```
I did re-install openssh-client but that did not help. How ssh-agent cat break gnome-system-monitor?
Please, help!

---

### Post by dino99 on 2011-08-17
report on launchpad

ubuntu-bug gnome-system-monitor

add the strace you got

---

### Post by Enigmapond on 2011-08-17
I have the same issue. You are not alone. It was definitely the kernel update as if I boot into the previous, it works just fine.

---

### Post by evaliauka on 2011-08-17
I found that 
```
kill -9 $(pidof ssh-agent)
```
and
```
kill -9 $(pidof gnome-pty-helper)
```

makes the System Monitor working.

Any ideas?

---

### Post by evaliauka on 2011-08-17
Found it on launchpad:
[https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/827038](https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/827038)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/825207](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/825207)

:popcorn:

---

### Post by Paper Bag on 2011-08-17
Same problem, with same symptoms. 10.10 and 2.6.35.30.

---

### Post by raja.genupula on 2011-08-17
after looking many post i have given a try  and got this . no much worries because i got my window but thinking about the warning


```
assassin@genupulas:~$ sudo gnome-system-monitor
[sudo] password for assassin: 

[B]** (gnome-system-monitor:3916): WARNING **: SELinux was found but is not enabled.
[/B]
assassin@genupulas:~$ 
```

---

### Post by AlfyBoy on 2011-08-17
Thanks:

> **Enigmapond said:**
> I have the same issue. You are not alone. It was definitely the kernel update as if I boot into the previous, it works just fine.

I have the same problem, but with older versions works just fine.
I'm using kernel:

```
$ uname -r
2.6.32-33-generic
```

And now I have it working... :lolflag:

---

### Post by okropnick on 2011-08-17
Same problem here:

```

user@system:~$ gnome-system-monitor 

** (gnome-system-monitor:31175): WARNING **: SELinux was found but is not enabled.

Killed


```

---

### Post by Enigmapond on 2011-08-17
> **AlfyBoy said:**
> Thanks:



I have the same problem, but with older versions works just fine.
I'm using kernel:

```
$ uname -r
2.6.32-33-generic
```And now I have it working... :lolflag:
I keep one older one just for this reason...but in 4 years with Linux this is the first time I've had to do it...:)

---

### Post by emarkay on 2011-08-19
As this appears to be a kernel issue, I hope it is addressed promptly...

---

### Post by AlfyBoy on 2011-08-20
The new kernel update has fixed this issue, from 2.6.32-34.35 (lucid-proposed) to 2.6.32-34.74 (lucid-proposed):

```
$ uname -r
2.6.32-34-generic
```

And now it works...

Cheers... :guitar:

---

### Post by evaliauka on 2011-08-22
Gnome system monitor works fine with the latest kernel update (#74).
:-\"

---

