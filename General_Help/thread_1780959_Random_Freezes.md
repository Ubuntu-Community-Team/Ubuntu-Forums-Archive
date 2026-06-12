---
title: "Random Freezes"
date: 2011-06-12
forum: General Help
---

### Post by RobFreak on 2011-06-12
Hi guys,

I've been running 11.04 for a while now. However, I encounter seemingly random freezes sometimes 2 hrs into the session, sometimes multiple in a row. For instance right now I had four freezes in a row.

Let me describe those freezes a little: I notice the system becoming sluggish, the fans start spinning up and then after a while I can only move my mouse. After some more time, the mouse stops working, too.

All the while the keyboard does nothing. Alt + Ctrl + Backspace does nothing. Alt + Ctrl + Fx does not change to another tty. Power button doesn't work either, I have to pull the plug and restart.

Nothing really exciting was found in syslog. Only that AptDaemon says a shutdown was requested and usually after that random tasks (networkmanager, etc.) will report to block for over 120 secs.

Please tell me what files I should specifically post and please don't ******** me about it being my hardware's fault. RAM works fine, CPU does not overheat etc. Windows runs as smooth as ever, of course.

cYa,

RobFreak

---

### Post by ivanovnegro on 2011-06-12
What graphics card do you use? That it works perfectly under Windows with the same harware does not mean it will with Ubuntu, especially with proprietary drivers.

Can you also have a look in the system monitor or type "top" without the quotes into a terminal to see what processes are running.

---

### Post by RobFreak on 2011-06-12
> **ivanovnegro said:**
> What graphics card do you use? That it works perfectly under Windows with the same harware does not mean it will with Ubuntu, especially with proprietary drivers.

I use an Nvidia 8800M GTS. It worked fine in Ubuntu 10.10 with proprietary drivers. I somehow don't think this is a likely cause at all.

> **ivanovnegro said:**
> Can you also have a look in the system monitor or type "top" without the quotes into a terminal to see what processes are running.

And what would that accomplish? As soon as the freeze begins, no window in the background nor foreground updates anymore, so I wouldn't see what it says anyway. Or am I misunderstanding something here?

cYa,

RobFreak

---

### Post by ivanovnegro on 2011-06-12
> **RobFreak said:**
> I use an Nvidia 8800M GTS. It worked fine in Ubuntu 10.10 with proprietary drivers. I somehow don't think this is a likely cause at all.



And what would that accomplish? As soon as the freeze begins, no window in the background nor foreground updates anymore, so I wouldn't see what it says anyway. Or am I misunderstanding something here?

cYa,

RobFreak

Did you try to install the additional drivers from system, additional hardware?
Unity is another animal as your old Maverick system.

It would maybe tell us what process is consuming the resources. But if your CPU is working fine, it could be really the graphics card.

---

### Post by RobFreak on 2011-06-12
> **ivanovnegro said:**
> Did you try to install the additional drivers from system, additional hardware?

I have those installed already!

> **ivanovnegro said:**
> Unity is another animal as your old Maverick system.

My system is not old! I can play Bioshock in full resolution with all details set to high. That counts for something, so why would that stupid Unity with its worthlessly cheap 3d effects be causing any trouble for my system? Seriously, is it programmed that shoddy?

It would be helpful to know what changed with 11.04. in regards to handling the gfx card, because 10.10 worked pretty good.
I also don't believe this is a Unity problem per sé, although unity sucks at the moment. The freezes don't seem to be particularly tied to 3d effects. Opening a tab in firefox lets it freeze, getting the desktop overview will, opening gedit will... The list goes on...

I somewhere read about ACPI trouble, but some changelogs for that are nowhere to be found either... However, all other "solutions" were to update the bios to the latest version and silently blame it on non-standard bios implementations. However, ACPI and Ubuntu alongside my current bios worked fine in 10.10. Maybe some dev changed something around to **** with people?

This needs serious fixing, because while I generally think Ubuntu was barely usable before -- now it has become perfectly unusable! I'll post relevant snippets of my syslog later... Maybe somebody sees something wrong in them.
Isn't there another method to produce a detialed logfile on the disk, wait for a freeze and then post that logfile? All the stuff I keep reading is shitting me with ssh, which I cannot do.

cYa,

RobFreak

---

### Post by RobFreak on 2011-06-12
Here are the syslog entries.

Freeze at 22:22 restart at 22:40 (I was busy and did not notice it freezing).

