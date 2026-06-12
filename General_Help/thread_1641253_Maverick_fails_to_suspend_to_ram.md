---
title: "Maverick fails to suspend to ram"
date: 2010-12-08
forum: General Help
---

### Post by MountainX on 2010-12-08
Maverick (64 bit) *will* suspend to RAM on my desktop computer immediately after I boot it up (before I start working). But after I have some programs open, **it always fails to suspend**. 

I get the typical blinking cursor in the upper right corner of a black screen. Then, after 20 seconds, the screen comes back on. The logs contain a message that "Freezing of tasks failed after 20.01 seconds."

The problem task is usually listed as gnome-panel. Sometimes other tasks are listed too (such as Nautilus).

Why will gnome-panel allow me to suspend soon after booting up, but not allow suspend after I start working with applications? I am not changing anything in the panel. And deleting the applets I have installed (system monitor and hardware monitor) doesn't make any difference - the problem continues. As I said, sometimes Nautilus is listed as the task that refuses to freeze.

If I switch users, I can suspend. I assume switching users just puts me in the "clean" state I have with my own user after booting up, so this doesn't really tell me anything new.

I have searched all the other threads I can find. Most of the extensive suspend debugging threads are either from the 2007 era or they deal with laptops or resume issues. My issue is failure to suspend on a desktop.

As you can see from the logs, I've been working on this for a month already!

Here's a typical error message:
Nov  7 01:52:59 MyComputer kernel: [ 1625.221296] Freezing of tasks failed after 20.01 seconds (1 tasks refusing to freeze):
Nov  7 01:52:59 MyComputer kernel: [ 1625.221374] gnome-panel   D 000000010001fdc2     0  1925   1853 0x00800004

