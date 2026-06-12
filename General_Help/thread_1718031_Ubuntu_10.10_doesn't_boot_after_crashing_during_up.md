---
title: "Ubuntu 10.10 doesn't boot after crashing during update."
date: 2011-03-30
forum: General Help
---

### Post by Argentina on 2011-03-30
I'm using Ubuntu 10.10. It's the only OS I have on my laptop. I hadn't updated it for over two months, and one day I started the update. I downloaded about 300 MB of updates and then started installing. While it was doing its job applying all the updates it had downloaded I had some 2 or 3 PDF files open, Amarok and a folder. Suddenly the computer crashed; mouse was dead, so was the keyboard. The computer stopped completely; I wasn't able to reboot it even with "sys rq + R + E + I + S + U + B", to give an idea. I had to kill the power to shut the PC down. But then, when I tried to turn it back on, it started booting up and then the following text showed up (shown in-between quotes):

"
Begin: Loading essential drivers ... done.
Begin: Running /scripts/init-premount ... done.
Begin: Mounting root file system ... Begin: Running /scripts/local-top ... done.
Begin: Running /scripts/local-premount ... done.
[      2.663902] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Begin: Running /scripts/local-bottom ... done.
done.
Begin: Running /scripts/init-bottom ... done.
[      2.916522] EXT4-fs error (device sda1): ext4_ext_check_inode: inode #262245: (comm init) bad header/extent: invalid 

magic - magic 0, entries 0, max 0(0), depth 0(0)
[      2.916683] EXT4-fs error (device sda1): ext4_ext_check_inode: inode #262245: (comm init) bad header/extent: invalid 

magic - magic 0, entries 0, max 0(0), depth 0(0)
[      2.916857] Kernel panic - not syncing: Attempted to kill init!
[      2.916887] Pid: 1, comm: init Not tainted 2.6.35-24-generic #42-Ubuntu
[      2.916918] Call Trace:
[      2.916937]   [<ffffffff81587061>] panic+0x90/0x111
[      2.916965]   [<ffffffff8106388d>] forget_original_parent+0x33d/0x350
[      2.916995]   [<ffffffff81062cb4>] ? put_files_struct+0xc4/0xf0
[      2.917023]   [<ffffffff810638bb>] exit_notify+0x1b/0x190
[      2.917050]   [<ffffffff810652f5>] do_exit+0x1c5/0x3f0
[      2.917074]   [<ffffffff81065575>] do_group_exit+0x55/0xd0
[      2.917101]   [<ffffffff81065607>] sys_exit_group+0x17/0x20
[      2.917129]   [<ffffffff8100a0f2>] system_call_fastpath+0x16/0x1b
[      2.917209] panic occurred, switching back to text console
"

I already tried to chroot into Ubuntu with the Ubuntu 10.10 Live CD, but when I mount the home partition and run "sudo chroot /media/Ubuntu", a message shows up that reads: "chroot: failed to run command `/bin/bash': Exec format error"

All I need is the log-on screen back on; a great deal of valuable information in the computer. Please, if there's somebody out there who can help me, I'd really be thankful.

---

### Post by blueridgedog on 2011-03-30
Before doing anything drastic, I would run fsck on the partition.

Boot on the 10.10 LiveCD then open a terminal and run:

```
sudo umount /dev/sda1
sudo fsck /dev/sda1
```

(assuming you have only one disk drive and the first partition is your / partition - change sda1 as needed)  If you have others or want to confirm the command, you can post the output of

```
sudo fdisk -l
```

Since you were able to mount the internal disk while on the LiveCD previously, you should be able to recover your files if a re-install is required.

---