```
Jun 12 21:09:40 lappy AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/58aa193e1d7d4650beb9ce16cee086c3
Jun 12 21:09:41 lappy AptDaemon.Worker: INFO: Committing packages: dbus.Array([dbus.String(u'glade')], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s'))
Jun 12 21:10:24 lappy AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/58aa193e1d7d4650beb9ce16cee086c3
Jun 12 21:16:09 lappy AptDaemon: INFO: Quitting due to inactivity
Jun 12 21:16:09 lappy AptDaemon: INFO: Shutdown was requested
Jun 12 21:16:09 lappy AptDaemon: INFO: Initializing daemon
Jun 12 21:17:01 lappy CRON[6320]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 12 21:21:10 lappy AptDaemon: INFO: Quitting due to inactivity
Jun 12 21:21:10 lappy AptDaemon: INFO: Shutdown was requested
Jun 12 22:17:01 lappy CRON[6458]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 12 22:20:19 lappy kernel: [ 7080.356085] INFO: task jbd2/sda8-8:289 blocked for more than 120 seconds.
Jun 12 22:20:19 lappy kernel: [ 7080.356088] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jun 12 22:20:19 lappy kernel: [ 7080.356091] jbd2/sda8-8     D edfe9d00     0   289      2 0x00000000
Jun 12 22:20:19 lappy kernel: [ 7080.356095]  f2edfe60 00000046 00000000 edfe9d00 00000000 00000000 f2ffe78c c183a8c0
Jun 12 22:20:19 lappy kernel: [ 7080.356100]  e74c3283 00000644 f2ffe788 c183a8c0 c183a8c0 f48068c0 f2ffe500 c1731f60
Jun 12 22:20:19 lappy kernel: [ 7080.356105]  f2edfe1c 00000282 f2ffe500 f2edfe50 c10b6786 f2fd4698 f2edfe58 c1078088
Jun 12 22:20:19 lappy kernel: [ 7080.356110] Call Trace:
Jun 12 22:20:19 lappy kernel: [ 7080.356118]  [<c10b6786>] ? delayacct_end+0x96/0xb0
Jun 12 22:20:19 lappy kernel: [ 7080.356123]  [<c1078088>] ? ktime_get_ts+0xf8/0x120
Jun 12 22:20:19 lappy kernel: [ 7080.356127]  [<c1507a4f>] io_schedule+0x5f/0xa0
Jun 12 22:20:19 lappy kernel: [ 7080.356131]  [<c114e2f8>] sync_buffer+0x38/0x40
Jun 12 22:20:19 lappy kernel: [ 7080.356134]  [<c150824d>] __wait_on_bit+0x4d/0x70
Jun 12 22:20:19 lappy kernel: [ 7080.356136]  [<c114e2c0>] ? sync_buffer+0x0/0x40
Jun 12 22:20:19 lappy kernel: [ 7080.356139]  [<c114e2c0>] ? sync_buffer+0x0/0x40
Jun 12 22:20:19 lappy kernel: [ 7080.356142]  [<c15082d1>] out_of_line_wait_on_bit+0x61/0x70
Jun 12 22:20:19 lappy kernel: [ 7080.356146]  [<c106d3c0>] ? wake_bit_function+0x0/0x60
Jun 12 22:20:19 lappy kernel: [ 7080.356148]  [<c114e2be>] __wait_on_buffer+0x2e/0x30
Jun 12 22:20:19 lappy kernel: [ 7080.356152]  [<c11ebcf2>] jbd2_journal_commit_transaction+0xe52/0xf30
Jun 12 22:20:19 lappy kernel: [ 7080.356157]  [<c102d8c8>] ? default_spin_lock_flags+0x8/0x10
Jun 12 22:20:19 lappy kernel: [ 7080.356160]  [<c105dc07>] ? try_to_del_timer_sync+0x67/0xb0
Jun 12 22:20:19 lappy kernel: [ 7080.356164]  [<c11ef8fe>] kjournald2+0x8e/0x1c0
Jun 12 22:20:19 lappy kernel: [ 7080.356166]  [<c106d370>] ? autoremove_wake_function+0x0/0x50
Jun 12 22:20:19 lappy kernel: [ 7080.356169]  [<c11ef870>] ? kjournald2+0x0/0x1c0
Jun 12 22:20:19 lappy kernel: [ 7080.356172]  [<c106ce04>] kthread+0x74/0x80
Jun 12 22:20:19 lappy kernel: [ 7080.356174]  [<c106cd90>] ? kthread+0x0/0x80
Jun 12 22:20:19 lappy kernel: [ 7080.356177]  [<c100367e>] kernel_thread_helper+0x6/0x10
Jun 12 22:20:19 lappy kernel: [ 7080.356181] INFO: task NetworkManager:834 blocked for more than 120 seconds.
Jun 12 22:20:19 lappy kernel: [ 7080.356183] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jun 12 22:20:19 lappy kernel: [ 7080.356185] NetworkManager  D f6b9a9d8     0   834      1 0x00000000
Jun 12 22:20:19 lappy kernel: [ 7080.356188]  eff45e6c 00000086 c11e9589 f6b9a9d8 e39e8300 f2d7f400 eff4a86c c183a8c0
Jun 12 22:20:19 lappy kernel: [ 7080.356193]  9bbc0d9f 0000064c eff4a868 c183a8c0 c183a8c0 f48068c0 eff4a5e0 ed495860
Jun 12 22:20:19 lappy kernel: [ 7080.356198]  c11c7aa3 00000000 f6b9a9d8 00000000 00000c13 eff06198 eff45e64 c1078088
Jun 12 22:20:19 lappy kernel: [ 7080.356203] Call Trace:
Jun 12 22:20:19 lappy kernel: [ 7080.356206]  [<c11e9589>] ? jbd2_journal_stop+0x1d9/0x2b0
Jun 12 22:20:19 lappy kernel: [ 7080.356210]  [<c11c7aa3>] ? ext4_journal_start_sb+0x93/0x110
Jun 12 22:20:19 lappy kernel: [ 7080.356213]  [<c1078088>] ? ktime_get_ts+0xf8/0x120
Jun 12 22:20:19 lappy kernel: [ 7080.356216]  [<c1507a4f>] io_schedule+0x5f/0xa0
Jun 12 22:20:19 lappy kernel: [ 7080.356219]  [<c10e1d3a>] sync_page+0x3a/0x50
Jun 12 22:20:19 lappy kernel: [ 7080.356221]  [<c150824d>] __wait_on_bit+0x4d/0x70
Jun 12 22:20:19 lappy kernel: [ 7080.356224]  [<c10e1d00>] ? sync_page+0x0/0x50
Jun 12 22:20:19 lappy kernel: [ 7080.356226]  [<c10e1ee5>] wait_on_page_bit+0x85/0x90
Jun 12 22:20:19 lappy kernel: [ 7080.356229]  [<c106d3c0>] ? wake_bit_function+0x0/0x60
Jun 12 22:20:19 lappy kernel: [ 7080.356231]  [<c10e1fcb>] filemap_fdatawait_range+0xdb/0x160
Jun 12 22:20:19 lappy kernel: [ 7080.356235]  [<c10eaedc>] ? do_writepages+0x1c/0x40
Jun 12 22:20:19 lappy kernel: [ 7080.356238]  [<c10e341e>] ? __filemap_fdatawrite_range+0x5e/0x70
Jun 12 22:20:19 lappy kernel: [ 7080.356240]  [<c10e34a9>] filemap_write_and_wait_range+0x79/0x90
Jun 12 22:20:19 lappy kernel: [ 7080.356244]  [<c114c42c>] vfs_fsync_range+0x5c/0xa0
Jun 12 22:20:19 lappy kernel: [ 7080.356246]  [<c114c527>] vfs_fsync+0x27/0x30
Jun 12 22:20:19 lappy kernel: [ 7080.356249]  [<c114c55f>] do_fsync+0x2f/0x50
Jun 12 22:20:19 lappy kernel: [ 7080.356251]  [<c114c782>] sys_fsync+0x12/0x20
Jun 12 22:20:19 lappy kernel: [ 7080.356254]  [<c1509bf4>] syscall_call+0x7/0xb
Jun 12 22:22:19 lappy kernel: [ 7200.356081] INFO: task jbd2/sda8-8:289 blocked for more than 120 seconds.
Jun 12 22:22:19 lappy kernel: [ 7200.356085] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jun 12 22:22:19 lappy kernel: [ 7200.356087] jbd2/sda8-8     D edfe9d00     0   289      2 0x00000000
Jun 12 22:22:19 lappy kernel: [ 7200.356091]  f2edfe60 00000046 00000000 edfe9d00 00000000 00000000 f2ffe78c c183a8c0
Jun 12 22:22:19 lappy kernel: [ 7200.356096]  e74c3283 00000644 f2ffe788 c183a8c0 c183a8c0 f48068c0 f2ffe500 c1731f60
Jun 12 22:22:19 lappy kernel: [ 7200.356101]  f2edfe1c 00000282 f2ffe500 f2edfe50 c10b6786 f2fd4698 f2edfe58 c1078088
Jun 12 22:22:19 lappy kernel: [ 7200.356107] Call Trace:
Jun 12 22:22:19 lappy kernel: [ 7200.356114]  [<c10b6786>] ? delayacct_end+0x96/0xb0
Jun 12 22:22:19 lappy kernel: [ 7200.356119]  [<c1078088>] ? ktime_get_ts+0xf8/0x120
Jun 12 22:22:19 lappy kernel: [ 7200.356124]  [<c1507a4f>] io_schedule+0x5f/0xa0
Jun 12 22:22:19 lappy kernel: [ 7200.356128]  [<c114e2f8>] sync_buffer+0x38/0x40
Jun 12 22:22:19 lappy kernel: [ 7200.356130]  [<c150824d>] __wait_on_bit+0x4d/0x70
Jun 12 22:22:19 lappy kernel: [ 7200.356133]  [<c114e2c0>] ? sync_buffer+0x0/0x40
Jun 12 22:22:19 lappy kernel: [ 7200.356136]  [<c114e2c0>] ? sync_buffer+0x0/0x40
Jun 12 22:22:19 lappy kernel: [ 7200.356139]  [<c15082d1>] out_of_line_wait_on_bit+0x61/0x70
Jun 12 22:22:19 lappy kernel: [ 7200.356142]  [<c106d3c0>] ? wake_bit_function+0x0/0x60
Jun 12 22:22:19 lappy kernel: [ 7200.356145]  [<c114e2be>] __wait_on_buffer+0x2e/0x30
Jun 12 22:22:19 lappy kernel: [ 7200.356149]  [<c11ebcf2>] jbd2_journal_commit_transaction+0xe52/0xf30
Jun 12 22:22:19 lappy kernel: [ 7200.356153]  [<c102d8c8>] ? default_spin_lock_flags+0x8/0x10
Jun 12 22:22:19 lappy kernel: [ 7200.356156]  [<c105dc07>] ? try_to_del_timer_sync+0x67/0xb0
Jun 12 22:22:19 lappy kernel: [ 7200.356160]  [<c11ef8fe>] kjournald2+0x8e/0x1c0
Jun 12 22:22:19 lappy kernel: [ 7200.356163]  [<c106d370>] ? autoremove_wake_function+0x0/0x50
Jun 12 22:22:19 lappy kernel: [ 7200.356165]  [<c11ef870>] ? kjournald2+0x0/0x1c0
Jun 12 22:22:19 lappy kernel: [ 7200.356168]  [<c106ce04>] kthread+0x74/0x80
Jun 12 22:22:19 lappy kernel: [ 7200.356171]  [<c106cd90>] ? kthread+0x0/0x80
Jun 12 22:22:19 lappy kernel: [ 7200.356174]  [<c100367e>] kernel_thread_helper+0x6/0x10
Jun 12 22:22:19 lappy kernel: [ 7200.356178] INFO: task NetworkManager:834 blocked for more than 120 seconds.
Jun 12 22:22:19 lappy kernel: [ 7200.356179] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jun 12 22:22:19 lappy kernel: [ 7200.356181] NetworkManager  D f6b9a9d8     0   834      1 0x00000000
Jun 12 22:22:19 lappy kernel: [ 7200.356185]  eff45e6c 00000086 c11e9589 f6b9a9d8 e39e8300 f2d7f400 eff4a86c c183a8c0
Jun 12 22:22:19 lappy kernel: [ 7200.356190]  9bbc0d9f 0000064c eff4a868 c183a8c0 c183a8c0 f48068c0 eff4a5e0 ed495860
Jun 12 22:22:19 lappy kernel: [ 7200.356195]  c11c7aa3 00000000 f6b9a9d8 00000000 00000c13 eff06198 eff45e64 c1078088
Jun 12 22:22:19 lappy kernel: [ 7200.356200] Call Trace:
Jun 12 22:22:19 lappy kernel: [ 7200.356202]  [<c11e9589>] ? jbd2_journal_stop+0x1d9/0x2b0
Jun 12 22:22:19 lappy kernel: [ 7200.356207]  [<c11c7aa3>] ? ext4_journal_start_sb+0x93/0x110
Jun 12 22:22:19 lappy kernel: [ 7200.356210]  [<c1078088>] ? ktime_get_ts+0xf8/0x120
Jun 12 22:22:19 lappy kernel: [ 7200.356213]  [<c1507a4f>] io_schedule+0x5f/0xa0
Jun 12 22:22:19 lappy kernel: [ 7200.356216]  [<c10e1d3a>] sync_page+0x3a/0x50
Jun 12 22:22:19 lappy kernel: [ 7200.356218]  [<c150824d>] __wait_on_bit+0x4d/0x70
Jun 12 22:22:19 lappy kernel: [ 7200.356220]  [<c10e1d00>] ? sync_page+0x0/0x50
Jun 12 22:22:19 lappy kernel: [ 7200.356223]  [<c10e1ee5>] wait_on_page_bit+0x85/0x90
Jun 12 22:22:19 lappy kernel: [ 7200.356226]  [<c106d3c0>] ? wake_bit_function+0x0/0x60
Jun 12 22:22:19 lappy kernel: [ 7200.356228]  [<c10e1fcb>] filemap_fdatawait_range+0xdb/0x160
Jun 12 22:22:19 lappy kernel: [ 7200.356232]  [<c10eaedc>] ? do_writepages+0x1c/0x40
Jun 12 22:22:19 lappy kernel: [ 7200.356234]  [<c10e341e>] ? __filemap_fdatawrite_range+0x5e/0x70
Jun 12 22:22:19 lappy kernel: [ 7200.356237]  [<c10e34a9>] filemap_write_and_wait_range+0x79/0x90
Jun 12 22:22:19 lappy kernel: [ 7200.356240]  [<c114c42c>] vfs_fsync_range+0x5c/0xa0
Jun 12 22:22:19 lappy kernel: [ 7200.356243]  [<c114c527>] vfs_fsync+0x27/0x30
Jun 12 22:22:19 lappy kernel: [ 7200.356245]  [<c114c55f>] do_fsync+0x2f/0x50
Jun 12 22:22:19 lappy kernel: [ 7200.356248]  [<c114c782>] sys_fsync+0x12/0x20
Jun 12 22:22:19 lappy kernel: [ 7200.356251]  [<c1509bf4>] syscall_call+0x7/0xb
Jun 12 22:40:48 lappy kernel: imklog 4.6.4, log source = /proc/kmsg started.
Jun 12 22:40:48 lappy rsyslogd: [origin software="rsyslogd" swVersion="4.6.4" x-pid="840" x-info="http://www.rsyslog.com"] (re)start
Jun 12 22:40:48 lappy rsyslogd: rsyslogd's groupid changed to 103
Jun 12 22:40:48 lappy rsyslogd: rsyslogd's userid changed to 101
Jun 12 22:40:48 lappy rsyslogd-2039: Could no open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Jun 12 22:40:48 lappy kernel: [    0.000000] Initializing cgroup subsys cpuset
Jun 12 22:40:48 lappy kernel: [    0.000000] Initializing cgroup subsys cpu
Jun 12 22:40:48 lappy kernel: [    0.000000] Linux version 2.6.38-8-generic (buildd@vernadsky) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 (Ubuntu 2.6.38-8.42-generic 2.6.38.2)
```

