---
title: "Locks and Freezes"
date: 2011-01-12
forum: General Help
---

### Post by kaspar_silas on 2011-01-12
Really not having a good ubuntu day :(. My desktop had it's problems and now I finished work and discovered my sodding laptop is sick too.

Naturally the problem is also a bit of a mystery. Basically suddenly everything is locking up or taking an incredibly long time (evolution took 5mins to load up). This is odd as it worked fine last night as nothing new was installed or updated.

Strangely if I watch "top" nothing is reported as using up memory or cpu when it locks. If I have another log in active at lock up this normally half works. Half in that it's runs fine provided the command input is very simple:

$ Echo "blah blah" 

is okay:

$ dmesg

will normally lock or cause a 5 min delay.
If I look at dmesg however I get alarming stuff like this:

```

[  600.272096] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[  600.272103] ubuntuone-syn D 00000000     0  1856      1 0x00000000
[  600.272113]  f132fcdc 00000086 f6e70000 00000000 f1196000 f132fcdc c08c4700 c08c4700
[  600.272129]  b4a7c9e2 0000006e c08c4700 c08c4700 00000000 0000006e f15efe00 c08c4700
[  600.272143]  c08c4700 f1728000 00000000 c23db684 f6172800 ef85e3c0 f132fd38 c02d2aa5
[  600.272157] Call Trace:
[  600.272175]  [<c02d2aa5>] do_get_write_access+0x215/0x3f0
[  600.272187]  [<c0165f10>] ? wake_bit_function+0x0/0x50
[  600.272195]  [<c02d2da8>] jbd2_journal_get_write_access+0x28/0x40
[  600.272205]  [<c02bc1ce>] __ext4_journal_get_write_access+0x2e/0x60
[  600.272216]  [<c029c87f>] ext4_reserve_inode_write+0x5f/0x80
[  600.272225]  [<c029c8d8>] ext4_mark_inode_dirty+0x38/0x1a0
[  600.272235]  [<c02afe80>] ? ext4_journal_start_sb+0xc0/0xf0
[  600.272244]  [<c029cb64>] ext4_dirty_inode+0x34/0x50
[  600.272253]  [<c0237441>] __mark_inode_dirty+0x31/0x190
[  600.272262]  [<c01d96e4>] ? file_remove_suid+0x24/0x80
[  600.272271]  [<c022cad5>] file_update_time+0xb5/0x130
[  600.272280]  [<c01dbb98>] __generic_file_aio_write+0x1b8/0x500
[  600.272290]  [<c02229ae>] ? path_to_nameidata+0x1e/0x50
[  600.272298]  [<c0224132>] ? link_path_walk+0x412/0x890
[  600.272308]  [<c0230bef>] ? mntput_no_expire+0x1f/0xd0
[  600.272316]  [<c01dbf37>] generic_file_aio_write+0x57/0xc0
[  600.272325]  [<c0296b81>] ext4_file_write+0x41/0xd0
[  600.272335]  [<c02188c4>] do_sync_write+0xa4/0xe0
[  600.272343]  [<c021c933>] ? cp_new_stat64+0xe3/0x100
[  600.272354]  [<c032ec46>] ? apparmor_file_permission+0x16/0x20
[  600.272365]  [<c03030b4>] ? security_file_permission+0x14/0x20
[  600.272373]  [<c0218a42>] ? rw_verify_area+0x62/0xd0
[  600.272382]  [<c0218b52>] vfs_write+0xa2/0x190
...
THE NEXT LINE REPEATS AFTER EVERY FREEZE EVENT
[ 2494.120050] usb 1-5: reset high speed USB device using ehci_hcd and address 2


```

All of which isn't exactly clear to me. The only thing I can thing of, solely as I see "ext4" in my computers stream of conscience, is that it is real disk errors as both my home drive and /usr are SD drives mounted on boot up (I do this as my laptop is an ASUS and thus only has 4Gb ).

So to say the least this is clutching at straws. Has anyone ever encountered anything similar or does anyone have any suggestions. Any help at all is appreciated, especially today.

---

