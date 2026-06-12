---
title: "Remote Admin"
date: 2010-11-30
forum: General Help
---

### Post by satimis on 2010-11-30
Remote admin Win7 VM
Hi folks,

locate desktop - Ubuntu 10.10 64bit
IP:123.123.123.123

Win 7 64bit - running on VM of VBox
IP:456.456.456.456

Both on Intranet


What will be an easy way to remote connect Win7 for admin, such as config including transfer of files between Win7 and Ubuntu 10.10 etc.

TIA

B.R.
satimis

---

### Post by eric3_14159 on 2010-12-24
There are a few ways, depending on what you want to do and what direction it should go in.

If you want to use the Windows computer to reach the Linux one, then install Putty, which will give you an SSH shell. To transfer files, WinSCP is likely to be useful.

VNC will work in either direction, allowing you to directly control the desktop of one computer with the other. This is likely to be the only way to do any administration tasks on the Windows computer, as Windows is not as usable from the command line as Linux is.

To transfer files from the Linux computer to the Windows one, you could set up a web server such as Apache on the Linux computer and have the Windows one download from it (possibly telling it to through VNC), or you could use Samba to let the Windows computer mount a directory on the Linux computer. There are other ways, but those are the two that occur to me.

---