Freeze at 23:01, restart at 23:03.
```
Jun 12 22:41:08 lappy kernel: [   47.363182] EXT4-fs (sda8): re-mounted. Opts: errors=remount-ro,commit=0
Jun 12 22:41:08 lappy kernel: [   47.589340] EXT4-fs (sda7): re-mounted. Opts: commit=0
Jun 12 22:41:09 lappy gdm-simple-greeter[1349]: WARNING: Unable to load CK history: no seat-id found
Jun 12 22:41:10 lappy gdm-session-worker[1351]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Jun 12 22:41:14 lappy gdm-session-worker[1476]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Jun 12 22:41:14 lappy gdm-session-worker[1476]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Jun 12 22:41:17 lappy gdm-session-worker[1476]: pam_sm_authenticate: Called
Jun 12 22:41:17 lappy gdm-session-worker[1476]: pam_sm_authenticate: username = [robert]
Jun 12 22:41:22 lappy rtkit-daemon[1370]: Successfully made thread 1576 of process 1576 (n/a) owned by '1000' high priority at nice level -11.
Jun 12 22:41:22 lappy rtkit-daemon[1370]: Supervising 4 threads of 2 processes of 2 users.
Jun 12 22:41:22 lappy rtkit-daemon[1370]: Successfully made thread 1579 of process 1576 (n/a) owned by '1000' RT at priority 5.
Jun 12 22:41:22 lappy rtkit-daemon[1370]: Supervising 5 threads of 2 processes of 2 users.
Jun 12 22:41:22 lappy rtkit-daemon[1370]: Successfully made thread 1580 of process 1576 (n/a) owned by '1000' RT at priority 5.
Jun 12 22:41:22 lappy rtkit-daemon[1370]: Supervising 6 threads of 2 processes of 2 users.
Jun 12 22:41:40 lappy kernel: [   79.279865] ISO 9660 Extensions: Microsoft Joliet Level 3
Jun 12 22:41:40 lappy kernel: [   79.309236] ISOFS: changing to secondary root
Jun 12 22:41:54 lappy kernel: [   92.892122] CE: hpet increased min_delta_ns to 20113 nsec
Jun 12 22:55:25 lappy AptDaemon: INFO: Initializing daemon
Jun 12 23:00:25 lappy AptDaemon: INFO: Quitting due to inactivity
Jun 12 23:00:25 lappy AptDaemon: INFO: Shutdown was requested
Jun 12 23:01:14 lappy kernel: [ 1252.801600] NVRM: os_pci_init_handle: invalid context!
Jun 12 23:01:14 lappy kernel: [ 1252.801604] NVRM: os_pci_init_handle: invalid context!
Jun 12 23:01:14 lappy kernel: [ 1252.801649] NVRM: os_pci_init_handle: invalid context!
Jun 12 23:01:14 lappy kernel: [ 1252.801651] NVRM: os_pci_init_handle: invalid context!
Jun 12 23:01:14 lappy kernel: [ 1252.801729] NVRM: os_pci_init_handle: invalid context!
Jun 12 23:01:14 lappy kernel: [ 1252.801731] NVRM: os_pci_init_handle: invalid context!
Jun 12 23:01:14 lappy kernel: [ 1252.801765] NVRM: os_pci_init_handle: invalid context!
Jun 12 23:01:14 lappy kernel: [ 1252.801767] NVRM: os_pci_init_handle: invalid context!
Jun 12 23:01:14 lappy kernel: [ 1252.801844] NVRM: os_pci_init_handle: invalid context!
Jun 12 23:01:14 lappy kernel: [ 1252.801846] NVRM: os_pci_init_handle: invalid context!
Jun 12 23:01:14 lappy kernel: [ 1252.801885] NVRM: os_pci_init_handle: invalid context!
Jun 12 23:01:14 lappy kernel: [ 1252.801886] NVRM: os_pci_init_handle: invalid context!
Jun 12 23:01:14 lappy kernel: [ 1252.801965] NVRM: os_pci_init_handle: invalid context!
Jun 12 23:01:14 lappy kernel: [ 1252.801966] NVRM: os_pci_init_handle: invalid context!
Jun 12 23:01:14 lappy kernel: [ 1252.802005] NVRM: os_pci_init_handle: invalid context!
Jun 12 23:01:14 lappy kernel: [ 1252.802006] NVRM: os_pci_init_handle: invalid context!
Jun 12 23:01:14 lappy kernel: [ 1252.802084] NVRM: os_pci_init_handle: invalid context!
Jun 12 23:01:14 lappy kernel: [ 1252.802085] NVRM: os_pci_init_handle: invalid context!
Jun 12 23:01:14 lappy kernel: [ 1252.802123] NVRM: os_pci_init_handle: invalid context!
Jun 12 23:01:14 lappy kernel: [ 1252.802125] NVRM: os_pci_init_handle: invalid context!
Jun 12 23:01:14 lappy kernel: [ 1252.802205] NVRM: os_pci_init_handle: invalid context!
Jun 12 23:01:14 lappy kernel: [ 1252.802207] NVRM: os_pci_init_handle: invalid context!
Jun 12 23:01:14 lappy kernel: [ 1252.802245] NVRM: os_pci_init_handle: invalid context!
Jun 12 23:01:14 lappy kernel: [ 1252.802247] NVRM: os_pci_init_handle: invalid context!
Jun 12 23:01:14 lappy kernel: [ 1252.802324] NVRM: os_pci_init_handle: invalid context!
Jun 12 23:01:14 lappy kernel: [ 1252.802326] NVRM: os_pci_init_handle: invalid context!
Jun 12 23:01:14 lappy kernel: [ 1252.802364] NVRM: os_pci_init_handle: invalid context!
Jun 12 23:01:14 lappy kernel: [ 1252.802366] NVRM: os_pci_init_handle: invalid context!
Jun 12 23:01:14 lappy kernel: [ 1252.802444] NVRM: os_pci_init_handle: invalid context!
Jun 12Jun 12 23:03:08 lappy kernel: imklog 4.6.4, log source = /proc/kmsg started.
Jun 12 23:03:08 lappy rsyslogd: [origin software="rsyslogd" swVersion="4.6.4" x-pid="811" x-info="http://www.rsyslog.com"] (re)start
Jun 12 23:03:08 lappy rsyslogd: rsyslogd's groupid changed to 103
Jun 12 23:03:08 lappy rsyslogd: rsyslogd's userid changed to 101
Jun 12 23:03:08 lappy rsyslogd-2039: Could no open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Jun 12 23:03:08 lappy kernel: [    0.000000] Initializing cgroup subsys cpuset
Jun 12 23:03:08 lappy kernel: [    0.000000] Initializing cgroup subsys cpu
Jun 12 23:03:08 lappy kernel: [    0.000000] Linux version 2.6.38-8-generic (buildd@vernadsky) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 (Ubuntu 2.6.38-8.42-generic 2.6.38.2)
```