Here's an example log showing 2 tasks that fail to freeze:
```
Nov  9 01:25:09 MyComputer kernel: [16615.765114] PM: Syncing filesystems ... done.
Nov  9 01:25:09 MyComputer rtkit-daemon[1738]: The canary thread is apparently starving. Taking action.
Nov  9 01:25:09 MyComputer kernel: [16615.767512] PM: Preparing system for mem sleep
Nov  9 01:25:09 MyComputer kernel: [16615.767518] Freezing user space processes ... 
Nov  9 01:25:09 MyComputer kernel: [16635.769822] Freezing of tasks failed after 20.01 seconds (2 tasks refusing to freeze):
Nov  9 01:25:09 MyComputer kernel: [16635.769898] nautilus      D 0000000000000082     0  1938   1871 0x00800004
Nov  9 01:25:09 MyComputer kernel: [16635.769905]  ffff88040a225a08 0000000000000086 ffff88040a2259d8 0000000000015980
Nov  9 01:25:09 MyComputer kernel: [16635.769907]  ffff88040a225fd8 0000000000015980 ffff88040a225fd8 ffff8803f355c4a0
Nov  9 01:25:09 MyComputer kernel: [16635.769910]  0000000000015980 0000000000015980 ffff88040a225fd8 0000000000015980
Nov  9 01:25:09 MyComputer kernel: [16635.769912] Call Trace:
Nov  9 01:25:09 MyComputer kernel: [16635.769924]  [<ffffffffa0ea2be0>] ? rpc_wait_bit_killable+0x0/0x40 [sunrpc]
Nov  9 01:25:09 MyComputer kernel: [16635.769930]  [<ffffffffa0ea2c04>] rpc_wait_bit_killable+0x24/0x40 [sunrpc]
Nov  9 01:25:09 MyComputer kernel: [16635.769933]  [<ffffffff815878ff>] __wait_on_bit+0x5f/0x90
Nov  9 01:25:09 MyComputer kernel: [16635.769938]  [<ffffffffa0ea2be0>] ? rpc_wait_bit_killable+0x0/0x40 [sunrpc]
Nov  9 01:25:09 MyComputer kernel: [16635.769941]  [<ffffffff815879a8>] out_of_line_wait_on_bit+0x78/0x90
Nov  9 01:25:09 MyComputer kernel: [16635.769943]  [<ffffffff8107f650>] ? wake_bit_function+0x0/0x40
Nov  9 01:25:09 MyComputer kernel: [16635.769949]  [<ffffffffa0ea34ed>] __rpc_execute+0xed/0x290 [sunrpc]
Nov  9 01:25:09 MyComputer kernel: [16635.769955]  [<ffffffffa0ea3713>] rpc_execute+0x83/0xa0 [sunrpc]
Nov  9 01:25:09 MyComputer kernel: [16635.769959]  [<ffffffffa0e9bc99>] rpc_run_task+0x29/0x40 [sunrpc]
Nov  9 01:25:09 MyComputer kernel: [16635.769963]  [<ffffffffa0e9bdb2>] rpc_call_sync+0x42/0x70 [sunrpc]
Nov  9 01:25:09 MyComputer kernel: [16635.769972]  [<ffffffffa1053555>] T.1029+0x35/0x80 [nfs]
Nov  9 01:25:09 MyComputer kernel: [16635.769975]  [<ffffffff81107794>] ? get_page_from_freelist+0x2a4/0x6c0
Nov  9 01:25:09 MyComputer kernel: [16635.769981]  [<ffffffffa10538ef>] nfs3_proc_access+0xbf/0x180 [nfs]
Nov  9 01:25:09 MyComputer kernel: [16635.769987]  [<ffffffffa103d737>] nfs_do_access+0x97/0xf0 [nfs]
Nov  9 01:25:09 MyComputer kernel: [16635.769993]  [<ffffffffa0ea5855>] ? generic_lookup_cred+0x15/0x20 [sunrpc]
Nov  9 01:25:09 MyComputer kernel: [16635.769999]  [<ffffffffa0ea49a0>] ? rpcauth_lookupcred+0x70/0xc0 [sunrpc]
Nov  9 01:25:09 MyComputer kernel: [16635.770002]  [<ffffffff8116687f>] ? dput+0xdf/0x1b0
Nov  9 01:25:09 MyComputer kernel: [16635.770006]  [<ffffffffa103d825>] nfs_permission+0x95/0x1d0 [nfs]
Nov  9 01:25:09 MyComputer kernel: [16635.770009]  [<ffffffff8115c810>] exec_permission+0x30/0x90
Nov  9 01:25:09 MyComputer kernel: [16635.770011]  [<ffffffff8115f569>] link_path_walk+0x89/0xab0
Nov  9 01:25:09 MyComputer kernel: [16635.770013]  [<ffffffff811600f7>] path_walk+0x67/0xe0
Nov  9 01:25:09 MyComputer kernel: [16635.770015]  [<ffffffff811602cb>] do_path_lookup+0x5b/0xa0
Nov  9 01:25:09 MyComputer kernel: [16635.770016]  [<ffffffff81160f97>] user_path_at+0x57/0xa0
Nov  9 01:25:09 MyComputer kernel: [16635.770020]  [<ffffffff8128a05d>] ? aa_dup_task_context+0x3d/0x70
Nov  9 01:25:09 MyComputer kernel: [16635.770022]  [<ffffffff8128fb80>] ? apparmor_cred_prepare+0x40/0x60
Nov  9 01:25:09 MyComputer kernel: [16635.770025]  [<ffffffff8125f906>] ? security_prepare_creds+0x16/0x20
Nov  9 01:25:09 MyComputer kernel: [16635.770028]  [<ffffffff81151970>] sys_faccessat+0xd0/0x1d0
Nov  9 01:25:09 MyComputer kernel: [16635.770030]  [<ffffffff81151a88>] sys_access+0x18/0x20
Nov  9 01:25:09 MyComputer kernel: [16635.770033]  [<ffffffff8100a0f2>] system_call_fastpath+0x16/0x1b
Nov  9 01:25:09 MyComputer kernel: [16635.770035] gnome-panel   D 0000000000000082     0  1943   1871 0x00800004
Nov  9 01:25:09 MyComputer kernel: [16635.770037]  ffff88040a12f998 0000000000000086 ffff88040a12f938 0000000000015980
Nov  9 01:25:09 MyComputer kernel: [16635.770039]  ffff88040a12ffd8 0000000000015980 ffff88040a12ffd8 ffff88040ccd5b80
Nov  9 01:25:09 MyComputer kernel: [16635.770041]  0000000000015980 0000000000015980 ffff88040a12ffd8 0000000000015980
Nov  9 01:25:09 MyComputer kernel: [16635.770044] Call Trace:
Nov  9 01:25:09 MyComputer kernel: [16635.770050]  [<ffffffffa0ea2be0>] ? rpc_wait_bit_killable+0x0/0x40 [sunrpc]
Nov  9 01:25:09 MyComputer kernel: [16635.770055]  [<ffffffffa0ea2c04>] rpc_wait_bit_killable+0x24/0x40 [sunrpc]
Nov  9 01:25:09 MyComputer kernel: [16635.770057]  [<ffffffff815878ff>] __wait_on_bit+0x5f/0x90
Nov  9 01:25:09 MyComputer kernel: [16635.770062]  [<ffffffffa0ea2be0>] ? rpc_wait_bit_killable+0x0/0x40 [sunrpc]
Nov  9 01:25:09 MyComputer kernel: [16635.770064]  [<ffffffff815879a8>] out_of_line_wait_on_bit+0x78/0x90
Nov  9 01:25:09 MyComputer kernel: [16635.770066]  [<ffffffff8107f650>] ? wake_bit_function+0x0/0x40
Nov  9 01:25:09 MyComputer kernel: [16635.770072]  [<ffffffffa0ea34ed>] __rpc_execute+0xed/0x290 [sunrpc]
Nov  9 01:25:09 MyComputer kernel: [16635.770078]  [<ffffffffa0ea3713>] rpc_execute+0x83/0xa0 [sunrpc]
Nov  9 01:25:09 MyComputer kernel: [16635.770082]  [<ffffffffa0e9bc99>] rpc_run_task+0x29/0x40 [sunrpc]
Nov  9 01:25:09 MyComputer kernel: [16635.770086]  [<ffffffffa0e9bdb2>] rpc_call_sync+0x42/0x70 [sunrpc]
Nov  9 01:25:09 MyComputer kernel: [16635.770093]  [<ffffffffa1053555>] T.1029+0x35/0x80 [nfs]
Nov  9 01:25:09 MyComputer kernel: [16635.770099]  [<ffffffffa10538ef>] nfs3_proc_access+0xbf/0x180 [nfs]
Nov  9 01:25:09 MyComputer kernel: [16635.770104]  [<ffffffffa103d737>] nfs_do_access+0x97/0xf0 [nfs]
Nov  9 01:25:09 MyComputer kernel: [16635.770110]  [<ffffffffa0ea5855>] ? generic_lookup_cred+0x15/0x20 [sunrpc]
Nov  9 01:25:09 MyComputer kernel: [16635.770116]  [<ffffffffa0ea49a0>] ? rpcauth_lookupcred+0x70/0xc0 [sunrpc]
Nov  9 01:25:09 MyComputer kernel: [16635.770118]  [<ffffffff8116687f>] ? dput+0xdf/0x1b0
Nov  9 01:25:09 MyComputer kernel: [16635.770123]  [<ffffffffa103d825>] nfs_permission+0x95/0x1d0 [nfs]
Nov  9 01:25:09 MyComputer kernel: [16635.770125]  [<ffffffff8115c810>] exec_permission+0x30/0x90
Nov  9 01:25:09 MyComputer kernel: [16635.770127]  [<ffffffff8115f569>] link_path_walk+0x89/0xab0
Nov  9 01:25:09 MyComputer kernel: [16635.770129]  [<ffffffff811600f7>] path_walk+0x67/0xe0
Nov  9 01:25:09 MyComputer kernel: [16635.770130]  [<ffffffff811602cb>] do_path_lookup+0x5b/0xa0
Nov  9 01:25:09 MyComputer kernel: [16635.770132]  [<ffffffff81160f97>] user_path_at+0x57/0xa0
Nov  9 01:25:09 MyComputer kernel: [16635.770134]  [<ffffffff81164990>] ? pollwake+0x0/0x60
Nov  9 01:25:09 MyComputer kernel: [16635.770136]  [<ffffffff8128fe70>] ? apparmor_inode_getattr+0x60/0x70
Nov  9 01:25:09 MyComputer kernel: [16635.770138]  [<ffffffff81156fa8>] ? cp_new_stat+0xf8/0x110
Nov  9 01:25:09 MyComputer kernel: [16635.770140]  [<ffffffff8115707c>] vfs_fstatat+0x3c/0x80
Nov  9 01:25:09 MyComputer kernel: [16635.770142]  [<ffffffff8115712e>] vfs_lstat+0x1e/0x20
Nov  9 01:25:09 MyComputer kernel: [16635.770143]  [<ffffffff81157154>] sys_newlstat+0x24/0x50
Nov  9 01:25:09 MyComputer kernel: [16635.770146]  [<ffffffff8100a0f2>] system_call_fastpath+0x16/0x1b
Nov  9 01:25:09 MyComputer kernel: [16635.770157] 
Nov  9 01:25:09 MyComputer rtkit-daemon[1738]: Demoting known real-time threads.
Nov  9 01:25:09 MyComputer rtkit-daemon[1738]: Successfully demoted thread 2054 of process 1940 (n/a).
Nov  9 01:25:09 MyComputer rtkit-daemon[1738]: Successfully demoted thread 2035 of process 1940 (n/a).
Nov  9 01:25:09 MyComputer rtkit-daemon[1738]: Successfully demoted thread 1940 of process 1940 (n/a).
Nov  9 01:25:09 MyComputer rtkit-daemon[1738]: Demoted 3 threads.
Nov  9 01:25:09 MyComputer kernel: [16635.770158] Restarting tasks ... done.

```

