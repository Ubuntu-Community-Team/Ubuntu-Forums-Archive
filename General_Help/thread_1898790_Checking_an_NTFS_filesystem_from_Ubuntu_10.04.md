---
title: "Checking an NTFS filesystem from Ubuntu 10.04"
date: 2011-12-22
forum: General Help
---

### Post by BlackMaxPhoto on 2011-12-22
Is there a way to do a file system check like 'chkdsk /f' on an ntfs external hard drive from Ubuntu 10.04.3 ?

I would need to do this via Ubuntu since there are no WinTel machines here.

---

### Post by davethewave83 on 2011-12-22
> **BlackMaxPhoto said:**
> Is there a way to do a file system check like 'chkdsk /f' on an ntfs external hard drive from Ubuntu 10.04.3 ?

I would need to do this via Ubuntu since there are no WinTel machines here.

I'm not sure if there is a tool in Ubuntu to check NTFS being how NTFS is not native supported by GNU/Linux, it works only by reverse engineered effort, you could try burning Hiren's bootCD and booting from that, I think Volkov Commander would do a chkdsk but I can't say for certain as I've never tried it. There are many other tools that might help you out on Hiren's, for example HDD Scan which may do what you need.

---

### Post by tjoff on 2011-12-22
Once I had what proved to be a corrupted NTFS file system, I spent too much time trying to find NTFS-diagnostics tools for ubuntu: [http://ubuntuforums.org/showthread.php?t=1605384](http://ubuntuforums.org/showthread.php?t=1605384)
I ran all tests from the disk utility, as well as ntfsfix and some others programs I do not remember, and none indicated any problems with the file system.
In the end I ran chkdsk from windows and it found and repaired the issue.
My conclusion was that you need windows for this task, but I would love to be proven wrong.

---

### Post by Mark Phelps on 2011-12-22
> **BlackMaxPhoto said:**
> Is there a way to do a file system check like 'chkdsk /f' on an ntfs external hard drive from Ubuntu 10.04.3 ?

I would need to do this via Ubuntu since there are no WinTel machines here.
There is no CHKDSK equivalent for Linux systems, unfortunately.

There is ntfsfix but it can only repair very simple problems.  It's not an equivalent of CHKDSK.

---

### Post by BlackMaxPhoto on 2011-12-22
... tried ntfsfix earlier, didn't work

... tried Hiren's bootCD, no luck there either.


Thanx for the replies


BC

---