Freeze not even 10 mins later.

```
Jun 12 23:03:20 lappy kernel: [   42.830040] ISO 9660 Extensions: Microsoft Joliet Level 3
Jun 12 23:03:20 lappy kernel: [   42.833898] ISOFS: changing to secondary root
Jun 12 23:03:20 lappy kernel: [   43.472014] eth0: no IPv6 routers present
Jun 12 23:03:22 lappy ntpdate[1423]: step time server 91.189.94.4 offset -0.702298 sec
Jun 12 23:13:11 lappy kernel: [  634.537177] NVRM: os_pci_init_handle: invalid context!
Jun 12 23:13:11 lappy kernel: [  634.537180] NVRM: os_pci_init_handle: invalid context!
Jun 12 23:13:11 lappy kernel: [  634.537243] NVRM: os_pci_init_handle: invalid context!
Jun 12 23:13:11 lappy kernel: [  634.537245] NVRM: os_pci_init_handle: invalid context!
Jun 12 23:13:11 lappy kernel: [  634.537390] NVRM: os_pci_init_handle: invalid context!
Jun 12 23:13:11 lappy kernel: [  634.537391] NVRM: os_pci_init_handle: invalid context!
Jun 12 23:13:11 lappy kernel: [  634.537455] NVRM: os_pci_init_handle: invalid context!
Jun 12 23:13:11 lappy kernel: [  634.537457] NVRM: os_pci_init_handle: invalid context!
Jun 12 23:13:11 lappy kernel: [  634.537604] NVRM: os_pci_init_handle: invalid context!
Jun 12 23:13:11 lappy kernel: [  634.537605] NVRM: os_pci_init_handle: invalid context!
Jun 12 23:13:11 lappy kernel: [  634.537670] NVRM: os_pci_init_handle: invalid context!
Jun 12 23:13:11 lappy kernel: [  634.537671] NVRM: os_pci_init_handle: invalid context!
Jun 12 23:13:11 lappy kernel: [  634.537817] NVRM: os_pci_init_handle: invalid context!
Jun 12 23:13:11 lappy kernel: [  634Jun 12 23:15:03 lappy kernel: imklog 4.6.4, log source = /proc/kmsg started.
Jun 12 23:15:03 lappy rsyslogd: [origin software="rsyslogd" swVersion="4.6.4" x-pid="809" x-info="http://www.rsyslog.com"] (re)start
Jun 12 23:15:03 lappy rsyslogd: rsyslogd's groupid changed to 103
Jun 12 23:15:03 lappy rsyslogd: rsyslogd's userid changed to 101
Jun 12 23:15:03 lappy rsyslogd-2039: Could no open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Jun 12 23:15:03 lappy kernel: [    0.000000] Initializing cgroup subsys cpuset
Jun 12 23:15:03 lappy kernel: [    0.000000] Initializing cgroup subsys cpu
Jun 12 23:15:03 lappy kernel: [    0.000000] Linux version 2.6.38-8-generic (buildd@vernadsky) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 (Ubuntu 2.6.38-8.42-generic 2.6.38.2)
```

