---
title: "Repeated lockups on multiple machines, 10.04."
date: 2010-09-27
forum: General Help
---

### Post by Kyle_S on 2010-09-27
I have two computer labs full of identical Dell Optiplex GX620, one lab (20 machines) running Ubuntu 10.04 i686, the other lab (30 machines) running Ubuntu 10.04 x86_64.  50 machines total, all with the same bug.

They both have the same set of packages, and are on 2.6.32-24-generic, with their respective architectures of course.  All machines are directing their syslog information to a central syslog server.

In both labs, I have machines lockup with a message of the form:
kernel: [  ] INFO: task $PROCESSNAME:$PID blocked for more than 120 seconds.
kernel: [  ] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.

Where PROCESSNAME is almost anything that's run on the system.  I've seen apt-get, sshd, ldm, modprobe, vim, and others.

After this happens, existing processes continue to run, albeit slowly, but no further processes may be started, which means I can't ssh in, login, or even launch shutdown (if I was actually already on that system in a root shell).

It happens on all of these machines, not just selected ones.

It happens more under heavy loads, but also happens on systems that are booted up, and never used.

Running memtest for 24 hours on these machines turns up no memory errors.

This is killing me.  Please help.

Here's a copy-paste from one machine that died a few minutes ago:
Sep 27 12:22:49 gvm13 kernel: [  481.296035] INFO: task apt-get:1493 blocked for more than 120 seconds.
Sep 27 12:22:49 gvm13 kernel: [  481.296041] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Sep 27 12:22:49 gvm13 kernel: [  481.296046] apt-get       D 000033e1     0  1493   1485 0x00000000
Sep 27 12:22:49 gvm13 kernel: [  481.296055]  f678dc64 00000086 f69b8000 000033e1 00000000 c0849760 f69368ac c0849760
Sep 27 12:22:49 gvm13 kernel: [  481.296067]  a396e60d 0000004a c0849760 c0849760 f69368ac c0849760 c0849760 f6bff400
Sep 27 12:22:49 gvm13 kernel: [  481.296078]  00000001 0000004a f6936600 c2508760 f6936600 f678dcb0 f678dc74 c058b16a
Sep 27 12:22:49 gvm13 kernel: [  481.296090] Call Trace:
Sep 27 12:22:49 gvm13 kernel: [  481.296103]  [<c058b16a>] io_schedule+0x3a/0x60
Sep 27 12:22:49 gvm13 kernel: [  481.296109]  [<c022d2c8>] sync_buffer+0x38/0x40
Sep 27 12:22:49 gvm13 kernel: [  481.296115]  [<c058b90d>] __wait_on_bit+0x4d/0x70
Sep 27 12:22:49 gvm13 kernel: [  481.296125]  [<c022d290>] ? sync_buffer+0x0/0x40
Sep 27 12:22:49 gvm13 kernel: [  481.296129]  [<c022d290>] ? sync_buffer+0x0/0x40
Sep 27 12:22:49 gvm13 kernel: [  481.296133]  [<c058b9db>] out_of_line_wait_on_bit+0xab/0xc0
Sep 27 12:22:49 gvm13 kernel: [  481.296139]  [<c0167860>] ? wake_bit_function+0x0/0x50
Sep 27 12:22:49 gvm13 kernel: [  481.296144]  [<c022d28e>] __wait_on_buffer+0x2e/0x30
Sep 27 12:22:49 gvm13 kernel: [  481.296160]  [<f829f30b>] squashfs_read_data+0x30b/0x720 [squashfs]
Sep 27 12:22:49 gvm13 kernel: [  481.296166]  [<c058cecd>] ? _spin_lock+0xd/0x10
Sep 27 12:22:49 gvm13 kernel: [  481.296172]  [<f829fb2e>] ? squashfs_cache_get+0x1ee/0x2f0 [squashfs]
Sep 27 12:22:49 gvm13 kernel: [  481.296178]  [<c058cecd>] ? _spin_lock+0xd/0x10
Sep 27 12:22:49 gvm13 kernel: [  481.296183]  [<f829fb06>] squashfs_cache_get+0x1c6/0x2f0 [squashfs]
Sep 27 12:22:49 gvm13 kernel: [  481.296190]  [<f829fcef>] ? squashfs_read_metadata+0x3f/0xe0 [squashfs]
Sep 27 12:22:49 gvm13 kernel: [  481.296195]  [<f829fc63>] squashfs_get_datablock+0x33/0x40 [squashfs]
Sep 27 12:22:49 gvm13 kernel: [  481.296201]  [<f82a1190>] squashfs_readpage+0x460/0x4c0 [squashfs]
Sep 27 12:22:49 gvm13 kernel: [  481.296208]  [<c01d2ac0>] __do_page_cache_readahead+0x1e0/0x200
Sep 27 12:22:49 gvm13 kernel: [  481.296213]  [<c01d2b06>] ra_submit+0x26/0x30
Sep 27 12:22:49 gvm13 kernel: [  481.296217]  [<c01ccafc>] filemap_fault+0x3dc/0x410
Sep 27 12:22:49 gvm13 kernel: [  481.296230]  [<f8352ae0>] aufs_fault+0xd0/0x120 [aufs]
Sep 27 12:22:49 gvm13 kernel: [  481.296236]  [<c0202815>] ? mem_cgroup_update_mapped_file_stat+0x35/0x90
Sep 27 12:22:49 gvm13 kernel: [  481.296241]  [<c01e5100>] __do_fault+0x40/0x490
Sep 27 12:22:49 gvm13 kernel: [  481.296246]  [<c01e6d09>] handle_mm_fault+0x139/0x390
Sep 27 12:22:49 gvm13 kernel: [  481.296251]  [<c058f2ad>] do_page_fault+0x10d/0x3a0
Sep 27 12:22:49 gvm13 kernel: [  481.296256]  [<c058d4f0>] ? do_device_not_available+0x0/0x60
Sep 27 12:22:49 gvm13 kernel: [  481.296261]  [<c058f1a0>] ? do_page_fault+0x0/0x3a0
Sep 27 12:22:49 gvm13 kernel: [  481.296265]  [<c058d1a3>] error_code+0x73/0x80
Sep 27 12:24:49 gvm13 kernel: [  601.296034] INFO: task apt-get:1493 blocked for more than 120 seconds.
Sep 27 12:24:49 gvm13 kernel: [  601.296040] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Sep 27 12:24:49 gvm13 kernel: [  601.296046] apt-get       D 000033e1     0  1493   1485 0x00000000
Sep 27 12:24:49 gvm13 kernel: [  601.296054]  f678dc64 00000086 f69b8000 000033e1 00000000 c0849760 f69368ac c0849760
Sep 27 12:24:49 gvm13 kernel: [  601.296067]  a396e60d 0000004a c0849760 c0849760 f69368ac c0849760 c0849760 f6bff400
Sep 27 12:24:49 gvm13 kernel: [  601.296078]  00000001 0000004a f6936600 c2508760 f6936600 f678dcb0 f678dc74 c058b16a
Sep 27 12:24:49 gvm13 kernel: [  601.296089] Call Trace:
Sep 27 12:24:49 gvm13 kernel: [  601.296101]  [<c058b16a>] io_schedule+0x3a/0x60
Sep 27 12:24:49 gvm13 kernel: [  601.296109]  [<c022d2c8>] sync_buffer+0x38/0x40
Sep 27 12:24:49 gvm13 kernel: [  601.296114]  [<c058b90d>] __wait_on_bit+0x4d/0x70
Sep 27 12:24:49 gvm13 kernel: [  601.296120]  [<c022d290>] ? sync_buffer+0x0/0x40
Sep 27 12:24:49 gvm13 kernel: [  601.296125]  [<c022d290>] ? sync_buffer+0x0/0x40
Sep 27 12:24:49 gvm13 kernel: [  601.296130]  [<c058b9db>] out_of_line_wait_on_bit+0xab/0xc0
Sep 27 12:24:49 gvm13 kernel: [  601.296138]  [<c0167860>] ? wake_bit_function+0x0/0x50
Sep 27 12:24:49 gvm13 kernel: [  601.296143]  [<c022d28e>] __wait_on_buffer+0x2e/0x30
Sep 27 12:24:49 gvm13 kernel: [  601.296164]  [<f829f30b>] squashfs_read_data+0x30b/0x720 [squashfs]
Sep 27 12:24:49 gvm13 kernel: [  601.296170]  [<c058cecd>] ? _spin_lock+0xd/0x10
Sep 27 12:24:49 gvm13 kernel: [  601.296176]  [<f829fb2e>] ? squashfs_cache_get+0x1ee/0x2f0 [squashfs]
Sep 27 12:24:49 gvm13 kernel: [  601.296182]  [<c058cecd>] ? _spin_lock+0xd/0x10
Sep 27 12:24:49 gvm13 kernel: [  601.296187]  [<f829fb06>] squashfs_cache_get+0x1c6/0x2f0 [squashfs]
Sep 27 12:24:49 gvm13 kernel: [  601.296194]  [<f829fcef>] ? squashfs_read_metadata+0x3f/0xe0 [squashfs]
Sep 27 12:24:49 gvm13 kernel: [  601.296200]  [<f829fc63>] squashfs_get_datablock+0x33/0x40 [squashfs]
Sep 27 12:24:49 gvm13 kernel: [  601.296205]  [<f82a1190>] squashfs_readpage+0x460/0x4c0 [squashfs]
Sep 27 12:24:49 gvm13 kernel: [  601.296212]  [<c01d2ac0>] __do_page_cache_readahead+0x1e0/0x200
Sep 27 12:24:49 gvm13 kernel: [  601.296217]  [<c01d2b06>] ra_submit+0x26/0x30
Sep 27 12:24:49 gvm13 kernel: [  601.296221]  [<c01ccafc>] filemap_fault+0x3dc/0x410
Sep 27 12:24:49 gvm13 kernel: [  601.296235]  [<f8352ae0>] aufs_fault+0xd0/0x120 [aufs]
Sep 27 12:24:49 gvm13 kernel: [  601.296241]  [<c0202815>] ? mem_cgroup_update_mapped_file_stat+0x35/0x90
Sep 27 12:24:49 gvm13 kernel: [  601.296246]  [<c01e5100>] __do_fault+0x40/0x490
Sep 27 12:24:49 gvm13 kernel: [  601.296250]  [<c01e6d09>] handle_mm_fault+0x139/0x390
Sep 27 12:24:49 gvm13 kernel: [  601.296256]  [<c058f2ad>] do_page_fault+0x10d/0x3a0
Sep 27 12:24:49 gvm13 kernel: [  601.296260]  [<c058d4f0>] ? do_device_not_available+0x0/0x60
Sep 27 12:24:49 gvm13 kernel: [  601.296265]  [<c058f1a0>] ? do_page_fault+0x0/0x3a0
Sep 27 12:24:49 gvm13 kernel: [  601.296269]  [<c058d1a3>] error_code+0x73/0x80
Sep 27 12:26:49 gvm13 kernel: [  721.296246]  [<c058d4f0>] ? do_device_not_available+0x0/0x60
Sep 27 12:26:49 gvm13 kernel: [  721.296251]  [<c058f1a0>] ? do_page_fault+0x0/0x3a0
Sep 27 12:26:49 gvm13 kernel: [  721.296255]  [<c058d1a3>] error_code+0x73/0x80
Sep 27 12:28:47 gvm13 kernel: [  840.024022] usb 5-2: new full speed USB device using uhci_hcd and address 2
Sep 27 12:28:48 gvm13 kernel: [  840.188223] usb 5-2: configuration #1 chosen from 1 choice
Sep 27 12:28:49 gvm13 kernel: [  841.296039] INFO: task apt-get:1493 blocked for more than 120 seconds.
Sep 27 12:28:49 gvm13 kernel: [  841.296045] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Sep 27 12:28:49 gvm13 kernel: [  841.296050] apt-get       D 000033e1     0  1493   1485 0x00000000
Sep 27 12:28:49 gvm13 kernel: [  841.296059]  f678dc64 00000086 f69b8000 000033e1 00000000 c0849760 f69368ac c0849760
Sep 27 12:28:49 gvm13 kernel: [  841.296071]  a396e60d 0000004a c0849760 c0849760 f69368ac c0849760 c0849760 f6bff400
Sep 27 12:28:49 gvm13 kernel: [  841.296083]  00000001 0000004a f6936600 c2508760 f6936600 f678dcb0 f678dc74 c058b16a
Sep 27 12:28:49 gvm13 kernel: [  841.296094] Call Trace:
Sep 27 12:28:49 gvm13 kernel: [  841.296111]  [<c058b16a>] io_schedule+0x3a/0x60
Sep 27 12:28:49 gvm13 kernel: [  841.296117]  [<c022d2c8>] sync_buffer+0x38/0x40
Sep 27 12:28:49 gvm13 kernel: [  841.296122]  [<c058b90d>] __wait_on_bit+0x4d/0x70
Sep 27 12:28:49 gvm13 kernel: [  841.296126]  [<c022d290>] ? sync_buffer+0x0/0x40
Sep 27 12:28:49 gvm13 kernel: [  841.296130]  [<c022d290>] ? sync_buffer+0x0/0x40
Sep 27 12:28:49 gvm13 kernel: [  841.296135]  [<c058b9db>] out_of_line_wait_on_bit+0xab/0xc0
Sep 27 12:28:49 gvm13 kernel: [  841.296141]  [<c0167860>] ? wake_bit_function+0x0/0x50
Sep 27 12:28:49 gvm13 kernel: [  841.296145]  [<c022d28e>] __wait_on_buffer+0x2e/0x30
Sep 27 12:28:49 gvm13 kernel: [  841.296162]  [<f829f30b>] squashfs_read_data+0x30b/0x720 [squashfs]
Sep 27 12:28:49 gvm13 kernel: [  841.296169]  [<c058cecd>] ? _spin_lock+0xd/0x10
Sep 27 12:28:49 gvm13 kernel: [  841.296175]  [<f829fb2e>] ? squashfs_cache_get+0x1ee/0x2f0 [squashfs]
Sep 27 12:28:49 gvm13 kernel: [  841.296181]  [<c058cecd>] ? _spin_lock+0xd/0x10
Sep 27 12:28:49 gvm13 kernel: [  841.296189]  [<f829fb06>] squashfs_cache_get+0x1c6/0x2f0 [squashfs]
Sep 27 12:28:49 gvm13 kernel: [  841.296195]  [<f829fcef>] ? squashfs_read_metadata+0x3f/0xe0 [squashfs]
Sep 27 12:28:49 gvm13 kernel: [  841.296200]  [<f829fc63>] squashfs_get_datablock+0x33/0x40 [squashfs]
Sep 27 12:28:49 gvm13 kernel: [  841.296206]  [<f82a1190>] squashfs_readpage+0x460/0x4c0 [squashfs]
Sep 27 12:28:49 gvm13 kernel: [  841.296213]  [<c01d2ac0>] __do_page_cache_readahead+0x1e0/0x200
Sep 27 12:28:49 gvm13 kernel: [  841.296218]  [<c01d2b06>] ra_submit+0x26/0x30
Sep 27 12:28:49 gvm13 kernel: [  841.296222]  [<c01ccafc>] filemap_fault+0x3dc/0x410
Sep 27 12:28:49 gvm13 kernel: [  841.296235]  [<f8352ae0>] aufs_fault+0xd0/0x120 [aufs]
Sep 27 12:28:49 gvm13 kernel: [  841.296241]  [<c0202815>] ? mem_cgroup_update_mapped_file_stat+0x35/0x90
Sep 27 12:28:49 gvm13 kernel: [  841.296246]  [<c01e5100>] __do_fault+0x40/0x490
Sep 27 12:28:49 gvm13 kernel: [  841.296251]  [<c01e6d09>] handle_mm_fault+0x139/0x390
Sep 27 12:28:49 gvm13 kernel: [  841.296256]  [<c058f2ad>] do_page_fault+0x10d/0x3a0
Sep 27 12:28:49 gvm13 kernel: [  841.296261]  [<c058d4f0>] ? do_device_not_available+0x0/0x60
Sep 27 12:28:49 gvm13 kernel: [  841.296265]  [<c058f1a0>] ? do_page_fault+0x0/0x3a0
Sep 27 12:28:49 gvm13 kernel: [  841.296269]  [<c058d1a3>] error_code+0x73/0x80

