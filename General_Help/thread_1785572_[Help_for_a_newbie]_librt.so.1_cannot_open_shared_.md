---
title: "[Help for a newbie] librt.so.1 cannot open shared object file error"
date: 2011-06-18
forum: General Help
---

### Post by nunoazevedo on 2011-06-18
Hi

I turn on my computer today and i got this error booting Ubuntu:

> /sbin/init: error while loading shared libraries: librt.so.1: cannot open shared object file: Input/Output error
Kernel panic - not syncing: Attempted to kill init!
Pid 1: 1, comm :init Not tainted 2.6.35-28-generic #50-Ubuntu
Call trace:
[<c05c8283>] ? printk+0x2d/0x32
[<c05c81dc>] panic+0x5a/0xd4
[<c014dba4>] forget_original_parent+0x2e4/0x2f0
[<c01acbed>] ? call_rcu+0xd/0x10
[<c014dbc3>]exit_notify+0x13/0x170
[<c014f4ac>]do_exit+0x17c/0x340
[<c0219de5>] ?vfs_writev+0x45/0x60
[<c014f6ae>] do_group_exit+0x3e/0xa0
[<c014f728>] sys_exit_group+0x18/0x20
[<c05caeb4>] syscall_call+0x7/0xbIs there anything i can do to copy another librt.so.1 or do i haveto re-install Ubuntu (and lost all programs installed!!:mad:)

Thanks

---

