---
title: "Kernel panic during boot: &quot;run-init: /sbin/init: No such file or directory&quot;"
date: 2009-12-06
forum: General Help
---

### Post by SciatoreItaliano on 2009-12-06
Hello all,
My computer started giving me a kernel panic whenever I boot yesterday. I've looked all over the internet to find a solution. Nothing seems to have done the trick. I would rather not reinstall the entire operating system if possible, since it would require gigabytes of backup and since I recently spent a long time installing many packages (I won't go into the details). If that's what's necessary, though, I'll do it.

I should probably point out that I have a dual-boot machine with Ubuntu 9.10 and Vista. When I try to boot normally, I get as far as the glowing circle of friends logo before the panic happens. When I try the recovery mode, it still panics and I see the following:

```
[    7.495344] [drm] LVDS—8: set mode l280x800 14
1 8.148095] Console: switching to colour frame buffer device 160x50
Begin: Loading essential drivers... ...
Done.
Begin: Running /scripts/init-premount ...
Done.
Begin: Mounting root file system... ...
Begin: Running /scripts/local-top ...
Bone.
Begin: Running /scripts/local-premount ...
[    8.352093] PM: Starting manual resume from disk
Done.
[    8.407323] kjournald starting. Commit Interval 5 seconds
[    8.407370] EXT3—fs: mounted filesysten with writeback data mode.
Begin: Running /scripts/local—bottom ...
Done.
Done.
Begin: Running /scripts./init—bottom ...
Begin: Starting AppArmor profiles ...
chroot cannot execute /etc/apparmor/initramfs: No such file or directory
Failure: AppArmor profiles failed to load
Done.
run—init: /sbin/init: No such file or directory
[    8.670042] Kernel panic — not syncing: Attempted to kill init!
[    8.670077] Pid: 1, comm: run—init Not tainted 2.6.31—15—generic #50—Ubuntu
[    8.670111] Call Trace:
[    8.670766]  [<ffffffff81527089>] panic+0x73/0x12b
[    8.671434]  [<ffffffff81120ca4>] ? __fput+0x194/0x210
[    6.672112]  [<ffffffff8106045b>] find_new_reaper+0x9b/0xa0
[    8.672807]  [<ffffffff8106103d>] forget_original_parent+0x3d/0x290
[    8.673519]  [<ffffffff8106064c>] ? put_files_struct+0xbc/0xe0
[    8.674259]  [<ffffffff810612a6>] exit_notify+0x16/0x1c0
[    8.675003]  [<ffffffff81061a85>] do_exit+0x1c5/0x1c0
[    8.675757]  [<ffffffff81061d12>] sys_exit+0x12/0x20
[    8.676533]  [<ffffffff81012002>] system_call_fastpath+0x16/0x1b
[    8.677334] [drm:intelfb_panic] *ERROR* panic occurred, switching back to text console
```

I tried my only other kernel with the same results. Vista, however, boots fine.

I'm pretty sure it's not a problem with my hard drive (e.g. corrupted partition table/filesystem) because I have no problem mounting and reading it with the LiveCD. I ran memtest86+ with no problems too. I suspect that some file is missing or damaged, or maybe more than one, and the boot log above seems to support that theory. The only problem is that I can't find anything missing. I checked for /etc/apparmor/initramfs and /sbin/init and both were there. Should I be looking for anything else?

As far as what caused this, I hadn't done any updates since my last successful boot so I know that wasn't the source of any problems. I'm almost positive a script to install a program had a bug and did something terribly wrong. I was running it with elevated permissions so it could do its job correctly and I think it deleted some important thing(s). In the middle of the script, it started complaining that it couldn't find stuff. After it finished I looked around in my open nautilus window for anything missing and I couldn't find anything gone. However, if I tried to start any program, it couldn't find it. From there it just got worse. I tried to open a new nautilus window to double check, and, of course, it couldn't find nautilus. Since I didn't find anything missing before, I was hoping a simple reboot would fix the problem. That was when it started panicking.
I guess the moral of the story is don't run something as root unless you're positive what it's doing.

I'm completely out of ideas. If anyone has any suggestions, I'd really appreciate it. I can attach the problem script if anyone would like to have a look. In the meantime, I'll keep searching and post any updates.

---

### Post by SciatoreItaliano on 2009-12-06
I should add that I've tried chrooting to the mounted filesystem in the LiveCD but that fails, saying "chroot: cannot run command `/bin/bash': No such file or directory". I does the same if I try to start in a different shell. It seems it can't find anything in the filesystem, although everything's there according to nautilus. GRUB also has no problem finding its grub.cfg.

---

### Post by SciatoreItaliano on 2009-12-06
It looks like at this point, the problem has become that it doesn't recognize that the files exist, even though everything's there. And it seems to only happen when the partition I have Ubuntu installed on is the root filesystem. In the LiveCD everything works as expected until I chroot to that partition's mount point.

This seems like it should be something that some Ubuntu guru would look at and instantly know the solution to. Any chance that such a guru is reading this right now?

---

### Post by SciatoreItaliano on 2009-12-06
Ah! I found the problem. I found this line in the script:
```
rm -Rf $FOLDER/lib
```
And $FOLDER had not been defined, so it wiped /lib. Not sure how I missed this earlier, but surely it's the problem.

So, I guess, as it turns out, the only solution is to reinstall. Good thing I can still at least access the filesystem to backup my home folder. And while looking for the problem I came across /var/lib/dpkg/status, with a list of installed packages.

---

### Post by jwwadk on 2010-01-22
> **SciatoreItaliano said:**
> Ah! I found the problem. I found this line in the script:
```
rm -Rf $FOLDER/lib
```
And $FOLDER had not been defined, so it wiped /lib. Not sure how I missed this earlier, but surely it's the problem.

So, I guess, as it turns out, the only solution is to reinstall. Good thing I can still at least access the filesystem to backup my home folder. And while looking for the problem I came across /var/lib/dpkg/status, with a list of installed packages.

I've now reinstalled twice and had the same problem both times. Any ideas as to how I fix this on the LiveCD before I install again?

---

### Post by SciatoreItaliano on 2010-01-24
> **jwwadk said:**
> I've now reinstalled twice and had the same problem both times. Any ideas as to how I fix this on the LiveCD before I install again?

What problem exactly? For me it was a one time thing. I ran a script that deleted /lib. I reinstalled Ubuntu, /lib was back, and I never ran the script that caused the problem ever again.

If your problem is that you get this kernel panic, then I'm not sure what to suggest. I had a specific problem, and a reinstall fixed it. If one reinstall doesn't fix it for you, I suspect your problem is a bit more complex than mine. Multiple reinstalls should not fix anything. And making changes on the LiveCD first shouldn't help either, since everything will be reset to the defaults when you reinstall. The only thing I used the LiveCD for was to access my files to back them up.

Can you give more info?

---