---

### Post by dcstar on 2010-12-08
> **MountainX said:**
> Maverick (64 bit) *will* suspend to RAM on my desktop computer immediately after I boot it up (before I start working). But after I have some programs open, **it always fails to suspend**. 
..........

Do you still have sufficient swap configured? (yes, even though it is to RAM this seems to be required).

---

### Post by MountainX on 2010-12-08
> **dcstar said:**
> Do you still have sufficient swap configured? (yes, even though it is to RAM this seems to be required).

Thank you. For reference for others, here is some documentation backing up what you stated:
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

It sounds like this could be my problem. I do have more RAM than swap. For some reason, this is what the default Ubuntu installer suggests!

I am using and SSD so I do not want to change my partitions (because of alignment issues). The link I listed above mentions using a swap file instead of a partition. Will this work? Are there better instructions for doing that?

---

### Post by MountainX on 2010-12-09
> **dcstar said:**
> Do you still have sufficient swap configured? (yes, even though it is to RAM this seems to be required).

I added a swap file equal to my RAM size. It did **not** solve the issue.

---

### Post by MountainX on 2010-12-10
```
Dec 10 00:45:41 MyComputer kernel: [ 9772.248587] Freezing user space processes ... 
Dec 10 00:45:41 MyComputer kernel: [ 9792.234911] gnome-panel   D 00000001000e7646     0  1936   1865 0x00800004
Dec 10 00:45:41 MyComputer kernel: [ 9792.234914]  ffff8803ffd47998 0000000000000082 ffff880300000000 0000000000015980
Dec 10 00:45:41 MyComputer kernel: [ 9792.234916]  ffff8803ffd47fd8 0000000000015980 ffff8803ffd47fd8 ffff88040ac42dc0
Dec 10 00:45:41 MyComputer kernel: [ 9792.234918]  0000000000015980 0000000000015980 ffff8803ffd47fd8 0000000000015980
Dec 10 00:45:41 MyComputer kernel: [ 9792.234921] Call Trace:
Dec 10 00:45:41 MyComputer kernel: [ 9792.234933]  [<ffffffffa0f6dbe0>] ? rpc_wait_bit_killable+0x0/0x40 [sunrpc]
Dec 10 00:45:41 MyComputer kernel: [ 9792.234939]  [<ffffffffa0f6dc04>] rpc_wait_bit_killable+0x24/0x40 [sunrpc]
Dec 10 00:45:41 MyComputer kernel: [ 9792.234942]  [<ffffffff8158813f>] __wait_on_bit+0x5f/0x90
Dec 10 00:45:41 MyComputer kernel: [ 9792.234948]  [<ffffffffa0f6dbe0>] ? rpc_wait_bit_killable+0x0/0x40 [sunrpc]
Dec 10 00:45:41 MyComputer kernel: [ 9792.234950]  [<ffffffff815881e8>] out_of_line_wait_on_bit+0x78/0x90
Dec 10 00:45:41 MyComputer kernel: [ 9792.234953]  [<ffffffff8107f660>] ? wake_bit_function+0x0/0x40
Dec 10 00:45:41 MyComputer kernel: [ 9792.234959]  [<ffffffffa0f6e4ed>] __rpc_execute+0xed/0x290 [sunrpc]
Dec 10 00:45:41 MyComputer kernel: [ 9792.234965]  [<ffffffffa0f6e713>] rpc_execute+0x83/0xa0 [sunrpc]
Dec 10 00:45:41 MyComputer kernel: [ 9792.234970]  [<ffffffffa0f66c99>] rpc_run_task+0x29/0x40 [sunrpc]
Dec 10 00:45:41 MyComputer kernel: [ 9792.234975]  [<ffffffffa0f66db2>] rpc_call_sync+0x42/0x70 [sunrpc]
Dec 10 00:45:41 MyComputer kernel: [ 9792.234984]  [<ffffffffa10db645>] T.1034+0x35/0x80 [nfs]
Dec 10 00:45:41 MyComputer kernel: [ 9792.234991]  [<ffffffffa10db9df>] nfs3_proc_access+0xbf/0x180 [nfs]
Dec 10 00:45:41 MyComputer kernel: [ 9792.234996]  [<ffffffffa10c57b7>] nfs_do_access+0x97/0xf0 [nfs]
Dec 10 00:45:41 MyComputer kernel: [ 9792.235003]  [<ffffffffa0f70855>] ? generic_lookup_cred+0x15/0x20 [sunrpc]
Dec 10 00:45:41 MyComputer kernel: [ 9792.235009]  [<ffffffffa0f6f9a0>] ? rpcauth_lookupcred+0x70/0xc0 [sunrpc]
Dec 10 00:45:41 MyComputer kernel: [ 9792.235012]  [<ffffffff81166c2f>] ? dput+0xdf/0x1b0
Dec 10 00:45:41 MyComputer kernel: [ 9792.235017]  [<ffffffffa10c58a5>] nfs_permission+0x95/0x1d0 [nfs]
Dec 10 00:45:41 MyComputer kernel: [ 9792.235020]  [<ffffffff8115cbc0>] exec_permission+0x30/0x90
Dec 10 00:45:41 MyComputer kernel: [ 9792.235022]  [<ffffffff8115f919>] link_path_walk+0x89/0xab0
Dec 10 00:45:41 MyComputer kernel: [ 9792.235023]  [<ffffffff811604a7>] path_walk+0x67/0xe0
Dec 10 00:45:41 MyComputer kernel: [ 9792.235025]  [<ffffffff8116067b>] do_path_lookup+0x5b/0xa0
Dec 10 00:45:41 MyComputer kernel: [ 9792.235027]  [<ffffffff81161347>] user_path_at+0x57/0xa0
Dec 10 00:45:41 MyComputer kernel: [ 9792.235029]  [<ffffffff811200d9>] ? do_wp_page+0x369/0x900
Dec 10 00:45:41 MyComputer kernel: [ 9792.235031]  [<ffffffff815899fe>] ? _raw_spin_lock+0xe/0x20
Dec 10 00:45:41 MyComputer kernel: [ 9792.235034]  [<ffffffff812b7a0d>] ? _atomic_dec_and_lock+0x4d/0x80
Dec 10 00:45:41 MyComputer kernel: [ 9792.235036]  [<ffffffff81157358>] ? cp_new_stat+0xf8/0x110
Dec 10 00:45:41 MyComputer kernel: [ 9792.235038]  [<ffffffff8115742c>] vfs_fstatat+0x3c/0x80
Dec 10 00:45:41 MyComputer kernel: [ 9792.235040]  [<ffffffff811574de>] vfs_lstat+0x1e/0x20
Dec 10 00:45:41 MyComputer kernel: [ 9792.235042]  [<ffffffff81157504>] sys_newlstat+0x24/0x50
Dec 10 00:45:41 MyComputer kernel: [ 9792.235044]  [<ffffffff8100a0f2>] system_call_fastpath+0x16/0x1b
```