---

### Post by andrewthomas on 2010-09-27
How do they run with a previous kernel?

---

### Post by Kyle_S on 2010-09-27
I haven't tried anything but the ubuntu 2.6.32 kernels.

Is there one you'd recommend I try?

---

### Post by andrewthomas on 2010-09-27
I meant more along the lines of 2.6.32-22

---

### Post by Kyle_S on 2010-09-27
I've used older version of 2.6.32 than 24, and they've have the same behavior.  Looking at /var/log/apt/history.log, I don't think I ever tried 22.

In that case is it worth it to try -22, or no?

---

### Post by andrewthomas on 2010-09-27
Not if the other previous versions have had the same problem.

---

### Post by andrewthomas on 2010-09-27
Read this 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/588046](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/588046)

and maybe try to test out an upstream kernel as mentioned in comment #2

---

### Post by Kyle_S on 2010-10-04
> **andrewthomas said:**
> Read this 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/588046](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/588046)

and maybe try to test out an upstream kernel as mentioned in comment #2

I had some initrd issues trying to get the latest greatest to work last week.  In the meantime a new kernel 2.6.32-25-generic came out, and the bug still exists in it.

I will try again with the latest kernel, hopefully today.

---

### Post by andrewthomas on 2010-10-04
You could also try out a maverick kernel

[http://packages.ubuntu.com/maverick/linux-image](http://packages.ubuntu.com/maverick/linux-image)

---

