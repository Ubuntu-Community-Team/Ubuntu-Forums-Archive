---
title: "really dumb question about stderr"
date: 2009-09-14
forum: General Help
---

### Post by linuxgrrl on 2009-09-14
hello,
i am trying to rescue a failing system.  I need to run xfs_check on a filesystem; however, when I run it there is no output. im told that xfs_check reports errors to "stderr", however, /dev/stderr is not a viewable file nor are any of the files it points to. where can  I find the output and errors being reported by xfs_check? 
thanks!

---

### Post by lswb on 2009-09-14
when something is written to "stderr" it just means it is written to the screen or console. (stdout is also written to screen or console but stderr and stdout are not the same) I'm not familiar with xfs_check and I do not see it listed by synaptic. If it is an X or gui program that is run from a menu, you could try running it from a terminal instead.

---

### Post by capscrew on 2009-09-14
> **linuxgrrl said:**
> hello,
i am trying to rescue a failing system.  I need to run xfs_check on a filesystem; however, when I run it there is no output. im told that xfs_check reports errors to "stderr", however, /dev/stderr is not a viewable file nor are any of the files it points to. where can  I find the output and errors being reported by xfs_check? 
thanks!

There is no file associated with stderr.  By definition stderr is a data stream to the terminal.  If you want it in a file you must redirect it there.

See the last line of examples **_[here]("http://linux.byexamples.com/archives/77/redirect-stderr-to-stdout/")_**

You will find more about it **_[here]("http://www.cyberciti.biz/faq/redirecting-stderr-to-stdout/")_**

Edit:  I'm assuming we are referring to the checking the XFS file system as described **_[here]("http://codeidol.com/unix/knoppix/Repair-Linux/57-Repair-Damaged-Filesystems/")_**

---

