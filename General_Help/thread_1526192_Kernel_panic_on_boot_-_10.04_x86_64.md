---
title: "Kernel panic on boot - 10.04 x86_64"
date: 2010-07-07
forum: General Help
---

### Post by azredwing on 2010-07-07
Hi all,

Out of the blue, Ubuntu Lucid fails to boot for me. Trying to boot to recovery mode yields these error messages:

```

[3.269057] EXT4-fs error (device sda2): ext4_dx_find_entry: bad entry in directory #1966081: directory entry across blocks - offset=8192, inode=41471, rec_len=196616, name_len=0
[3.271367] EXT4-fs error (device sda2): ext4_lookup: deleted inode referenced: 1968543
[3.311762] EXT4-fs error (device sda2): ext4_dx_find_entry: bad entry in directory #1966081: directory entry across blocks - offset=8192, inode=41471, rec_len=196616, name_len=0
init: hash.c:296: Assertion failed in nih_hash_search: hash != NULL
init: Caught abort, core dumped

```

Trying to to fsck on /dev/sda2 yields no results (ran this via Ubuntu LiveUSB) - the drive is errorless.

Reverting to previous kernels also does not help.

Any idea what is going on and how to fix?

---

### Post by RJARRRPCGP on 2010-07-07
You may have bad RAM or loose RAM.

---

### Post by azredwing on 2010-07-07
> **RJARRRPCGP said:**
> You may have bad RAM or loose RAM.

If that were true, shouldn't the computer not be able to even boot to USB?

(FYI, I'm running on a laptop - Thinkpad T61.)

---

### Post by azredwing on 2010-07-08
Running fsck again on the drive fixed the EXT4-fs errors, but it's still kernel panicking. The attached screenshot contains the full error message.

Still no idea what is going on.

I'll try reseating my memory tonight. I don't have extra so I can't tell if it's faulty yet.

---

### Post by azredwing on 2010-07-08
Running memtest86+ returns no errors. So I'm inclined to believe this isn't a memory problem...

---

### Post by jshtylr on 2011-01-28
Sorry to bring this back up, but did you ever find a solution? As I am having very similar problems, with the same symptoms.

---

### Post by yaddoshi on 2011-08-01
I am experiencing an identical issue.  Last thing I did was install World of Warcraft using PlayOnLinux - it hung during the final phase of the install so I powered off, booted back up and got this same error message.
```
init: hash.c:296: Assertion failed in nih_hash_search: hash != NULL
[4.976485] Kernal panic - not syncing: Attempted to kill init!
[4.976510] Pid: 1, comm: init Not tainted 2.6.38-10-generic #46-Ubuntu
[4.976527] Call Trace:
[4.976541] [<ffffffff815c032e>] ? panic+0x91/0x19c
[4.976558] [<ffffffff81069a93>] ? forget_original_parent+0x263/0x270
[4.976576] [<ffffffff81069abb>] ? exit_notify+0x1b/0x180
[4.976592] [<ffffffff8106a483>] ? do_exit+0x1d3/0x410
[4.976609] [<ffffffff8106a878>] ? do_group_exit+0x58/0xd0
[4.976623] [<ffffffff8106a907>] ? sys_exit_group+0x17/0x20
[4.976638] [<ffffffff8100c002>] ? system_call_fastpath+0x16/0x1b
```

OS version: Ubuntu 11.04 x86_64
Hardware:  Acer Aspire Ethos AS8493G - Intel 1.73GHz quad core, Radeon 5850 (ATI proprietary drivers installed from AMD.com), 4GB DDR3 RAM (2x2GB), 60GB OCZ SSD drive

Any input on this would be appreciated.

---