Thanks,

RobFreak

---

### Post by ivanovnegro on 2011-06-12
I am not the great expert to read everything from the sys logs, others sure, but I can see that there are some problems and warnings. Did you do a fresh install or just an upgrade?

Also, I am sorry for your experience, I for one dont use Unity and I cannot stand it but really there is no reason to whine here. Before upgrading to a newer system, read the release notes and problems and see if your hardware is compatible, try the Live CD whatever. And why upgrading for the sake of upgrading?
In my opinion you should just stay on Maverick, 11.04 is cutting edge and is known for a bunch of problems for many people on many hardware out there, even though it can run perfectly and in my case it ran perfectly in the sense of how it was designed.

---

### Post by RobFreak on 2011-06-12
> **ivanovnegro said:**
> I am not the great expert to read everything from the sys logs, others sure, but I can see that there are some problems and warnings. Did you do a fresh install or just an upgrade?

I upgraded from 10.10, partly because I had hoped for newer software packages.

> **ivanovnegro said:**
> [T]here is no reason to whine here. Before upgrading to a newer system, read the release notes and problems and see if your hardware is compatible, try the Live CD whatever.

I'm always bewildered how bad quality software is always the user's fault. I already had to blacklist a rampaging kernel module on my own that would disallow my wireless LAN card to be activated via hardware switch. Now I face this freezing disaster. And now it's my fault that the Ubuntu guys apparently cannot manage QC?

