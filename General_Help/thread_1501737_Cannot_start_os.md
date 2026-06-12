---
title: "Cannot start os"
date: 2010-06-04
forum: General Help
---

### Post by C84H on 2010-06-04
I have MSI wind Laptop computer with the latest version of Ubuntu installed. Currently both Ubuntu and windows are running on the laptop. My problem is that when I turn it on and try to boot it up it hangs in start up.

I installed Ubuntu via a program called "Wubi" on drive "D." I can access this drive from windows but I cannot get to my files from windows. If there is a way to fix the problem or to recover my files, that would be great.


I have tried booting in recovery mode, but with no luck (it will appear to be starting up fine, then I get dropped to an initramfs prompt .) The grub menu will load upon startup, but selecting recovery mode does not seem to help the problem.

The Error Message I get is;

> Buffer I/0 ERROR ON DEVICE SDA3
LOGICAL BLOCK 7796420
....
ATA1: EH COMPLETE
JBD: FAILED TO READ AT OFFSET 27460
...
JBD: RECOVERY FAILED
EXT3-FS: ERROR READING JOURNAL
...
MOUNTING /DEVLOOP0 ON /ROOT FAILED: INVALID ARGUMENT
...
...ROOT/DEV FAILED:NO SUCH FILE OR DIRECTORY
...ROOT/SYS FAILED: NO SUCH FILE OR DIRECTORY
...ROOT/PROC FAILED. NO SUCH FILE OR DIRECTORY

BUSYBOX V.1.13.3...PRESS 'H' FOR HELP

(INITRAMFS)_

Thanks in advance for the help.
~Chase

---

### Post by C84H on 2010-06-05
Anyone have any ideas what is wrong?

---