---

### Post by MountainX on 2011-01-06
I still have not found a solution. But I have more info. 

When I try to suspend after using my computer for some time, it will always fail. However, if I log out and log back in and then immediately suspend it will always succeed.

Any ideas?

---

### Post by MountainX on 2011-01-07
I have a hypothesis that the failure to suspend is related to my mounted NFS shares. Does anyone have suspend/resume working with mounted NFS shares? If so, is there a trick to it?

---

### Post by MountainX on 2011-01-07
I found two bug reports that seem related:

[https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/506116](https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/506116)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/292698](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/292698)

These are also related:

[https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/30594](https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/30594)

[http://ubuntuforums.org/showthread.php?t=1225117](http://ubuntuforums.org/showthread.php?t=1225117)

**Unfortunately, I have not found a solution.** I'm still looking for help on this. Thanks.

---

### Post by cmoraes on 2011-01-07
Just a few thoughts - 
Maybe you could try a swap file slightly bigger than your RAM, say 10-15% bigger. 
The network share may be the issue, if the suspend process first disconnects the n/w and then tries to write something to your home directory.

---

### Post by MountainX on 2011-01-07
> **cmoraes said:**
> Just a few thoughts - 
Maybe you could try a swap file slightly bigger than your RAM, say 10-15% bigger. 
The network share may be the issue, if the suspend process first disconnects the n/w and then tries to write something to your home directory.

Thank you for your thoughts. I believe I have ruled out the swap file as the cause. It sure seems like I have narrowed it down via troubleshooting to something related to NFS shares...

I just need to figure out what to try next.

---

### Post by MountainX on 2011-01-09
In continuing my troubleshooting I came across an instance where the cause of the failure to suspend appears different from my usual case. Here's the log:

```
Jan  9 11:35:32 mycomputer kernel: [47932.007687] Freezing user space processes ... (elapsed 0.01 seconds) done.
Jan  9 11:35:32 mycomputer kernel: [47932.026903] Freezing remaining freezable tasks ... (elapsed 0.02 seconds) done.
Jan  9 11:35:32 mycomputer kernel: [47932.046926] PM: Entering mem sleep
Jan  9 11:35:32 mycomputer kernel: [47932.046943] Suspending console(s) (use no_console_suspend to debug)
Jan  9 11:35:32 mycomputer kernel: [47932.047301] ACPI handle has no context!
...
Jan  9 11:35:32 mycomputer kernel: [47932.586174] PM: suspend of devices complete after 539.421 msecs
Jan  9 11:35:32 mycomputer kernel: [47932.586179] PM: suspend devices took 0.540 seconds
Jan  9 11:35:32 mycomputer kernel: [47932.586402] r8169 0000:03:00.0: PME# enabled
Jan  9 11:35:32 mycomputer kernel: [47932.586410] pcieport 0000:00:1c.1: wake-up capability enabled by ACPI
Jan  9 11:35:32 mycomputer kernel: [47932.646056] PM: late suspend of devices complete after 59.915 msecs
Jan  9 11:35:32 mycomputer kernel: [47932.646311] ACPI: Preparing to enter system sleep state S3
Jan  9 11:35:32 mycomputer kernel: [47932.646807] PM: Saving platform NVS memory
Jan  9 11:35:32 mycomputer kernel: [47932.646879] Disabling non-boot CPUs ...
Jan  9 11:35:32 mycomputer kernel: [47932.656810] Broke affinity for irq 19
Jan  9 11:35:32 mycomputer kernel: [47932.656818] Broke affinity for irq 21
Jan  9 11:35:32 mycomputer kernel: [47932.657851] CPU 1 is now offline
Jan  9 11:35:32 mycomputer kernel: [47932.666058] Broke affinity for irq 16
Jan  9 11:35:32 mycomputer kernel: [47932.666092] Broke affinity for irq 23
Jan  9 11:35:32 mycomputer kernel: [47932.775810] CPU 2 is now offline
Jan  9 11:35:32 mycomputer kernel: [47932.825909] Broke affinity for irq 17
Jan  9 11:35:32 mycomputer kernel: [47932.825917] Broke affinity for irq 18
Jan  9 11:35:32 mycomputer kernel: [47932.935586] CPU 3 is now offline
Jan  9 11:35:32 mycomputer kernel: [47932.935590] SMP alternatives: switching to UP code
Jan  9 11:35:32 mycomputer kernel: [47932.941512] Back to C!
Jan  9 11:35:32 mycomputer kernel: [47932.941514] PM: Restoring platform NVS memory
Jan  9 11:35:32 mycomputer kernel: [47932.941817] Enabling non-boot CPUs ...
Jan  9 11:35:32 mycomputer kernel: [47932.941934] SMP alternatives: switching to SMP code
Jan  9 11:35:32 mycomputer kernel: [47932.946481] Booting Node 0 Processor 1 APIC 0x2
Jan  9 11:35:32 mycomputer kernel: [47933.186537] CPU1 is up
Jan  9 11:35:32 mycomputer kernel: [47933.187490] Booting Node 0 Processor 2 APIC 0x4
Jan  9 11:35:32 mycomputer kernel: [47933.406441] CPU2 is up
Jan  9 11:35:32 mycomputer kernel: [47933.408273] Booting Node 0 Processor 3 APIC 0x6
Jan  9 11:35:32 mycomputer kernel: [47933.656385] CPU3 is up
Jan  9 11:35:32 mycomputer kernel: [47933.657663] ACPI: Waking up from system sleep state S3
```

Almost every time it fails to suspend, the failure is in "Freezing user space processes". The above log shows that in this case it proceeded past that point. I don't believe this new case is my main problem, but I think this shows that I probably need some expert help. 

I'd be willing to pay for assistance. Where can I find help on this?

---

### Post by MountainX on 2011-01-09
Actually, I'm starting to wonder if this will even work at all, regardless of the amount of troubleshooting done.

My goal was for suspend/resume to work as well as it does on my iMac. My iMac has the same NFS shares to the same file server. On the iMac I can just put it to sleep any time, even with the Finder open or even with files on the NFS shares open.

Ubuntu won't do that. And I'm beginning to think it won't do that no matter what.

Personally, this is the first thing I have found that I like better about OS X than Ubuntu.

---

### Post by MountainX on 2011-03-26
The following script will solve my suspend problem:

```

sync
sleep 2
sudo umount -a -t NFS -f
sudo pm-suspend
sudo mount -a -t NFS

```

Unfortunately, I'm told that it could lead to loss of data or file system corruption, etc.

But it does point out exactly where the problem is: NFS mounts.

This is NOT related to open files on those mounts. I can close every application and the PC will still not suspend until I run that script.

---

### Post by linuxuser12345 on 2011-03-26
Go through your BIOS and change your suspend mode. This should fix the problem: I have had a similar problem before

---

### Post by MountainX on 2011-03-26
> **linuxuser12345 said:**
> Go through your BIOS and change your suspend mode. This should fix the problem: I have had a similar problem before

I'm pretty sure that's not the issue...

---

### Post by linuxuser12345 on 2011-03-26
You can try it. I thought my computer was screwed up before, too, because it wouldn't suspend correctly. It turns out all I needed to do was go into the BIOS and make a simple change

---

### Post by MountainX on 2011-04-04
I purchased Canonical's Ubuntu Advantage support and opened a ticket on this issue.

---

### Post by Rebelli0us on 2011-04-05
Is it a new machine with USB3? On 3 new PCs suspend failed until I disabled USB3 in BIOS.  USB3 problem is listed in Ubuntu version bug reports.

---

### Post by MountainX on 2011-04-05
> **Rebelli0us said:**
> Is it a new machine with USB3? On 3 new PCs suspend failed until I disabled USB3 in BIOS.  USB3 problem is listed in Ubuntu version bug reports.

Now that's interesting. Yes, it has USB 3.0. My motherboard is a GIGABYTE GA-P55-USB3 LGA 1156 Intel P55 USB 3.0 ATX Intel Motherboard.

However, doesn't my post here:
[http://ubuntuforums.org/showpost.php?p=10603567&postcount=13](http://ubuntuforums.org/showpost.php?p=10603567&postcount=13)
prove that this is related to NFS?

My PC will always suspend and wake up perfectly when I'm not connected to any NFS shares. That would seem to rule out USB 3 don't you think?

---

### Post by airtonix on 2011-04-25
My motherboard does not have usb3 but exhibits the same problems as MountainX.

If I simply run : 

```
sudo s2ram -f
```Then it immediatly suspends without all the QQ.

I should also mention that my HP Mini311 Netbook(running maverick) will suspend and hibernate via the panel menus regardless of the situation...

both use the same kernel : 
```
2.6.35-28-generic-pae
```

---

### Post by MountainX on 2011-04-25
It looks like I lucked into a solution finally after five months! All it took was a new release of Ubuntu! (And a suggestion from a Canonical support engineer.)

I installed the **Natty kernel **(2.6.38-4) and the Natty linux-firmware package on my existing Maverick installation and now my computer suspends and resumes perfectly, even with NFS shares open. I'm going to stick with this solution. I don't plan to upgrade to Natty (seems too buggy), but I will use the Natty kernel backports when they are available.

Here are my exact steps:

```

uname -a
Linux desktop 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 18:42:20 UTC 2011 x86_64 GNU/Linux

Browse this website http://kernel.ubuntu.com/ 
I want v2.6.38.4-natty (there are some for 2.6.39 too)

wget  http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38.4-natty/linux-headers-2.6.38-02063804_2.6.38-02063804.201104221009_all.deb

wget  http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38.4-natty/linux-headers-2.6.38-02063804-generic_2.6.38-02063804.201104221009_amd64.deb

wget  http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38.4-natty/linux-image-2.6.38-02063804-generic_2.6.38-02063804.201104221009_amd64.deb

Make absolutely sure that you install them in this order : 

sudo dpkg -i linux-headers-2.6.38-02063804_2.6.38-02063804.201104221009_all.deb

sudo dpkg -i linux-headers-2.6.38-02063804-generic_2.6.38-02063804.201104221009_amd64.deb

sudo dpkg -i linux-image-2.6.38-02063804-generic_2.6.38-02063804.201104221009_amd64.deb

```OOOPS - errors!!!
Actually, they are warnings, but they are imporant and I needed to fix them:
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168d-2.fw for module r8169
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168d-1.fw for module r8169

Here's how to fix firmware for 8169 using linux-firmware package from natty:
```

wget https://launchpad.net/ubuntu/+archive/primary/+files/linux-firmware_1.49_all.deb
sudo dpkg -i linux-firmware_1.49_all.deb 
sudo update-initramfs -u

sudo update-grub

reboot

uname -a
Linux desktop 2.6.38-02063804-generic #201104221009 SMP Fri Apr 22 10:11:24 UTC 2011 x86_64 GNU/Linux

```Seems to have fixed many of my problems! So far this is a huge improvement :grin:
(I'll do more testing over the next few days...)

---

### Post by airtonix on 2011-04-25
I actually resorted to this dbus method instead : 

```

#!/bin/bash
#Suspend

dbus-send --session --dest=org.gnome.ScreenSaver --type=method_call --print-reply /ScreenSaver org.gnome.ScreenSaver.Lock
dbus-send --system --print-reply --dest="org.freedesktop.Hal" /org/freedesktop/Hal/devices/computer org.freedesktop.Hal.Device.SystemPowerManagement.Suspend int32:0

```

Locks the screen and suspends.

---

### Post by MountainX on 2011-04-26
UPDATE: For anyone reading my [**solution**]("http://ubuntuforums.org/showpost.php?p=10718714&postcount=21") (2 posts above) and on a laptop, be aware of this:
[http://www.phoronix.com/scan.php?page=news_item&px=OTM3NQ](http://www.phoronix.com/scan.php?page=news_item&px=OTM3NQ)
Linux kernel power bug in 2.6-38 (Natty kernel)

I'm on a desktop so I don't care too much about 10 or 15% greater power consumption for a few weeks or however long it is until the bug is resolved. But laptop/notebook users will certainly care. It kinda sucks that the new kernel fixes this suspend/resume bug but adds a significant new bug.

EDIT: hmmm, there is a comment that says, "fix released"... wonder if this is really fixed so quickly!?
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131)

---

### Post by jinbatsu on 2011-11-10
@MountainX, thank you for the solution  linux-firmware package from natty.
I already install latest Kernel backport natty in my Lucid.

With this command in terminal:
```
sudo add-apt-repository ppa:kernel-ppa/ppa
sudo apt-get update
sudo apt-get install linux-image-generic-lts-backport-natty linux-headers-generic-lts-backport-natty
```
And after getting warning firmware, I continue with your command in terminal:
```
wget https://launchpad.net/ubuntu/+archive/primary/+files/linux-firmware_1.49_all.deb
sudo dpkg -i linux-firmware_1.49_all.deb 
sudo update-initramfs -u

sudo update-grub
```

And viola, all done, my Lucid (10.04) is now Kernel 2.6.38-12.
This fixed my error msg during boot:
```
softreset failed device not ready
```

Thank You! :popcorn:

---