> **ivanovnegro said:**
> [I]t ran perfectly in the sense of how it was designed.

Maybe it was designed to be shitty for so many users? Just like Unity's behavior cannot be configured one single bit?

I can see there's something wrong in there, but I cannot pinpoint it. There must be somebody around who knows enough about this stuff to narrow it further. I don't think three different applications just stop reacting for 120 seconds because they all fail. I think there's something else going on and I quite frankly don't have clue how to find out what is making these programs crash in the first place and if that is actually causing the freezes or not...

cYa,

RobFreak

---

### Post by ivanovnegro on 2011-06-12
I never said its your fault, but some research before the upgrade would not be bad to save you these problems.
And, I mentioned it, I dont use Unity and I dont like Unity or the new Ubuntu 11.04, I am not a fan of it and not a fanboy either. In reality I dislike 11.04 totally and find it buggy and unstable and for me even unusable with my workflow.

Try the Ubuntu Classic mode after logging out. When you see the login prompt click first on your user name and then go to the bottom and login with Ubuntu Classic to see if you will have the same issues.

And I would also consider you, if you really want to be a tester of beta software, what 11.04 for me is, then install it fresh from scratch.

Ubuntu will improve I think, but this release was the worst I saw, its not the users fault but you as a user have to know before what you could estimate with this release by following the Ubuntu development cycle, news, comments, the web etc. This is sadly the downside of using the newest of the newest.

