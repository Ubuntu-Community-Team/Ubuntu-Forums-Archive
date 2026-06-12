---
title: "&quot;Multiple Page-IO Submissions&quot; for Insanely Great EXT4 Performance"
date: 2011-05-10
forum: General Help
---

### Post by nutznboltz on 2011-05-10
In case you don't scrape the news for every little thing about squeezing out performance improvements from Linux, allow me to focus on one for you:

Coming in Linux 2.6.39 but probably really here under your nose in 2.6.38: mblk_io_submit

[INDENT][Ext4 will now by default use the "Multiple Page-IO Submissions" mblk_io_submit option, which is said to considerably improve performance and scalability. The code behind it was already added to the kernel with version 2.6.37; however, just before this Linux version was finalised, the Ext developers disabled the function by default because it caused data corruption in certain situations; the responsible bug was fixed in the stabilisation phase of 2.6.38.]("http://www.h-online.com/open/features/Kernel-Log-Coming-in-2-6-39-Part-2-Storage-and-file-systems-1232317.html?page=2")[/INDENT]

So is that true? Does 2.6.38 have a deactivated-but-perfectly-usable EXT4 file system performance option by the name of  mblk_io_submit?

On Natty (well really Lucid running a back-port of 2.6.38 but Natty should be even easier) I added it to /etc/fstab like this:
```

/dev/mapper/vg0-lv0 / ext4 mblk_io_submit,relatime,errors=remount-ro 0 1
```
and rebooted.  The system (really a VM) had no issues at all 

```
$ dmesg | grep -i ext4
[    3.363201] EXT4-fs (dm-1): mounted filesystem with ordered data mode. Opts: (null)
[    3.925013] EXT4-fs (dm-1): re-mounted. Opts: mblk_io_submit,errors=remount-ro
```
But is it really faster?

---

### Post by nutznboltz on 2011-05-10
Is it safe to use?

[INDENT]Ted Tzo:
[URL="http://us.generation-nt.com/answer/ext4-multiple-page-io-submission-option-mblk-io-submit-help-202064502.html"]
I'm planning on turning it on by default post 2.6.38, during the
2.6.39-rc1 merge window. That's me being paranoid, since this is so
late in the -rc cycle for 2.6.38.[/URL][/INDENT]

Ted Tzo's statement makes me think it's safe to use though do your own research.

---