If you really want newer apps, you can have them also under an older Ubuntu release, PPAs etc.

---

### Post by mörgæs on 2011-06-12
A fresh intstall of Xubuntu 11.04 is another option worth trying.

---

### Post by RobFreak on 2011-06-13
So now I'm supposed to leave all my configurations, all my programs behind and move on to Xubuntu? How is that a solution at all?

cYa,

RobFreak

---

### Post by ivanovnegro on 2011-06-13
> **RobFreak said:**
> So now I'm supposed to leave all my configurations, all my programs behind and move on to Xubuntu? How is that a solution at all?

cYa,

RobFreak

Did you try Gnome Classic? Just to see if without Unity running you dont come into issues.
We try to help you here!

Maybe someone knows what is going on on your machine, but we apparently dont.

As I said, you have the choice to use another thing if 11.04 does not make it on your machine, what is so difficult about it? In reality many folks went back to 10.10 or 10.04 because there was no chance to run 11.04 on their machines. Of course this does not mean that there is not maybe a solution for your problem.

As mentioned Xubuntu, it is a great alternative.

---

### Post by stephenbbb on 2011-12-01
I have the same problem on 11.10 and it is caused by the unable to open pipe /dev/xconsole (message by rsyslogd)
unfortunately I get that immediately and the desktop is unusable.

this seems to be a real bug. is it time to swicth to another OS??

---

